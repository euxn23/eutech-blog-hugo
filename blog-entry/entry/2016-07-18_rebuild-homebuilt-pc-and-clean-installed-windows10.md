
+++
date = "2016-07-18T21:03:01+09:00"
draft = false
title = "自作PCのパーツを変更しながらにWindows10をクリーンインストールする"
thumbnail = "images/windows10.png"
tags = ["pc", "windows"]
categories = ["Tech"]

+++
Windows10をアップグレード無しに直接クリーンインストール可能な話を見るが、ほとんどがメーカ製のPCの話が殆どである。

Windows10のライセンスが自作PCとあわないという話を見ましたが、問題なかったので手順を記述する。

<strong>私の環境では成功したという例です。</strong>自己責任にてお願いします。

# 手順

<ul>
<li>パーツを新しいものに交換する。(GPUはドライバが必要なので後から取り付ける。)</li>
<li>起動ディスクにWindows7をインストールし、ライセンス認証を行う。(自分はクリーンインストールした。)</li>
<li>この時点でライセンス認証ができない場合、MSに問い合わせる。</li>
<li><a href="https://www.microsoft.com/ja-jp/software-download/windows10">https://www.microsoft.com/ja-jp/software-download/windows10</a>からメディア作成ツールをダウンロードし、インストールメディアを作成する。</li>
<li>PCをシャットダウンし、インストールメディアからブートしてインストールを開始する。問題なければ、インストール先のディスクをフォーマットする。</li>
<li>インストール後にWindows7のライセンスキーでオンライン認証を行う。</li>
<li>システム情報(Windows + Pause)からライセンスが認証されていることを確認する。</li>
<li>GPUのドライバをダウンロードしておき、GPUを取り付けて再度起動し、インストールする。(GeForceは<a href="http://www.nvidia.co.jp/download/driverResults.aspx/87933/jp">http://www.nvidia.co.jp/download/driverResults.aspx/87933/jp</a>からDL可能。)</li>
<li>すべてのパーツを付けた状態でライセンスが認証されていることを確認する。</li>
</ul>


# 補足

<ul>
<li>パーツ構成の軸はマザーボードのようである。</li>
<li>パーツの構成とライセンスを関連付けて記録するとのことで、一旦新しい構成でWin7を認証した。</li>
</ul>


# 参考

<ul>
<li><a href="http://it.english-and-paso.com/soft/windows10-cleaninstall/">Windows 10をアップグレード抜きで無償クリーンインストール。 | PCユーザーメモ</a></li>
<li><a href="http://kiritsume.com/how-to-clean-install-free-upgraded-windows10/">http://kiritsume.com/how-to-clean-install-free-upgraded-windows10/</a></li>
<li><a href="http://mirunews.jp/9494">Windows10 のライセンス認証が厳しすぎるので Windows7/8.1 からの移行は要注意</a></li>
<li><a href="http://freesoft.tvbok.com/win10/installation/licence_of_free_upgrade.html">無料アップグレードしたWindows10の パーツ変更、再認証、ライセンスの扱いについて</a></li>
</ul>



