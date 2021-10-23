### TeX Live 2021/W32TeX build procedure

* Fetch "W32TeX sources" (TeX Live svn Master/source/w32tex-src.tar.xz: r58680) and extract.
* Environment: Windows 10 + Git for Windows + GNU make + Visual Studio 2010 + Visual Studio 2015



#### Building "ktx" directory

* [1] Start "Visual Studio 2010 Command Prompt".

* [2] Adjust PATH: execute the following `msbuild2010-path.bat`.

  ```
  @echo off
  set PATH=C:\WINDOWS\system32;C:\WINDOWS;C:\WINDOWS\System32\Wbem;C:\WINDOWS\System32\WindowsPowerShell\v1.0\
  set PATH=%PATH%;c:\PROGRA~2\Microsoft Visual Studio 10.0\VSTSDB\Deploy
  set PATH=%PATH%;c:\PROGRA~2\Microsoft Visual Studio 10.0\Common7\IDE\
  set PATH=%PATH%;c:\PROGRA~2\Microsoft Visual Studio 10.0\VC\BIN
  set PATH=%PATH%;c:\PROGRA~2\Microsoft Visual Studio 10.0\Common7\Tools
  set PATH=%PATH%;C:\Windows\Microsoft.NET\Framework\v4.0.30319
  set PATH=%PATH%;C:\Windows\Microsoft.NET\Framework\v3.5
  set PATH=%PATH%;c:\PROGRA~2\Microsoft Visual Studio 10.0\VC\VCPackages
  set PATH=%PATH%;C:\PROGRA~1\Git\bin
  set PATH=%PATH%;C:\PROGRA~1\Git\mingw64\bin;C:\PROGRA~1\Git\mingw64\bin
  set PATH=%PATH%;C:\PROGRA~1\Git\usr\local\bin;C:\PROGRA~1\Git\usr\bin;
  set PATH=%PATH%;c:\usr\bin
  ```

* [3] Install missing commands and headers.

  * GNU make (make.exe) => `c:\usr\bin` (or, somewhere accessible by PATH)

  * "inttypes.h" (Visual Studio 2010 lacks it)

    * Obtain msinttypes-r26.zip from https://code.google.com/archive/p/msinttypes/downloads
    * Place in:
      * `w32tex-src\ktx\texk`
      * `w32tex-src\ktx\utils\lacheck`
      * `w32tex-src\ktx\utils\t1utils`

  * "unistd.h" (Visual Studio 2010 lacks it)

    * Create empty unistd.h (TODO: is this safe?)
    * Place in:
      * `w32tex-src\ktx\libs\libpaper`
      * `w32tex-src\ktx\texk\psutils`

  * "stdbool.h" (Visual Studio 2010 lacks it)

    * Create the following stdbool.h

      ```
      typedef int bool;
      #define false 0
      #define true 1
      ```

    * Place in:

      * `w32tex-src\ktx\texk`

