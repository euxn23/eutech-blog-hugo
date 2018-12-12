
+++
date = "2016-03-13T03:14:46+09:00"
draft = false
title = "WindowsでCDからflac、mp3にエンコードする(foobar2000)"
thumbnail = "images/foobar2000.jpg"
tags = ["audio", "windows"]
categories = ["Tech"]

+++
SONY製品が多いのでMedia Goで普段CDを取り込んでいたが、HDD増強したしホームシアター買いたいしで、flacにしてもいいんじゃないかと思い環境を探した。

foobar2000は開発も続いているし、UIも今はわかりやすいので、今回はこれを使用した。

foobar2000でのエンコードの場合、主に以下の設定が使用できるのが嬉しい。

<ul>
<li>ファイル保存の際のディレクトリ構造やファイル名を変数を用いて指定可能</li>
<li>エンコーダが詳細に設定可能</li>
<li>プレイリスト表示の高度なfilter、表示設定</li>
</ul>


#### 導入手順

以下の手順でfoobar2000とflacとlame(mp3)をインストール

<h6>foobar2000</h6>

<a href="https://www.foobar2000.org/">https://www.foobar2000.org/</a>から最新版をダウンロードしインストール

最初にUIを聞かれるのでお好きなものを選択

<h6>flac</h6>

<a href="https://xiph.org/flac/download.html">https://xiph.org/flac/download.html</a>からdownload項のWindowsにあるリンクからダウンロード

解凍後に含まれるflac(exeファイル)をfoobar2000のディレクトリ(標準であればProgram Files (x86)以下)に配置

<h6>lame</h6>

<a href="http://www.rarewares.org/mp3-lame-bundle.php">http://www.rarewares.org/mp3-lame-bundle.php</a>からダウンロード。64bit環境の場合はそちらを選択

foobar2000からは参照を指定するため、配置場所は自由。Program Filesに配置するのが無難か

あと、Lame Ain&#39;t an Mp3 Encoderって名前がかっこいい

#### foobar2000設定

エンコードの手順を行う中で都度必要な設定を行う

<ol>
<li>CDを読み込んだ状態でFile > Open audio CDを選択</li>
<li>CDドライブが認識されるので、選択しDrive settingsを選択

 Read offset correctionは右のautoボタンで自動設定

 Ripping securityはstandardを推奨。以上を設定したらOKをクリック</li>
<li>RipボタンをクリックしCD詳細画面へ

 Information lookupのSourceをfreedbに変更し、Lookupボタンで日本語の情報も取得できる

 Verify with AccurateRipにチェックを入れると次回も同じようにCD情報を取得する

 Process to the Converter Setup dialogをクリックし、エンコードの設定へ</li>
<li>エンコード設定を行う

 右側のOutput formatからflacを選択しbackをクリック

 Destinationをクリック。Output pathからSpecify folderに選択を入れればデフォルトの保存先を設定できる

 Output style and file name formattingからファイル名を設定する。右の...ボタンをクリックすることで複数種類の中から選択可能

 例えば<code>%album artist%/%album%/%track%. %title%</code>とすれば、<code>アーティスト/アルバム名/01. 曲名</code>となる

 設定が完了したらbackをクリック</li>
<li>Saveボタンでエンコード設定を保存する。名前にはflac等と指定する</li>
<li>mp3のエンコード設定を作成するため、Output formatをクリック

 Add newボタンで新規作成する。EncoderからまずMP3を選択してからCustomを選択すると初期情報が入っているので楽になる

 Encode fileに先にダウンロードしたlameファイルを指定する

 Extension(拡張子)はmp3と入力

 Parameterは最高音質にするのであれば、<code>-S --noreplaygain -b 320 - %d</code>と入力。固定(CBR)320kbpsとなる

 Bit depthのformatはlossy、Highest BPS mode supportedは24を選択

 Displayの項目で表示される名称を入力。MP3(320kbps)/320/CBRとするのが良いだろう</li>
<li>エンコーダを指定してリッピング開始

 flacの設定を指定し、convertボタンでエンコードを実行

 次回以降はRip now using one of the existing presetsから設定を指定して実行できる

 エンコード中のShow output tracks when doneのチェックを外すと、終了時に結果表示がなくなる</li>
<li>flacからmp3にエンコード

 リッピングしたflacからmp3にエンコードする方が、CDから取り込むよりも早い

 取り込んだファイルを開き、右クリック > Convertから、mp3(320)の設定を指定して実行

 複数ファイル選択し同時に実行できる</li>
</ol>



