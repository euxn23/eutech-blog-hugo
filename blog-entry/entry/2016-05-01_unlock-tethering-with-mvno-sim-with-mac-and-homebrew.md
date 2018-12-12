
+++
date = "2016-05-01T18:25:00+09:00"
draft = false
title = "MVNO SIMのテザリングロックをMac/homebrewで解除する"
thumbnail = "images/nifmo.png"
tags = ["gadget", "google"]
categories = ["Tech"]

+++
SIMロック解除や、docomo系のMVNOを使う場合、通信はできてもテザリングができないという場合があります。

端末を有線接続し、本体を操作することで、root権限不要でテザリング可能に設定を変更することができます。

(変更の可否は端末によります。今回はXperia Z3 Compactで行いました。)

Windowsの場合はAndroid SDKの設定手順が多く大変ですが、Macの場合brewで環境が簡単に整います。

homebrewが入っていない場合はこちら

<a href="http://brew.sh/index_ja.html">Homebrew — OS X 用パッケージマネージャー</a>

以下、実行に必要なコマンド

<hr/>

<ol>
<li><code>brew install android-sdk</code> android-sdkのインストール</li>
<li><code>android -v</code> android-sdkがインストールされたことを確認</li>
<li><code>android update sdk --no-ui --filter &#39;platform-tools&#39;</code> android adbのインストール</li>
<li><code>adb -v</code> android-adbがインストールされたことを確認</li>
<li>スマートフォンをUSBデバッグモードにしてMacと接続</li>
<li><code>adb shell</code> 接続された端末にコマンドラインからログイン。ユーザ名が端末名になっていることを確認</li>
<li><code>settings put global tether_dun_required 0</code> 端末内でテザリングを有効化</li>
<li><code>exit</code>で端末からログアウトし終了</li>
</ol>


<hr/>

Macでは以上のコマンドで操作が完了します。

その他細かい点については、他に詳しいブログがあるので、そちらをご参照ください。

Android標準で用意されているコマンドの実行ですが、ご利用は自己責任でお願いいたします。

<iframe frameborder="0" allowtransparency="true" height="60" width="234" marginheight="0" scrolling="no" src="http://ad.jp.ap.valuecommerce.com/servlet/htmlbanner?sid=3248018&amp;pid=883723512" marginwidth="0"><script language="javascript" src="http://ad.jp.ap.valuecommerce.com/servlet/jsbanner?sid=3248018&pid=883723512"></script><noscript><a href="http://ck.jp.ap.valuecommerce.com/servlet/referral?sid=3248018&pid=883723512" target="_blank" ><img src="http://ad.jp.ap.valuecommerce.com/servlet/gifbanner?sid=3248018&pid=883723512" height="60" width="234" border="0"></a></noscript></iframe>



