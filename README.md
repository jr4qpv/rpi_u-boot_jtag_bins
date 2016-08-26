rpi_u-boot_jtag_bins
====================
u-boot binary for raspberry pi enabled jtag.

概要
----
Raspberry Pi Zero/2/3用の、コンパイル済みのu-bootバイナリー。  
u-bootの初期起動時に、Raspberry PiのJTAGピンを有効にして立ち上がる。  
u-boot起動後、JTAGデバッガ経由でプログラムのダウンロードや実行する事も可能。又、JTAG機能は使わなくてもu-bootからプログラムのロードや実行もできる。

詳しくは、下記の関連ブログを参照

* [【Raspberry Pi】u-bootでJTAGピンを有効にする](http://jr4qpv.hatenablog.com/entry/2016/08/23/142543)
* [【Raspberry Pi】u-bootを動かす](http://jr4qpv.hatenablog.com/entry/2016/08/13/084519)
* [【Ubuntu 16.04 LTS Server】u-bootをコンパイルする](http://jr4qpv.hatenablog.com/entry/2016/08/11/093517)

使い方
------
FATでフォーマット済みのマイクロSDカードに、機種に合わせた下記４つのファイルをSDカードのルートに書き込む。そのSDカードをRaspberry Piにセットし電源起動すると、u-bootが起動する。シリアルコンソールに起動メッセージを表示してカウントダウンするので、何かキーを押すとコマンド入力できる。"help"と入力すると使えるコマンドの一覧が表示される。

1. `bootcode.bin`    boot.zip から解凍しコピー
2. `start.elf`       boot.zip から解凍しコピー
3. `u-boot.bin`      機種別.zip から解凍しコピー
4. `config.txt`      機種別.zip から解凍しコピー

|機種別ファイル|対応機種         |備考            |
|:-------------|:----------------|:---------------|
|rpi           |Raspberry Pi Zero|Pi1では未確認   |
|rpi_2         |Raspberry Pi 2   |                |
|rpi_3_32b     |Raspberry Pi 3   |32bitモード     |

※各ファイルはzip圧縮してあるので解凍して利用する。

JTAGピン割り当て
----------------
Raspberry PiコネクタのJTAG信号の割り当ては下記

|ピン番号|GPIO番号|GPIOモード|機能（JTAG）|
|:-------|:-------|:---------|:-----------|
|15      |GPIO22  |ALT4      |TRST        |
|7       |GPIO4   |ALT5      |TDI         |
|13      |GPIO27  |ALT5      |TMS         |
|22      |GPIO25  |ALT5      |TCK         |
|18      |GPIO24  |ALT5      |TDO         |

bootファイル入手先
------------------
上記、1)と2)のファイルは、下記URLから入手（2016/08/11版）  
<https://github.com/raspberrypi/firmware/tree/master/boot>

u-bootソースファイル入手先
--------------------------
3)のファイルは、下記URLから入手(2016/08/16版)し、｢[GNU ARM Embedded Toolchain](https://launchpad.net/gcc-arm-embedded)｣でコンパイル  
<git://git.denx.de/u-boot.git>

JTAG有効化で変更したソースの箇所は、関連ブログの記事を参照。

作者関連サイト
--------------
* [Around the modern stone age.](http://jr4qpv.hatenablog.com/)
* [JR4QPV Yoko's Library](http://jr4qpv.my.coocan.jp/)

免責
----
本プログラムの使用にあたっては、使用者自身の責任で行ってください。作者は何の保証もしないし、本プログラムを利用した上で生じたいかなる障害や損害についても、作者は責任を負いません。


履歴
----
* 2016/08/25 公開(By JR4QPV)
* 2016/08/26 ファイルはzip圧縮して公開するように変更