* [4] Start building ktx:

  Copy the official texmf.cnf (`C:\texlive\2021\texmf-dist\web2c\texmf.cnf`) into `ktx\texk\web2c`.

  Some sources are missing:

  * Fetch missing "regex" directory from `w32tex-src\ktx\web2c\pdftexdir`, and place it into `ktx\texk\chktex`.

  * [optional] Fetch missing "VFlib2-2.25.6" directory from w32tex-src.tar.xz as of 2014, and place it into `ktx\texk`.

  Starting from the library ...

  ```
  cd w32tex-src
  cd ktx\texk
  cd kpathsea
  make
  cd win32
  make
  cd ..\..\ptexenc
  make
  cd ..\..
  cd libs\zlib
  nmake
  cd ..\libpng
  nmake
  cd ..\freetype
  sh w32build.sh
  cd ..\xpdf
  make
  cd ..\libpaper
  make
  cd ..\gd
  make
  cd ..\..
  cd extra\libjpeg
  nmake
  cd ..\..
  ```

  Copy generated "kpathsealib.dll" into `ktx\texk\web2c` and `ktx\texk\web2c\web2c`.

  ```
  cd libs\freetype15\lib\arch\win32
  make                     % unnecessary for TeX Live: for NTT JTeX dvi2ps
  cd ..\..\..\..\..
  ```

  Copy generated "libttf.lib" into `ktx\libs\freetype15\lib`.

  Main programs ...

  ```
  cd texk\web2c
  make
  cd ctiedir
  make
  cd ..
  cd ptexdir
  make
  cd ..\uptexdir
  make
  cd ..\eptexdir
  make
  cd ..\euptexdir
  make
  cd ..\jtexdir
  make                     % unnecessary for TeX Live: for NTT JTeX
  cd ..\omegafonts
  make
  cd ..\..
  cd dvipdfm-x
  make
  cd ..\dvipng
  make
  cd ..\dviout-util
  make
  cd ..\afm2pl
  make
  cd ..\aftopl
  nmake
  cd ..\autosp
  nmake
  cd ..\chktex
  nmake
  cd ..\cjkutils
  make
  cd ..\detex
  make
  cd ..\dtl
  make
  cd ..\dvi2dvi
  make                     % unnecessary for TeX Live: for NTT JTeX dvi2dvi
  cd ..
  cd VFlib2-2.25.6\src
  make                     % unnecessary for TeX Live: for NTT JTeX dvi2ps
  cd ..\..\dvi2ps
  make                     % unnecessary for TeX Live: for NTT JTeX dvi2ps
  cd ..\dvi2tty
  nmake
  cd ..\dvidvi
  make
  cd ..\dvihp
  make
  cd ..\dviljk
  nmake all
  cd ..\dvipdfm
  make                     % unnecessary for TeX Live: for original dvipdfm as dvipdfmo.exe
  cd ..\dvipos
  make
  cd ..\dvipsk
  make
  cd ..\kptools
  make                     % unnecessary for TeX Live: for W32TeX-specific fmtutil.exe etc, different from TeX Live
  cd ..\latex2rtf
  make                     % unnecessary for TeX Live: latex2rtf.exe
  cd ..\makeindexk
  make
  cd ..\makejvf
  make
  cd ..\mendexk
  nmake
  cd ..\mftrace
  make                     % unnecessary for TeX Live: gf2pbm.exe
  cd ..\musixtnt\musixtnt-src
  nmake
  cd ..\..\ps2otfps
  make                     % unnecessary for TeX Live: ps2otfps.exe
  cd ..\psutils
  make                     %% see comment below
  ```

  In case of build error, remove the following lines from `Makefile`:

  ```
  config.h: config.h.msvc
  	cp config.h.msvc $@
  ```

  ```
  cd ..\runscr
  make                     % unnecessary for TeX Live (TODO: where is runscript.exe/dll?)
  cd ..\seetexk
  make
  cd ..\showlang
  make                     % unnecessary for TeX Live: showlang.exe
  cd ..\tex4htk
  make
  cd ..\texworkswrapper
  make
  cd ..\ttf2pfb
  make                     % unnecessary for TeX Live: ttf2pfb.exe etc
  cd ..\ttf2pk2
  make
  cd ..\ttf2pt1
  make                     % unnecessary for TeX Live: ttf2pt1.exe
  cd ..\ttfdump
  cd libttf
  make
  cd ..\src
  make
  cd ..\..\..
  cd utils
  cd allow5c
  make                     % unnecessary for TeX Live: allow5c.exe based on dvispc.exe (dviout-util)
  cd ..\bkmk2uni
  make                     % unnecessary for TeX Live: bkmk2uni.exe
  cd ..\bmp2png
  make
  cd ..\devnag\src
  make
  cd ..\..\dviinfo
  make                     % unnecessary for TeX Live: dviinfo.exe
  cd ..\epstool
  make                     % unnecessary for TeX Live: epstool.exe
  cd ..\is64bit
  make                     % unnecessary for TeX Live: is64bit.exe
  cd ..\lacheck
  nmake
  cd ..\m-tx
  nmake
  cd ..\out2uni
  make                     % unnecessary for TeX Live: out2uni.exe
  cd ..\pfm2afm
  make                     % unnecessary for TeX Live: pfm2afm.exe and afm2pfm.exe
  cd ..\plain2-2.54p1\src
  make                     % unnecessary for TeX Live: plain2.exe
  cd ..\..\platex-ng
  make                     % unnecessary for TeX Live: platex-ng.exe (wrapper of ptex-ng.exe)
  cd ..\pmx
  make
  cd ..\ps2eps
  make
  cd ..\pst2pdf
  make                     % unnecessary for TeX Live: pst2pdf.exe and pst2eps.exe
  cd ..\ptexindy
  make
  cd ..\rungs
  make
  cd ..\t1utils
  make
  cd ..\texview
  make
  cd ..\txtutil
  nmake
  cd ..\vlna
  make
  ```

  * TODO: `pdfopen`, `jbig2enc-0.23`, `sam2p-2018`, `tif22pnm-0.12`, `tiff2png`, `xindy`.



