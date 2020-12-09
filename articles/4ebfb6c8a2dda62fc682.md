---
title: "Iosevkaというフォントが良い"
emoji: "ℹ️"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["font"]
published: true
---
突然ですが、皆さんはどのフォントでコーディングしていますか?
monaco、Monospace、MSゴシックなど、種類は多種多様です
そんな中、それらを尻目に私が使っているフォントはIosevkaというフォントです

# Iosevkaとは?

以下の特徴を持ったフォントです

* 等幅フォント
* 日本特有の文字種(㈱や㌕など)に対応
  * これらもきっちりと等幅を守っている
* リガチャ機能あり
  * `!=`や`<=`など、特定の連続した文字列を合成して別の文字で表す機能
* 特定の文字をプリセットの中から選ぶ事ができる
  * プリセットから選んで、特定の文字のみデザインを変更することも可能
* 全体的な文字の太さ、デザイン、文字のゆとりも設定することが可能

特に

> 特定の文字をプリセットの中から選ぶ事ができる
> 全体的な文字の太さ、文字のゆとりも設定することが可能

が個人的に目玉です
他のフォントでは見たことないレベルで、カスタマイズが可能です
これだけでは「はい・・・?」と想像しづらい(できない)と思われるので、詳細を説明していきます

# 公式サイト

こちらになります

https://typeof.net/Iosevka/

一番見てもらいたいところは

> Variants à la Carte

の部分です

![](https://i.gyazo.com/05cbd9e3aca561d3c7a9a185ddd664af.gif)

この通り、58文字を自分の好きなデザインに変えられることができます
他にも

* サンセリフ調にするか否か
* 文字の太さの調整
* リガチャのプリセット設定
  * リガチャ自体を無効にすることも可能
  * 文字の様に文字単位でのリガチャの無効やデザイン変更はできない

という様に、自分が違和感なく使えるフォントを徹底的に設定することができます

# フォントの入手方法

大きく分けて2つあります
「GitHubのReleaseページからフォントをダウンロード」と、「GitHubからソースをクローンしてビルド」になります

## GitHubのReleaseページからフォントをダウンロード

:::message
この方法では、文字ごとのカスタマイズなどはできません
:::

公式サイトにあるStylistic Setsなどのプリセットで十分という方は、以下のページからフォントをダウンロードすることができます

https://github.com/be5invis/Iosevka/releases

## GitHubからソースをクローンしてビルド

以下のリポジトリをクローンして、ビルドを行うと、フォントがジェネレートされます

https://github.com/be5invis/Iosevka

GitHubにも、ビルドする手順が掲載されているので、一読すると良いです

https://github.com/be5invis/Iosevka#building-from-source

### ビルドを試す

まずは、ビルドが正常に動作するか確認します

#### 必須環境

ビルドをするには、以下の環境が必要になります

* Node.js(12.16.0以上のバージョン)
* `ttfautohint`のインストール(`npm i ttfautohint`でOK)

#### ビルド方法

:::message
負荷のかかる処理なので、別作業をしながらビルドすると、結構カクつきます
しばらく放置することになると思います
:::

以下のコマンドを実行するだけです

```shell
npm install
npm run build -- contents::iosevka
```

正常に完了すれば、`dist/`内にフォントがあると思います

### フォントをカスタマイズする

ここから、Iosevkaの本領発揮をする、フォントを自分好みにカスマイズします
もちろん、GitHubにも以下のリンクから説明されています

https://github.com/be5invis/Iosevka#customized-build

ですが、自分の環境だと、↑の方法ではエラーになってできたなかったので、`private-build-plans.sample.toml`を直接編集します

各設定項目と、設定できる値については、以下を参考にしてください

https://github.com/be5invis/Iosevka#configuring-custom-build

ここで編集しておくべき項目は`[buildPlans.iosevka-custom]`にある`family`です
ここで設定した値が、インストールしたときのフォント名になるので、自分が作成したとわかる様な名前にしてください

`private-build-plans.sample.toml`を好きなようにカスタマイズできたら、もう一度`npm run build -- contents::iosevka`を実行します
正常に終了したら、`[buildPlans.iosevka-custom]`の`family`に設定したフォント名のファイルができていると思います

# 最後に

中国語、日本語は更紗ゴシックと言うフォントがあります

https://github.com/be5invis/Sarasa-Gothic

Iosevkaと源ノ角ゴシックをベースに指定しているみたいですが、カスタマイズはできなさそう?(やったことないので、憶測になります)