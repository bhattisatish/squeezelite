# Dependencies #

Squeezelite requires header files for the following libraries to be present at build time:
  * libasound2
  * libflac
  * libmad0
  * libvorbis
  * libfaad
  * libmpg123

All above libraries are dynamically loaded and optional at runtime, meaning that these libraries are only required on the build machine.

It also optionally supports the following libraries which may be enabled by defining additional build options:
  * libsoxr
  * libffmpeg

# Build Options #

Optional build options are enabled by passing additional defines to the compiler.  This may be done with the -D option to ggc or via setting OPTS before calling the included makefiles.  For example:

OPTS="-DFFMPEG -DRESAMPLE" make

The following build options are supported
  * PORTAUDIO - build with port audio support (on linux only, it is not optional on other platforms)
  * RESAMPLE - build with libsoxr support for real time upsampling
  * FFMPEG - build with FFMPEG support for wma and alac support.  Note that this requires the binary to be run with FFMPEG library versions which match the header files used for compilation.  This is necessary and the ffmpeg api changes between versions.
  * VISEXPORT - support export of audio data to jivelite for visualization support (linux only)
  * DSD - support of DSD playback via DOP (-D command line option) or conversion to pcm (requires LMS server patches)

# Target Platforms #

Squeezelite can be build with gcc on linux and osx platforms using the included makefiles.

It also builds using MSVC++ on Windows (project file not currently included in git).

# Examples #

To build on linux with support for re sampling if the same tree was previously used to build with different options:

OPTS=-DRESAMPLE make clean

OPTS=-DRESAMPLE make