#### Building "qtx" directory

* [5] Start "Visual Studio 2015 Command Prompt".

* [6] Adjust PATH: execute the following `msbuild2015-path.bat`.

  ```
  @echo off
  set PATH=C:\WINDOWS\system32;C:\WINDOWS;C:\WINDOWS\System32\Wbem;C:\WINDOWS\System32\WindowsPowerShell\v1.0\
  set PATH=%PATH%;C:\PROGRA~2\Microsoft Visual Studio 14.0\Common7\IDE\
  set PATH=%PATH%;C:\PROGRA~2\Microsoft Visual Studio 14.0\VC\BIN
  set PATH=%PATH%;C:\PROGRA~2\Microsoft Visual Studio 14.0\Common7\Tools
  set PATH=%PATH%;C:\WINDOWS\Microsoft.NET\Framework\v4.0.30319
  set PATH=%PATH%;C:\PROGRA~2\Microsoft Visual Studio 14.0\VC\VCPackages
  set PATH=%PATH%;C:\PROGRA~1\Git\bin
  set PATH=%PATH%;C:\PROGRA~1\Git\mingw64\bin;C:\PROGRA~1\Git\mingw64\bin
  set PATH=%PATH%;C:\PROGRA~1\Git\usr\local\bin;C:\PROGRA~1\Git\usr\bin;
  set PATH=%PATH%;c:\usr\bin
  ```

* [7] Install missing commands and headers.

  * GNU make (make.exe) => `c:\usr\bin` (or, somewhere accessible by PATH)

* [8] Start building qtx:

  Copy the official texmf.cnf (`C:\texlive\2021\texmf-dist\web2c\texmf.cnf`) into `qtx\texk\web2c`.

  Starting from the library ...

  ```
  cd qtx\texk\kpathsea
  make
  cd ..\..\libs
  cd zlib
  make
  cd ..\libpng
  make
  cd ..\graphite2-src\src
  make
  cd ..\..\harfbuzz\harfbuzz-src\src
  make
  cd ..\..\..\pplib\src
  make
  cd ..\..\zziplib\zzip
  make
  cd ..\bins
  make
  ```

  Main programs ...

  ```
  cd qtx\texk\web2c
  cd lualibs\lua53
  make
  cd ..\LuaJIT-2.1.0-beta3\src
  msvcbuild32.bat
  ```

  Copy generated "luajit51.lib" into `lualibs\luajit`.

  ```
  cd ..\..\luaffi
  msvcbuildstatic.bat
  cd ..\luafontloader
  make
  cd ..\luafontloader-jit
  make
  cd ..\luamd5
  make
  cd ..\luamd5-jit
  make
  cd ..\luapeg
  make
  cd ..\luapeg-jit
  make
  cd ..\luasocket\src
  make
  cd ..\..\luasocket-jit\src
  make
  cd ..\..\luazip\src
  make
  cd ..\..\luazip-jit\src
  make
  cd ..\..\luazlib
  make
  cd ..\luazlib-jit
  make
  cd ..\slnunicode
  make
  cd ..\slnunicode-jit
  make
  cd ..\..
  cd ..\..
  cd mplibdir
  make
  cd ..\mplibdir-jit
  make
  cd ..\lib
  make
  cd ..\luatexdir
  sh buildall.sh
  cd ..\
  make
  make -f Makefile.hb
  make -f Makefile.jit
  make -f Makefile.jithb
  ```



#### Building "ptx" directory

* [9] Start "Visual Studio 2015 Command Prompt".

* [10] Adjust PATH: execute the following `msbuild2015-path.bat` (same as [6]).

