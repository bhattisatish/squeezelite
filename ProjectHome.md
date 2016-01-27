# Headless squeezebox emulator for linux/osx/windows #

Squeezelite is a small headless squeezebox emulator for linux using alsa audio output and other platforms using portaudio.  It is aimed at supporting high quality audio including usb dac based output at multiple sample rates including 44.1/48/88.2/96/176.4/192k/352.8/384kHz.

The current version supports:
  * built in pcm (wav/aiff) decode plus flac, mp3, ogg and aac via libFLAC, libmad/libmpg123, libvorbisfile, libfaad respectively if they are present on your machine.
  * includes support for wma and alac decode via the ffmpeg library if it is built with the -DFFMPEG build option.  (This is not included in binaries by default)
  * upsampling using the libsoxr resampling library if present on the machine.  This allows squeezelite to upsample the output to the highest sample rate supported by the output device.  It is optionally included in the build process.  (Resampling is not included in armv5te, armv6 and mips binaries in the download directory.)  Resampling support is enabled at compile time with the -DRESAMPLE build option.
  * export of audio data to jivelite on linux to support visualizations.  This is enabled with the -DVISEXPORT build option.  (This is not included in the binaries by default.)
  * DSD playback via DOP capable DACs or via conversion to pcm.  This is enabled with the -DDSD build option and requires additional LMS server patches.

Run "./squeezelite -?" for command line options included in the binary:

```

Squeezelite v1.7, Copyright 2012-2015 Adrian Smith. See -t for license terms
Usage: ./squeezelite [options]
  -s <server>[:<port>]  Connect to specified server, otherwise uses autodiscovery to find server
  -o <output device>    Specify output device, default "default", - = output to stdout
  -l                    List output devices
  -a <b>:<p>:<f>:<m>    Specify ALSA params to open output device, b = buffer time in ms or size in bytes, p = period count or size in bytes, f sample format (16|24|24_3|32), m = use mmap (0|1)
  -a <f>                Specify sample format (16|24|32) of output file when using -o - to output samples to stdout (interleaved little endian only)
  -b <stream>:<output>  Specify internal Stream and Output buffer sizes in Kbytes
  -c <codec1>,<codec2>  Restrict codecs to those specified, otherwise load all available codecs; known codecs: flac,pcm,mp3,ogg,aac,wma,alac,dsd (mad,mpg for specific mp3 codec)
  -d <log>=<level>      Set logging level, logs: all|slimproto|stream|decode|output, level: info|debug|sdebug
  -e <codec1>,<codec2>  Explicitly exclude native support of one or more codecs; known codecs: flac,pcm,mp3,ogg,aac,wma,alac,dsd (mad,mpg for specific mp3 codec)
  -f <logfile>          Write debug to logfile
  -m <mac addr>         Set mac address, format: ab:cd:ef:12:34:56
  -M <modelname>        Set the squeezelite player model name sent to the server (default: SqueezeLite)
  -n <name>             Set the player name
  -N <filename>         Store player name in filename to allow server defined name changes to be shared between servers (not supported with -n)
  -p <priority>         Set real time priority of output thread (1-99)
  -P <filename>         Store the process id (PID) in filename
  -r <rates>[:<delay>]  Sample rates supported, allows output to be off when squeezelite is started; rates = <maxrate>|<minrate>-<maxrate>|<rate1>,<rate2>,<rate3>; delay = optional delay switching rates in ms
  -R -u [params]        Resample, params = <recipe>:<flags>:<attenuation>:<precision>:<passband_end>:<stopband_start>:<phase_response>,
                         recipe = (v|h|m|l|q)(L|I|M)(s) [E|X], E = exception - resample only if native rate not supported, X = async - resample to max rate for device, otherwise to max sync rate
                         flags = num in hex,
                         attenuation = attenuation in dB to apply (default is -1db if not explicitly set),
                         precision = number of bits precision (NB. HQ = 20. VHQ = 28),
                         passband_end = number in percent (0dB pt. bandwidth to preserve. nyquist = 100%),
                         stopband_start = number in percent (Aliasing/imaging control. > passband_end),
                         phase_response = 0-100 (0 = minimum / 50 = linear / 100 = maximum)
  -D [delay]            Output device supports DSD over PCM (DoP), delay = optional delay switching between PCM and DoP in ms
  -v                    Visualiser support
  -z                    Daemonize
  -t                    License terms
  -?                    Display this help text

Build options: LINUX ALSA EVENTFD RESAMPLE FFMPEG VISEXPORT DSD

```


---


Build Instructions [BuildInstructions](BuildInstructions.md)


---


Binary Files are now available from the companion project squeezelite-downloads:

  * Linux armv5te - http://squeezelite-downloads.googlecode.com/git/squeezelite-armv5te
  * Linux armv6 - http://squeezelite-downloads.googlecode.com/git/squeezelite-armv6
  * Linux armv6hf - http://squeezelite-downloads.googlecode.com/git/squeezelite-armv6hf
  * Linux intel 32 bit - http://squeezelite-downloads.googlecode.com/git/squeezelite-i386
  * Linux intel 64 bit - http://squeezelite-downloads.googlecode.com/git/squeezelite-x86-64
  * Linux mips ar71xx - http://squeezelite-downloads.googlecode.com/git/squeezelite-mips-ar71xx
  * OSX 32/64 bit - http://squeezelite-downloads.googlecode.com/git/squeezelite-osx
  * OSX 32 bit - http://squeezelite-downloads.googlecode.com/git/squeezelite-osx-i386
  * Windows - http://squeezelite-downloads.googlecode.com/git/squeezelite-win.zip







