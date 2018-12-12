
+++
date = "2016-06-26T02:55:39+09:00"
draft = false
title = "ErgoDox EZのキーマップを変更して1週間程度使った"
thumbnail = "images/ergodox-ez.jpg"
tags = ["gadget", "keyboard"]
categories = ["Tech"]

+++
## 到着まで

購入概要については前回の記事を参照。

[ErgoDoxを注文した - Wakotech Blog](http://yutaszk23.hatenadiary.jp/entry/2016/06/05/020805)

106円/ドルのタイミングで購入したのと、カード会社の上乗せ分(2円程？)が入り、35,000円程度での決済だった。

到着までだいたい2週間。関税の支払いを受け取り時にするので、対面受け取りが必要。(1300円だった)

台湾から発送で、海外購入の業者から来ますが、土日の再発送だったのでクロネコヤマトに引き渡してくれた。便利。

## リマップ

<a href="https://github.com/jackhumbert/qmk_firmware">jackhumbert/qmk_firmware</a>からcloneなりforkなりする。

元のキーマップは<code>keyboard/ergodox_ez/keymaps/default</code>に存在するので、これを元に自分用のディレクトリを切る。

keymap.cに配置情報が書かれているので、これを編集する。当然ながらコメントを実装コードの両方の編集が必要。

引数をいい感じに改行してわかりやすくなっているので、これをなるべく崩さないようにするのが良い。

特殊な挙動を当てるキーコードについては、主に以下を参考にした。

[ErgoDoxのキーマップをいじる時に見るチートシート - Qiita](http://qiita.com/ReSTARTR/items/970354940f49c67fb9fd)

リマップしてからしばらく使っていると、主に親指まわりが納得いかず何度も修正することになる。

1週間経った現在でも安定していないので、結構長い戦いになりそう。

なお、半角/全角切り替えは、OS側でのリマップが必要だった。

モディファイアキー/任意のキーでのMod/Tapを設定し、任意のキーをOS側でIME制御に割り当てた。

残念ながら、この任意のキーは殺すことになる。自分はF15/16に死んでもらった。

OS XならばKarabinerのprivate.xmlでKeyToKeyを書く。WindowsはIME設定から設定できる。

(この時代にXMLを真面目に書くの、つらい気持ちがある。)

現在の自分の配置は以下の通り。


<div class="github-card" data-user="yutaszk/qmk_firmware/tree/master/keyboards/ergodox_ez/keymaps" data-repo="yutaszk" data-width="400" data-height="" data-theme="default"></div>
<script src="https://cdn.jsdelivr.net/github-cards/latest/widget.js"></script>


## 感想

<ul>
<li>元のキーボード(HHKB)を使った時に肩がきついことを感じるようになった。</li>
<li>小指を酷使しないようにリマップしたので、指の負担が減った気がする。</li>
<li>親指を変に動かすとこちらが疲れるので、意外と親指で色んなことはできない。</li>
<li>レイヤー機能でメタキーをOS上のソフトウェアに頼らず実装できるので、安定する。

<ul>
<li>特にWindowsのリマップが貧弱だったのが解消されたのは嬉しい。</li>
</ul>
</li>
</ul>


練習にe-typingをやったが、はじめはE評価だった。脳に指がついてくるようになるには、慣れが必要。


