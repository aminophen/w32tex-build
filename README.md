# w32tex-build

This repository contains binary files of win32 TeX distribution.
Current binaries are mostly based on

- w32tex-src.tar.xz (as of 2017-05-14 07:02, r44334)

and some sources are updated along with TeX Live svn

- ktx/texk/dvidvi (r44675)
- ktx/texk/kpathsea/win32 (r44560)
- ktx/texk/seetexk (r44674)
- ktx/texk/ttfdump (r44679)

Some binaries are built with additional patches

  - (currently unavailable -- aminophen 2017-06-23)

Also, some missing sources are retrieved from older archives

- w32tex-src.tar.xz (as of 2014-05-22 00:48, r34185)
- w32tex-src.tar.xz (as of 2016-05-13 10:17, r41087)

some additional notes:

- ktx/utils/bmp2png: bmp2png 1.62
  - original retrieved from r34185
  - updated along with http://cetus.sakura.ne.jp/softlab/b2p-home/index.html
- xtx/texk/dvisvgm: dvisvgm 1.15.1
  - retrieved from r41087 to keep the old version (which can be built on VS2013)

Only a small subset of binaries are available, since these are the ones
which I managed to build by myself using Visual Studio 2013. The even
better and stable binaries are also included in W32TeX by Akira Kakuto,
so there is no reason to choose ones in this repository.
No warranty.

## Additional Utilities for win32

In addition to TeX Live/W32TeX programs, the following utilities are also
available from this repository:

- Utilities from dviout (checked aminophen/dviout-util@cf9c3b7)
  - chkfont.exe: Check font in DVI/TFM/JFM/FONT files
  - dvispc.exe:  Modify a DVI file to be page-independent in specials, translation between DVI <-> Text
  - propw.exe:   Generate TeX PL file for Japanese Proportional Fonts

----

これは、私が Visual Studio 2013 環境でどうにかビルドに成功した win32 の
TeX 関連バイナリを置いておくための場所です。成功したものしか置いていま
せんので、角藤先生の W32TeX に比べてファイルが欠けています。
ただの練習目的ですので、常用しないほうがよいと思います。当然無保証です。

あわせて、dviout の付属ユーティリティの独自改良版も置いてあります。
これらは dviout の DVI プレビュー機能とは独立に、便利に使えるものです。

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
