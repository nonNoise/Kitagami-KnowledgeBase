=====================================================
PoketBeagle セットアップ方法
=====================================================


■はじめに
-----------------------------------------------------

Pocketbeagleとは、半導体メーカであるテキサス・インスツルメンツ（TI）社より開発された、
BeagleBoneシリーズの一つで、最も小さいモデルである。

PocketBeagleの目玉はボードの小ささであり、BeagleBoneBlackと同じCPUを持ちつつ、
BeagleBoneBlackで使用されていた AM335X を継承した形で、DDR3メモリや電源回路をワンチップに収めた
OSD3358-SMを使っている所である。

RaspberryPiも同様にCPUとメモリをワンチップとして生産されているが、こちらは電源回路もワンチップ化されている。


.. image:: https://www.digikey.jp/-/media/Images/Product%20Highlights/O/Octavo%20Systems/OSD335x-SM%20System-In-Package%20SiP%20Family/octavo-osd335x-sm-200-2.jpg?ts=80a1d435-556e-4e06-a2f7-2a4f69f5dbd4&la=ja-JP
    :width: 480px
    :target: https://www.digikey.jp/ja/product-highlight/o/octavo-systems/osd335x-sm-system-in-package-sip-family

RaspberryPiと大きく違う点は、PocketBeagleはCPU単品を小売りして購入することが出来る点である。

RaspberryPiで使用されているCPUは単体では購入出来ず、どうしてもRaspberryPi本体を購入しなければならいが、PocketBeagleで使われているCPUは単体で購入することが出来る。
更に、購入出来ても設計が難しい際は難儀を示すが、先ほど述べた通りPocketBeagleのCPUには配線が複雑なメモリや電源といった箇所がワンチップで提供されている。
その為、CPUを購入し自作のシングルコンピュータボードを作成することができる。

自作マザーボードといった夢のある話を評価するに打ってつけのPocketBeagleボードである。


:CPU: ARM Cortex-A8 
:プロセッサ: AM335x 
:クロック: 1GHz
:メモリ: 512MB DDR3 RAM
:USB: x2(OTG対応)
:SD: x1
:ADC: 
:DAC:
::
