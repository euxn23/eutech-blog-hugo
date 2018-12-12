
+++
date = "2015-11-23T21:53:07+09:00"
draft = false
title = "iPhone5S(iOS8)+mineoでauのLTEを安定動作させた話"
thumbnail = "images/mineo.jpg"
tags = ["apple", "gadget"]
categories = ["Tech"]

+++
半年間使用料無料で契約したmineoが届きました。
[mineoのauデータ回線が0円/月1GBで持てるキャンペーンを開始したので契約した - Wakotech Blog](http://yutaszk23.hatenadiary.jp/entry/2015/08/31/231402)

前回の通りiOS8のau版iPhone5Sで検証したところ、最終的に動作するようになったためそちらの報告です。

なお、個体差があるようですので、あくまで自己責任でお願いいたします。当方で責任は負いかねます。

# 結論

<ul>
<li>手順が少し面倒だが通信は安定する模様</li>
<li>電源が切れなければ継続して使用可能</li>
</ul>


# 試したこと

### 普通にプロファイル設定……→しばらくすると切断されるのでNG

以下の記事を参考にプロファイルを入れてみるも、最初のみ4G通信されるがすぐに切断……

[iPhone・iPadのAPN構成プロファイルの変更による動作確認テストについて（第３報） | 王国通信 | マイネ王](https://king.mineo.jp/magazines/special/116)

ここで切断されずに安定するケースもあるようですが、自分の個体はダメでした。

機内モードオンオフで一旦は復帰するものの、安定して使えるとは言えない状態です。

### auSIMを刺してから再度mineoに戻す→安定して動作！

auのSIMを刺すと良いというコメントを見かけたため実験してみることに。

auのSIM(解約済)を刺してから、再度mineoSIMに戻すと安定して動作するようになりました。

2週間ほど使用していますが<strong>電源が切れない限り安定して動作</strong>しています。

# 手順

<ol>
<li>auSIMを刺す(解約済SIM可、おそらく音声のみ)</li>
<li><a href="http://mineo.jp/apn/beta/test01-mineo.mobileconfig">mineo用APN構成プロファイル</a>をインストール</li>
<li>SIMが認識されたあと、mineoSIMに刺しかえる(この際、電源を切らない)</li>
<li>mineoSIMが認識され、4G通信が可能になる。この後、切断されずに通信が安定する。</li>
<li>電源オフになった場合、再度上記の手順で再び安定
(電源オフにしない限りこの手順は一度でOK)</li>
</ol>


# 最後に

キャンペーンは10月末までです。iPhone以外でも使用できますので、以前の機種で使いたいという方はこの機会に。

違約金はないため、MVNOを試してみるにはちょうどいいかもしれません。

<iframe frameborder="0" allowtransparency="true" height="60" width="234" marginheight="0" scrolling="no" src="http://ad.jp.ap.valuecommerce.com/servlet/htmlbanner?sid=3248018&amp;pid=883723512" marginwidth="0"><script language="javascript" src="http://ad.jp.ap.valuecommerce.com/servlet/jsbanner?sid=3248018&pid=883723512"></script><noscript><a href="http://ck.jp.ap.valuecommerce.com/servlet/referral?sid=3248018&pid=883723512" target="_blank" ><img src="http://ad.jp.ap.valuecommerce.com/servlet/gifbanner?sid=3248018&pid=883723512" height="60" width="234" border="0"></a></noscript></iframe>


次回はiOS9で動作確認したいところですが、まだiOS9の様子見をしているところ。

こういうときiPhone複数台欲しいですね……。


