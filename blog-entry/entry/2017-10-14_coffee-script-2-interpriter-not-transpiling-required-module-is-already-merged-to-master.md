+++
date = 2017-10-14T03:36:41+09:00
title = "coffeescript2 インタプリタのtranspile オプションでrequire されたmodule に対して適用されない問題が既にmaster にマージされていた"
thumbnail = "images/coffeescript.png"
tags = ["javascript", "coffeescript", "babel"]
categories = ["Engineering"]
+++

CoffeeScript2 では、初代と同様にインタプリタとしても機能する。

CoffeeScript の仕様としてES Modules (import/export) やJSX をサポートしているものの、それはコンパイルを通すだけであり、実行時には環境に解釈される(=現状では動かない)というものとなっている。

(ので、サポートというか、シンタックスエラーとして扱わずそのままJS にしてくれている、くらいの感覚。)

そこでCoffeeScript はBabel の使用をサポートしており、 `.babelrc` を配置して `--transpile` オプションを付与して実行するだけで、

Babel でのトランスパイルまで一度に行える。

サーバサイドのプログラムを `babel-node` や `ts-node` のように、coffee のインタプリタで動作させるにあたり、上記を使用して `import/export` を使用できないかと試みた。

※[teppeis さんのブログ](http://teppeis.hatenablog.com/entry/2017/08/es-modules-in-nodejs)でも触れられていますが、ES Modules は今になっても安定していない(named import が使えなくなったり)ので、使っているのはカッコイイという理由だけです。長く使うコードでもないし。

しかし、実際には実行時にコマンドに渡したルートファイルのみBabel でトランスパイルされるため、import されているファイルはトランスパイルされず、import/export の部分でSyntax Error が発生するという状態になっていました。

とりあえず[issue に書いた](https://github.com/jashkenas/coffeescript/issues/4745)ところ、なんと既にmaster にはmerge されていたとのことで、手元でmaster で試して動作確認できました。

次のリリースには乗りそうなので安心ですね。めでたしめでたし。



CoffeeScript2、もともとCoffee 好きなので書いていた楽しい感じなのだけど、Flow のType Annotation だけはどうにかならなかったのかなあ……。