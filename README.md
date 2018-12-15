# w32tex-build

This repository contains binary files of win32 TeX distribution.
Current binaries are mostly based on

- w32tex-src.tar.xz (as of 2018-04-03 05:03:03, r47261)

and some sources are updated along with TeX Live svn

  - (nothing)

Some binaries are built with additional patches

  - (nothing)

Also, some missing sources are retrieved from older archives

- w32tex-src.tar.xz (as of 2014-05-22 00:48, r34185)
- w32tex-src.tar.xz (as of 2017-05-14 07:02, r44344)

some additional notes:

- [bmp2png]
  - original retrieved from r34185
  - updated along with http://cetus.sakura.ne.jp/softlab/b2p-home/index.html
- [poppler-exe], [sam2p] are not up-to-date!
  - retrieved from r44334 (TeX Live 2017) and built on VS2013

Only a small subset of binaries are available, since these are the ones
which I managed to build by myself using Visual Studio 2013. The even
better and stable binaries are also included in W32TeX by Akira Kakuto,
so there is no reason to choose ones in this repository.
No warranty.

## Additional Utilities for win32

In addition to TeX Live/W32TeX programs, the following utilities are also
available from this repository:

- Utilities from dviout (checked aminophen/dviout-util@e45ae9b)
  - chkdvifont.exe: Check font in DVI/TFM/JFM/FONT files
  - dvispc.exe: Modify a DVI file to be page-independent in specials, translation between DVI <-> Text
  - propw.exe: Generate TeX PL file for Japanese Proportional Fonts

----

これは、私が Visual Studio 2010/2015 環境でどうにかビルドに成功した
win32 の TeX 関連バイナリを置いておくための場所です。
成功したものしか置いていませんので、角藤先生の W32TeX に比べてファイルが
欠けています。
ただの練習目的ですので、常用しないほうがよいと思います。当然無保証です。

あわせて、dviout の付属ユーティリティの独自改良版も置いてあります。
これらは dviout の DVI プレビュー機能とは独立に、便利に使えるものです。

もし使ってみたい場合は、W32TeX や TeX Live (win32) の元々の同名ファイル
をリネームして保管しておき、代わりにこのリポジトリから取得したファイルを
置いてください。それ以上の説明はあえて控えます。

多くは Visual Studio 2010 でビルドしていますが、必要なものだけ
Visual Studio 2015 でビルドしています。
Microsoft が提供する
「[Microsoft Visual C++ 2010 再頒布可能パッケージ](https://www.microsoft.com/en-US/download/details.aspx?id=5555)」
及び
「[Visual Studio 2015 の Visual C++ 再頒布可能パッケージ](https://www.microsoft.com/en-US/download/details.aspx?id=48145)」
が必要なものが含まれます。

Hironobu Yamashita
