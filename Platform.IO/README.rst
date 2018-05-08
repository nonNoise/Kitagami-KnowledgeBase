================================================================================
Platform.IOでマイコン開発環境を整える
================================================================================


----------------------------------------------------------------------

このサイトは、mbedやArduinoなど幅広いボードを開発出来、オフライン開発環境を超手早く構築できる
PlatformIOの紹介と手順をまとめたサイトです。

PlatformIOとは何ですか？
----------------------------------------------------------------------

PlatformIOとは、Pythonの力を使いGCCのコンパイル環境をOSやボードに合わせて自動生成する画期的なプログラムです。

近年、Arduinoやmbed、その他マイコンがGCCでコンパイル出来ることが増え、CPUを変えた際にリンカプログラムの書き換えが必要だったりGCC自体違うものを使用したりと
非常に大変な作業が多く、皆簡単に出来ると言い丸っと１日費やしてしまう。

PlatformIOはそんな手作業を自動化し、ビルド済みで配布する画期的な仕組みとなっている。

また、Arduinoやmbedは開発団体があり、そこに登録を行わないと開発環境は提供されないが、PlatformIOはコンパイル環境の提供であるため、
例えばカスタムボード用の環境や事業で使用するボード、性能違いピンパッケージ違いなどの細かな微調整も加工次第では対応することができる。

PlatformIOに関しては、MONOISTの以下の記事が大変判りやすく、また記事になるほど業界への影響があることが伺える。

::

    ◇ MONOIST ベンダーに染まらない「PlatformIO」 (1/3)
    http://monoist.atmarkit.co.jp/mn/articles/1610/31/news005.html


また、EclipseというIDEとはどう違うかという話もあるが、PlatformIOはGCCコンパイルを自動化したコマンドツールである。

そのため、勿論Eclipseで使用することも可能だが（そんなことをする人が居るはずないが）近年は、ATOMやVSCodeと言った
WEB開発者向けの高品質エディタに組み込んで使うことが多い。当然ながら、エディター＋コマンドで開発していくことも可能である。

セットアップ方法
-------------------------------------------------------------------------------

PlartformIOはコマンドでインストールしていきます。Windows,Mac,LinuxどのOSにも対応しております。

大まかなステップ

・Python 環境を整える(2.7専用)

・pipを使ってPlatformIO環境をインストール

・コマンドの確認

以上

▼　Windowsの場合
--------------------------------------------------


・Python 2.7をインストール(3.xでは動きません涙)

https://www.python.org/downloads/release/python-2714/

この辺で、32bitの方は「Windows x86 MSI installer」 64bitの方は「Windows x86-64 MSI installer 」を。

全てOKで進めて行けば、今だとPATHまで自動で入ると思われるので、再起動後にコマンドプロントで「python -V」を入力します。

無事にコマンドが認識すればOK。

続いて pipコマンドを入れます。

・pipコマンドをインストール

https://bootstrap.pypa.io/get-pip.py 

より、ソースをダウンロードして、コマンドよりcdやdirを駆使して 「python get-pip.py」 を実行します。

無事に完了すると、コマンド pip が使用できるように成ります。

・pipを使ってPlatformIOをインストールする。

コマンドで「pip install platformio」で全自動でGCCやらヘッダーファイルやら何やら全部インストールが出来ます。

::

    pip install platformio

・インストールが終わったら、PlatformIO用のコマンドが動くか確認

PlatformIOのコマンドは２種類あり、

::

    platformio

と、

::

    pio

の２種類です。どちらも同じ動きをしますが、記述が面倒なので「pio」を主力として記述していきます。

もし、大きな力でpioが他のコマンドとかぶる際は、仕方がなくplatformioと全部書くようにしましょう。

以上でPlatformIOが使えるようになったと思います！（多分）


▼　Mac,Linuxの場合
--------------------------------------------------

Pythonがデフォルトでインストールされているため、Super-Quick手法でインストールします。

::

    python -c "$(curl -fsSL https://raw.githubusercontent.com/platformio/platformio/develop/scripts/get-platformio.py)"

以上でPlatformIOが使えるようになったと思います！



▼　Platform.IOで使えるコマンド
--------------------------------------------------

基本形
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    pio [OPTIONS] COMMAND
    platformio [OPTIONS] COMMAND

    ※コマンドは両方使用することができます。ただ毎回platformioと記述するのが面倒なので、pioで慣れてしまうのがおすすめです。どちらも同じ動きをします。

::

    Options:

        --version          Show the version and exit.
            PlatformIOのバージョン表示

        -f, --force        Force to accept any confirmation prompts.

        -c, --caller TEXT  Caller ID (service).

        -h, --help         Show this message and exit.
            Platformのコマンドの意味などを確認できます。

