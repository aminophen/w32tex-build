# w32tex-build

This repository contains binary files of win32 TeX distribution.
Current binaries are mostly based on

- w32tex-src.tar.xz (as of 2016-05-13 10:17)

and some sources are updated along with TeX Live svn

- ktx/texk/kpathsea (r42472)
- ktx/texk/dvipdfm-x (r42391)
- ktx/texk/dvipsk (r42461)
- ktx/texk/mendexk (r42492)
- ktx/texk/tex4htk (r42110)
- ktx/texk/web2c (r42506)
- ktx/texk/web2c/eptexdir (r42506)
- ktx/texk/web2c/euptexdir (r42506)
- ktx/texk/web2c/lib (r42506)
- ktx/texk/web2c/pdftexdir (r42438)
- ktx/texk/web2c/ptexdir (r42040)
- xtx/texk/kpathsea (r42472)
- xtx/texk/upmendex (r42493)
- xtx/texk/web2c (r42506)
- xtx/texk/web2c/lib (r42506)
- xtx/texk/web2c/xetexdir (r42194)

Only a small subset of binaries are available, since these are the ones
which I managed to build by myself using Visual Studio 2013. The even
better and stable binaries are also included in W32TeX by Akira Kakuto,
so there is no reason to choose ones in this repository.
No warranty.

----

これは、私が Visual Studio 2013 環境でどうにかビルドに成功した win32 の
TeX 関連バイナリを置いておくための場所です。成功したものしか置いていま
せんので、角藤先生の W32TeX に比べてファイルが欠けています。
ただの練習目的ですので、常用しないほうがよいと思います。当然無保証です。

もし使ってみたい場合は、W32TeX や TeX Live (win32) の元々の同名ファイル
をリネームして保管しておき、代わりにこのリポジトリから取得したファイルを
置いてください。それ以上の説明はあえて控えます。

Visual Studio 2013 でビルドしているため、Microsoft が提供する
[「Visual Studio 2013 の Visual C++ 再頒布可能パッケージ」](https://www.microsoft.com/ja-jp/download/details.aspx?id=40784)
がインストールされている必要があると思います。おそらく msvcr120.dll が
あれば十分な気がするので、簡単のため

- http://dl.dropboxusercontent.com/s/z3t81hxc28p9qlk/msvcr120.dll

からダウンロードできるようにしておきます。

Hironobu Yamashita
