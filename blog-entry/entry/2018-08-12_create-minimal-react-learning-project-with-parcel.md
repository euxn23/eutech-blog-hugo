+++
date = 2018-08-12T18:00:00+09:00
title = "Parcel ベースの極小 React 学習用プロジェクトを作った"
thumbnail = "images/react.png"
tags = ["react", "parcel", "newbie"]
categories = ["Engineering"]
# ["Tech", "Engineering", "Life", "Poem", "DevEnv", "Otaku", "Career"]
+++

[euxn23/minimal-react-parcel](github.com/euxn23/minimal-react-parcel)

React の現場に入ったがフロントエンド未経験、という人に教えることになったが、ペアプロをしようにもビルドツールまわりが入ってくると非常に面倒なことになった。

`create-react-app は複雑なので使いたくない` `webpack や babel 等の文脈に触れたくない` `React のコードが動けば良い(プロダクションではない)` という要件だったので、これなら parcel で良いのでは、と思い作った。

`$ parcel src/index.html` で watch して差分ビルドしつつ、自動リロードされる画面が localhost:1234 に立ち上がる。zero config でここまでできる。

もちろんパフォーマンスとかエントリーポイントの分割とか色々する場合は webpack の方が枯れているが、あまり package.json にずらずらと書いてあって、「これはおまじない」とするのもあまりよくないかな、と思った次第である。

時期が来たら、というか実運用されているコードを読むことが先になるだろうが、そのときに改めて webpack / babel の話をすればよいと思う。初心者にいきなりその話は時期尚早であると感じる。