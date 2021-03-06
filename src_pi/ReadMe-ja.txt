----------------------------------------------------------------
* テキスト音楽「サクラ」 for Raspberry Pi (Raspbian用)
----------------------------------------------------------------

テキスト音楽「サクラ」は、エディタに『ドレミ』と書けば、その通りに音楽を演奏することができるソフトです。 パソコン＋サクラの本体だけで、本格的な音楽制作ができます。 スクリプト機能を持ち繊細な音楽表現やアルゴリズム作曲もできます。 加えて、掲示板6にて ユーザーさんの作った曲を聴くこともできます。これまでに、1万曲以上がサクラを使って作られています。小中学校(教育の現場)でも使われています！高校の情報の教科書にも掲載されました。オンラインゲームやイベント・店内向けBGM素材作成にも使えます。 

- [Webサイト] http://oto.chu.jp/
- [曲掲示板] http://oto.chu.jp/mmlbbs6/

----------------------------------------------------------------

* Raspberry Piでの音楽制作環境を整える

最新のRaspbianでは、timidityがインストールされています。
古いRaspbianを利用している場合には、timidityのインストールが必要です。

もし、timidityがインストールされてなければ、MIDIファイルが再生できるように、timidityをインストールします。コマンドラインから以下のコマンドを実行しましょう。

{{{
sudo apt-get install timidity 
sudo apt-get install fluid-sound-font-gm fluid-sound-font-gs
}}}

もし、曲掲示板の曲を聴きたい場合には、掲示板のMMLファイルの文字コードをUTF-8に変換してから実行する必要があります。以下のコマンドを実行して、文字コードの変換プログラムを入手しましょう。

{{{
sudo apt-get install nkf
}}}
  
----------------------------------------------------------------

* サクラのダウンロード

サクラ for Raspberry Piは、以下よりダウンロードできます。以下よりダウンロードします。

- http://kujirahand.com/blog/go.php?688

----------------------------------------------------------------

* サクラで音楽を再生するまで

Raspberry Piで好みのテキストエディタでテキストを編集しましょう。
「pico」を使う場合、コマンドラインに以下のように入力して、picoを起動します。

{{{
pico hana.mml
}}}

さらに、以下のようなサクラの楽譜を入力したら、[Ctrl]+[X]キーを押して、その後、[Y]キー、その後[Enter]キーをタイプします。

{{{
音符４
ドレミー　ドレミー　ソミレド　レミレー
ドレミー　ドレミー　ソミレド　レミドー
ソソミソ　ララソー　ミミレレ　ドーーー
}}}

そして、楽譜データをMIDIファイルに変換します。ターミナルへ以下のように入力します。
 
{{{
./sakura hana.mml
}}}

すると、「hana.mid」というMIDIファイルが出力されます。次に、timidityでMIDIファイルを再生しましょう。

{{{
timidity hana.mid
}}}

----------------------------------------------------------------

* C言語のソースからインストールする場合


{{{
# ctagsが必要です（暫定ですが)
$ sudo apt-get install ctags

# GitHubからソースコード一式をダウンロードします
$ git clone https://github.com/kujirahand/sakuramml-c
$ cd sakuramml-c
$ make
}}}












