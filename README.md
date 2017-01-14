# w32tex-build

This repository contains binary files of win32 TeX distribution.
Current binaries are mostly based on

- w32tex-src.tar.xz (as of 2016-05-13 10:17, r41087)

and some sources are updated along with TeX Live svn

- ktx/texk/kpathsea (r42801)
- ktx/texk/dvipdfm-x (r42803)
- ktx/texk/dvipsk (r42703)
- ktx/texk/makejvf (r42724)
- ktx/texk/mendexk (r42772)
- ktx/texk/tex4htk (r42110)
- ktx/texk/web2c (r42506)
- ktx/texk/web2c/eptexdir (r42711)
- ktx/texk/web2c/euptexdir (r42711)
- ktx/texk/web2c/lib (r42828)
- ktx/texk/web2c/pdftexdir (r42438)
- ktx/texk/web2c/ptexdir (r42720)
- ktx/texk/web2c/uptexdir (r42954)
- xtx/texk/kpathsea (r42801)
- xtx/texk/upmendex (r42784)
- xtx/texk/web2c (r42506)
- xtx/texk/web2c/lib (r42828)
- xtx/texk/web2c/xetexdir (r42194)

Also, some missing sources are retrieved from older archives

- w32tex-src.tar.xz (as of 2014-05-22 00:48, r34185)

and updated along with the upstream

- ktx/utils/bmp2png: bmp2png 1.62
  from http://cetus.sakura.ne.jp/softlab/b2p-home/index.html

Only a small subset of binaries are available, since these are the ones
which I managed to build by myself using Visual Studio 2013. The even
better and stable binaries are also included in W32TeX by Akira Kakuto,
so there is no reason to choose ones in this repository.
No warranty.

----

ꂍA Visual Studio 2013 łǂɂrhɐ󂵂 win32 ̊TeX ֘AoCi𒵂Ă߂̏ꏊłB󂵂uĂ܊񂌂ŁAp搶̠W32TeX ɔ䂗ăt@CĂ܂B
̗󋖚Ił̂ŁA헰Ȃق悢Ǝv܂BRۏ؂łB

µgBĂ݂ꍇ́AW32TeX ⠔eX Live (win32) ̌X̓t@C
㊃l[ĕۊǂĂAキ肉̃|Wg玦t@C꒵ĂBꈈれ־͂čT܂B

Visual Studio 2013 ŃrhĂ邽߁AMicrosoft 񋟂銛uVisual Studio 2013 ̠Visual C++ ĔЕz\pbP[Wv](https://www.microsoft.com/ja-jp/download/details.aspx?id=40784)
CXg[ꂄ镋v邆v܂B炭 msvcr120.dll 
ꂎ\ȋC邌ŁAȒP̂ߊ
- http://dl.dropboxusercontent.com/s/z3t81hxc28p9qlk/msvcr120.dll

烟E[hł邦ɂĂ܂B

Hironobu Yamashita
