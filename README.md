# CMU Sphinx Build

An attempt to build the CMU Sphinx 5prealpha source for use on a Raspberry Pi 3.

The process I used is was...

Downloaded the sources from:

https://cmusphinx.github.io/wiki/download/

In particular, downloaded the following "sphinxbase-5prealpha" and "pocketsphinx-5prealpha" files from sourceforge:

pocketsphinx-5prealpha-win32.zip from https://sourceforge.net/projects/cmusphinx/files/pocketsphinx/5prealpha/
sphinxbase-5prealpha-win32.zip from https://sourceforge.net/projects/cmusphinx/files/sphinxbase/5prealpha/

Decompressed both zip files into a folder (which I named "5prealpha-win32") and moved both of the solution folders ("pocketsphinx" and "sphinxbase") into the same folder (the decompress method I used put each of the solution folders into folders named the same as the zip file.)

I then opened the .sln files with Visual Studio 2015 Enterprise (which had all installation options [C++, mobile, the whole lot] installed).

I hit rebuild solution with Debug and Win32 selected.

I then copied the following files from the sphinxbase\bin\Debug\Win32 folder into the pocketsphinx\bin\Debug\Win32 folder:

- sphinx_cepview.exe
- sphinx_fe.exe
- sphinx_jsgf2fsg.exe
- sphinx_lm_convert.exe
- sphinx_pitch.exe
- sphinx_seg.exe
- sphinxbase.dll
- sphinxbase.dll
- sphinxbase.lib

I then opened powershell and navigated to the pocketsphinx solution folder and used the following command:

C:\git\5prealpha-win32\pocketsphinx> .\bin\Debug\Win32\pocketsphinx_continuous.exe -inmic yes -hmm .\model\en-us\en-us\ -lm .\model\en-us\en-us.lm.bin -dict .\model\en-us\cmudict-en-us.dict

This SO post indicates how to turn off the verbose logging on the command line:
https://stackoverflow.com/questions/17825820/how-do-i-turn-off-e-info-in-pocketsphinx
