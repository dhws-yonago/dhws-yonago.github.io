---
layout: post
title: jQuery のあれこれ
author: Webトレーナー S.Yabu
tags:
  - jquery
  - coding
---



<!--more-->

## 1. `<script></script>` タグの記述位置について

```html
<!DOCTYPE html>
<html>
  <!-- 省略 -->
  <body>
    <!-- 省略 -->
    <script src="https://code.jquery.com/jquery-3.6.0.min.js" integrity="sha256-/xUj+3OJU5yExlq6GSYGSHk7tPXikynS7ogEvDej/m4=" crossorigin="anonymous"></script>
    <script src="./assets/js/main.js"></script>
  </body>
</html>
```

`<script></script>` タグによる JavaScript の読み込みは `</body>` の直前に記述するのが現在のモダンな実装です。  
これは JavaScript の処理によってレンダリングを阻害することを防ぐことによりページの描画を早めるというメリットがあります。  
また DOM 要素をすべて読みこんだ後に JavaScript の処理が発生するため、 DOM が存在せずエラーになるといったことも防げます。  

※なお特定の実装条件において [例外](https://ssig33.com/text/JavaScript%20%E3%82%92%E6%9C%80%E4%B8%8B%E6%AE%B5%E3%81%A7%E8%AA%AD%E3%81%BF%E8%BE%BC%E3%82%80%E3%81%AE%E3%81%8C%E3%81%82%E3%81%BE%E3%82%8A%E6%9C%89%E5%8A%B9%E3%81%A7%E3%81%AF%E3%81%AA%E3%81%84?utm_source=twitterfeed&utm_medium=twitter) もあります  

## 2. CSS、JavaScript の読み込みの順番について

```html
<!DOCTYPE html>
<html lang="ja">
  <head>
    <!-- 中略 -->
    <link rel="stylesheet" type="text/css" href="./assets/css/reset.css">
    <link rel="stylesheet" type="text/css" href="https://cdn.jsdelivr.net/npm/slick-carousel@1.8.1/slick/slick.css">
    <link rel="stylesheet" type="text/css" href="./assets/css/style.css">
  </head>
  <body>
    <!-- 中略 -->
    <script src="https://code.jquery.com/jquery-3.6.0.min.js" integrity="sha256-/xUj+3OJU5yExlq6GSYGSHk7tPXikynS7ogEvDej/m4=" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/slick-carousel@1.8.1/slick/slick.min.js"></script>
    <script src="./assets/js/main.js"></script>
  </body>
</html>
```

上記は [slick.js](https://kenwheeler.github.io/slick/) を使った例です。

スタイルシートは

1. リセット系
2. jQuery ライブラリの CSS
3. 自身の記述した CSS

JavaScript は

1. jQuery 本体
2. jQuery ライブラリの `.js` ファイル
3. 自身の記述した `.js` ファイル

の順番で読み込むようにしましょう。  

CSS については変更したスタイルを jQuery ライブラリのスタイルに上書きされないようにするためです。  

JavaScript については jQuery やライブラリなどの命令が使われている場合、後から読み込んだ場合、エラーの原因となってしまうためです。  

## 3. `<script></script>` タグでなく、 `.js` ファイルに記述する

これは同じコードの再利用をしやすくし、メンテナンス性を高めるためです。  
ファイルを分けることにより、どこに書いてあるか分かりやすくなるというメリットもあります。  

詳しくは [控えめな JavaScript](https://www.google.com/search?q=%E6%8E%A7%E3%81%88%E3%82%81%E3%81%AAJavaScript&rlz=1C1GCEU_jaJP875JP875&sourceid=chrome&ie=UTF-8) で検索してみると解説の記事がたくさんでてきます。  

## 4. jQuery ライブラリ置き場所

jQuery のライブラリはトップフォルダなどに置かず、必ずなにがしかのフォルダにまとめておきましょう。  
このほうが管理がしやすくなり、ページを構成する資源を一元化できます。  

例えば **assets** フォルダがある場合はそちらの中に格納します。
他にも **js/lib** や **js/common** を作成しライブラリとわかるように格納する方法もあります。  

## その他参考文献について

- JavaScriptの読み込み位置をページ最後にしたほうがよい理由
  - [https://memocarilog.info/jquery/5842](https://memocarilog.info/jquery/5842)
- 控えめなJavaScript - wikipedia
  - [https://ja.wikipedia.org/wiki/%E6%8E%A7%E3%81%88%E3%82%81%E3%81%AAJavaScript](https://ja.wikipedia.org/wiki/%E6%8E%A7%E3%81%88%E3%82%81%E3%81%AAJavaScript)
