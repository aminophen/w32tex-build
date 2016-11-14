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

����́A���� Visual Studio 2013 ���łǂ��ɂ��r���h�ɐ������� win32 ��
TeX �֘A�o�C�i����u���Ă������߂̏ꏊ�ł��B�����������̂����u���Ă���
����̂ŁA�p���搶�� W32TeX �ɔ�ׂăt�@�C���������Ă��܂��B
�����̗��K�ړI�ł��̂ŁA��p���Ȃ��ق����悢�Ǝv���܂��B���R���ۏ؂ł��B

�����g���Ă݂����ꍇ�́AW32TeX �� TeX Live (win32) �̌��X�̓����t�@�C��
�����l�[�����ĕۊǂ��Ă����A����ɂ��̃��|�W�g������擾�����t�@�C����
�u���Ă��������B����ȏ�̐����͂����čT���܂��B

Visual Studio 2013 �Ńr���h���Ă��邽�߁AMicrosoft ���񋟂���
[�uVisual Studio 2013 �� Visual C++ �ĔЕz�\�p�b�P�[�W�v](https://www.microsoft.com/ja-jp/download/details.aspx?id=40784)
���C���X�g�[������Ă���K�v������Ǝv���܂��B�����炭 msvcr120.dll ��
����Ώ\���ȋC������̂ŁA�ȒP�̂���

- http://dl.dropboxusercontent.com/s/z3t81hxc28p9qlk/msvcr120.dll

����_�E�����[�h�ł���悤�ɂ��Ă����܂��B

Hironobu Yamashita
