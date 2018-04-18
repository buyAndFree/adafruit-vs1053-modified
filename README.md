## Modified Adafruit VS1053 for Music Maker Shield

Adafruit VS1053 Library with added methods for utilising the spectrum analyser plugin.
Uses the spectrum analyser plugin from the VSLI website (http://www.vlsi.fi/en/support/software/vs10xxplugins.html).

In theory it should be compatible with other arduino shields which use the VS1053 chip.

### Added methods

* ```readFrequencies(uint16_t *currentVal, uint16_t *peak)``` reads the results and fills two arrays with the current and peak values of an mp3 that is being played by the shield (values are from 0 to 31 in 3dB steps).
* ```checkRateAndBands(void)``` prints out the sampling rate and the number of frequency bands being read.
* ```setFrequencies(int numOfBands, short *frequency)``` sets the frequencies to be read. 
* ```readBands(void)``` returns the frequency bands.
* ```readSamplingRate(void)``` returns the sampling rate.

### How to setup your project to use the added functionality

1. Download the spectrum analyser plugin from the VSLI website (http://www.vlsi.fi/en/support/software/vs10xxplugins.html)
2. Open "spectrumAnalyzer1053b.plg" in a text editor
3. Copy from #ifndef SKIP_PLUGIN_VARNAME (line 27) to #endif (line 152) to the top of your arduino project sketch
4. Make sure you have included the modified library in your sketch
5. After you initialise the mp3 player shield in your sketch add the following code: varNameOfFilePlayer.applyPatch(plugin, PLUGIN_SIZE);
6. Use methods as required (refer to example code for reference)