* [11] Install missing commands and headers.

  * GNU make (make.exe) => `c:\usr\bin` (or, somewhere accessible by PATH)

  * "unistd.h" (Visual Studio 2010 lacks it)

    * Create empty unistd.h (TODO: is this safe?)
    * Place in:
      * `w32tex-src\ptx\libs\fontconfig\src`
      * `w32tex-src\ptx\libs\ptx\libs\potrace-exec`

* [12] Start building ptx:

  Copy the official texmf.cnf (`C:\texlive\2021\texmf-dist\web2c\texmf.cnf`) into `ptx\texk\web2c`.

  Starting from the library ...

  ```
  cd w32tex-src\ptx
  cd texk\kpathsea
  make
  cd ..\ptexenc
  make
  cd ..\..
  cd libs\zlib
  make
  cd ..\libpng
  make
  cd ..\freetype
  sh w32build.sh
  cd ..\expat\lib
  make
  cd ..\..\fontconfig\src
  make
  cd ..
  sh mkall.sh
  cd ..\pplib\src
  make
  cd ..\..\graphite2-src\src
  make
  cd ..\..\teckit
  make
  cd ..\icu-src
  cd source
  cd common
  make && make install
  cd ..
  cd i18n
  make && make install
  cd ..
  cd io
  make && make install
  cd ..
  cd stubdata
  make && make install
  cd ..
  cd tools
  cd toolutil
  make && make install
  cd ..
  cd gencfu
  make && make install
  cd ..
  cd gencnval
  make && make install
  cd ..
  cd gennorm2
  make && make install
  cd ..
  cd genrb
  make && make install
  cd ..
  cd gensprep
  make && make install
  cd ..
  cd gentest
  make && make install
  cd ..
  cd icupkg
  make && make install
  cd ..
  cd makeconv
  make && make install
  cd ..
  cd pkgdata
  make && make install
  cd ..
  cd genbrk
  make && make install
  cd ..
  cd gendict
  make && make install
  cd ..\..\data
  ```

  Edit "makedata.mak":

  ```
  ICUMAKE=C:\path\to\w32tex-src\ptx\libs\icu-src\source\data
  CFG=x86\Release
  ```

  (The directory name should be the absolute path.)

  ```
  nmake -f makedata.mak
  cd ..\..\..
  cd harfbuzz\harfbuzz-src\src
  make
  cd ..\..\..\..
  cd libs\libpaper
  touch unistd.h
  make
  cd ..\pixman\pixman-src
  sh buildw32.sh
  cd ..\..\gd
  make
  cd ..\potrace-exe
  make
  cd ..\gmp\gmp-src
  sh mklibw32.sh
  cd ..\..\mpfr\mpfr-src\src
  sh mklibw32.sh
  cd ..\..\..\..
  ```

  Main programs ...

  ```
  cd texk\web2c
  make
  make cweb
  make xetex.dll
  ```

  In case of build error, find the following lines in the Makefile of `ptx\texk\web2c\web2c`:

  ```
  $(kpathsea): $(kpathsea_srcdir)/*.c $(kpathsea_srcdir)/*.h \
  	     $(top_srcdir)/../make/paths.mk
  	cd $(kpathsea_dir) && $(MAKE) $(makeargs)
  ```

  and comment-out the line `$(top_srcdir)/../make/paths.mk`

  ```
  cd web2c
  make
  cd ..
  make xetex.dll
  make synctex.exe
  cd mplibdir
  make
  cd ..\pmpostdir
  make
  make -f Makefile.upm
  cd ..\lualibs\lua53
  make
  ```

  Copy generated "luajit51.lib" (inside `qtx\...` counterpart) into `lualibs\luajit`.

  ```
  cd ..\..
  make
  cd ..\bibtex-x
  make
  cd ..\dvisvgm
  make
  cd ..\upmendex
  make
  cd ..\gregorio
  make
  cd ..\lcdf-typetools
  make
  cd ..\libdpx
  make
  cd ..\pstoedit
  make
  cd ..\xml2pmx
  make
  cd ..\..
  cd utils
  cd axodraw2
  make
  ```

  * TODO: `extractpdfmark` (requires `poppler-new`), `ptex-ng` (requires `cairo` and `mruby` which requires Rake)

----
Hironobu Yamashita (@aminophen)
