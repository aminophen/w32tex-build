# w32tex-build

This is a trial build of binares of win32 TeX distribution.
Current binaries are mostly based on

- w32tex-src.tar.xz (as of 2021-03-23 23:15:54, r58680)

and some sources are updated along with TeX Live svn

- (nothing)

Some binaries are built with additional patches

- (nothing)

Also, some missing sources are retrieved from older archives

- w32tex-src.tar.xz (as of 2014-05-22 00:48, r34185)
- w32tex-src.tar.xz (as of 2017-05-14 07:02, r44344)
- w32tex-src.tar.xz (as of 2018-04-03 05:03, r47261)
- w32tex-src.tar.xz (as of 2019-04-08 21:59, r50878)
- w32tex-src.tar.xz (as of 2020-03-26 23:20, r54576)

some additional notes:

- [poppler-exe], [sam2p] are not up-to-date!
  - retrieved from r44334 (TeX Live 2017) and built on VS2013

Only a small subset of binaries are available, since these are the ones
which I managed to build by myself using Visual Studio 2010 and 2015.
The even better and stable binaries are also included in W32TeX
by Akira Kakuto, so there is no reason to choose ones in this repository.
No warranty.

## Additional Utilities for win32

In addition to TeX Live/W32TeX programs, the following utilities are also
available from this repository:

- Utilities from dviout (checked aminophen/dviout-util@e45ae9b)
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