::

    Commands:

        account   Manage PIO Account
            PlatformIOに登録したアカウントにアクセスしたりできます。

        boards    Embedded Board Explorer
            PlatformIOで開発できるボードを確認できます。

        ci        Continuous Integration
    
        debug     PIO Unified Debugger
        
        device    Monitor device or list existing
            PlatformIOに登録されているデバイスの確認ができる

        init      Initialize PlatformIO project or update existing
            PlatformIOを新規に作成する際の初期化コマンド

        lib       Library Manager

        platform  Platform Manager
            PlatformIOに登録されているプラットフォーム（開発環境）への操作

        remote    PIO Remote

        run       Process project environments
            プロジェクトのmakeや書き込み等一括で行うコマンド

        settings  Manage PlatformIO settings
            PlatformIOの設定の確認や変更ができます。

        test      Local Unit Testing

        update    Update installed platforms, packages and libraries
            Platformやライブラリをアップデートします。

        upgrade   Upgrade PlatformIO to the latest version
            PlatformIO自体のアップグレードができます。


最初の設定
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    pio init --board <ボードID>


ボードIDは以下のコマンドより確認することができます。

::

    pio boards 
        これで全部表示

    pio boards arduino
        Arduinoとして登録されているボード一覧
    
    pio boards mbed
        mbedとして登録されているボード一覧
    
    pio boards stm32
        STM32系列のボード一覧
    
    pio boards > boards.TEXT   
        ボード一覧をテキストに保存

PlatformIO, version 3.4.1(2017/10/28　現在登録されているボードリスト)

    https://raw.githubusercontent.com/nonNoise/PlatformIO-MakeIt/master/Sphinx/rst/boards.txt

試しに、ArduinoUno の環境を整えます。ArduinoUnoのボードIDは"uno"となりますので（わかりづら！）

::

    pio init --board uno

するど、フォルダーの中に

::

    platformio.ini - Project Configuration File
        PlatformIOの設定ファイル（主にボードIDやファームウェアなど)

    src - Put your source files here
        プログラムを入れるフォルダ。

    lib - Put here project specific (private) libraries
        ダウンロードしたライブラリなどを入れるフォルダ

が出力されます。

試しにLチカプログラム Blinks を試して見たいと思います。

以下のプログラムを　scrフォルダの中で **main.cpp**　というファイルを作り貼り付けます。

::

    /**
    * Blink
    *
    * Turns on an LED on for one second,
    * then off for one second, repeatedly.
    */
    #include "Arduino.h"

    #ifndef LED_BUILTIN
    #define LED_BUILTIN 13
    #endif

    void setup()
    {
        // initialize LED digital pin as an output.
        pinMode(LED_BUILTIN, OUTPUT);
    }

    void loop()
    {
        // turn the LED on (HIGH is the voltage level)
        digitalWrite(LED_BUILTIN, HIGH);

        // wait for a second
        delay(1000);

        // turn the LED off by making the voltage LOW
        digitalWrite(LED_BUILTIN, LOW);

        // wait for a second
        delay(1000);
    }

コピペとかが面倒な際は、以下のコマンドでダウンロードしてきます。

::

    wget https://raw.githubusercontent.com/nonNoise/PlatformIO-MakeIt/master/Sphinx/sorce/arduino/blinks.cpp

blinksプログラムが整ったら、**run** コマンドでコンパイルをします。

::

    pio run

すると、このタイミングでArudinoUNOに必要な開発環境(主にGCC周りや書き込み用ライブラリ)を自動でダウンロードからインストールまで行います。

この動作が大変、大変便利で気持ちよく開発を行うことができます。真似して行きたい環境セットアップ手法ですね。

開発環境のインストールが行われて無事にコンパイルも行われると、最後に以下のような表示がされるはずです。

::

    AVR Memory Usage
    ----------------
    Device: atmega328p

    Program:     928 bytes (2.8% Full)
    (.text + .data + .bootloader)

    Data:          9 bytes (0.4% Full)
    (.data + .bss + .noinit)

    ========================= [SUCCESS] Took 2.38 seconds =========================

コンパイルまでの時間の確認も面白いですが、肝心な項目は **使用メモリー** の箇所です。
自分が作成したプログラムがマイコンのメモリーをどれくらい消費しているか。
プログラマーは常にマイコンのメモリー空間を意識しながら書いて行くと、大変良いプログラムが出来上がると思います。

▼まとめ
--------------------------------------------

以上の内容でPlatformIOの基本的なコマンとの流れが掴めたかと思います。

大まかにまとめると

::

    pio boards
        これで使いたいボードIDを探す
    pio init --board uno
        これでボードID"uno"を選択して初期化
    scrフォルダにmainソースを書く 
    pio run
        runコマンドでコンパイルを行う。GCC環境とかがなければ自動でインストールする。

こんな感じですかね。

次回以降、それぞれの開発環境に合わせたコマンドや書き込み方法をまとめて行きます。



----------------------------------------------------------------------

◇本家サイト

    http://platformio.org/

◇本家Github

    https://github.com/platformio

◇本家ドキュメント    

    http://docs.platformio.org/en/latest/userguide/demo.html#blink-project






管理情報
******************************************************************
:著者: 北神 雄太(Yuta Kitagami)
:連絡先: kitagami@Artifactnoise.com
:公開日: 2017/10/14 mbed祭り 2017@秋の虎ノ門の帰宅後 

外部リンク
******************************************************************

:ArtifactNoise:  http://artifactnoise.com/
	
:Twitter: @nonNoise  http://twitter.com/nonNoise

:FaseBook: https://www.facebook.com/yuta.kitagamiEx
