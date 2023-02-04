---
layout: post
title: Visual Studio Code - Live Share
author: Webトレーナー S.Yabu
tags:
  - vscode
  - extension
  - coding
---

いろいろな機能を追加して、自分の好みの環境にできる Visual Studio Code (以下 VS Code) ですが自分の作業環境をそのまま相手に見せることができる機能があることをご存知ですか ?  

今回は共同で作業をする際や、遠隔でのコードレビューに便利な拡張機能 **Live Share** を紹介します。  

<!--more-->

## Live Share とは

Live Share は VS Code の開発元である Microsoft が提供している、作業状態を共有するための VS Code の拡張機能の一つです。  

導入しいくつかの設定をするだけで、遠隔の人に自分の作業環境を共有して共同で作業をしたり、コードを見てもらうことが可能になります。  

利用には Github か Microsoft のアカウントが必要となります。  

### Visual Studio Marketplace の Live Share の ページ

[https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare)

## 導入方法と使い方

※ VS Code をインストールしてあることを前提として解説します。  

### 1. Github アカウントを用意する

まずは Github か Microsoft のアカウントを作成しましょう。  
取り回しの良さを考えるのであれば、 Github アカウントのほうが手軽に用意できます。  

![""]({{ site.repository }}/assets/images/2023/02/04_vscode-liveshare/img001.png)

必要になるのは以下の 3 つです。  

- ユーザ名 (半角英数)
- メールアドレス
- パスワード

### 2. VS Code で Live Share をインストールする

次に VS Code で Live Share の拡張機能をインストールします。  
手順は以下の通りです。  

![""]({{ site.repository }}/assets/images/2023/02/04_vscode-liveshare/img002.png)

1. VS Code の拡張機能のタブを開きます。
2. 検索ワードの `Live Share` を入力します。
3. 候補の中にでてきた Live Share を選択します。
4. インストールボタンをクリックします。  

以上で導入は完了です。  
インストールが終わったら最後の設定をしていきます。  

### 3. Github のアカウントに VS Code でログインする

Live Share のインストールが終わったら画面の左下に画像のようなボタンが現れているはずです。  
※もし見当たらない場合は VS Code を一度終了して立ち上げ直してみてください。  

![""]({{ site.repository }}/assets/images/2023/02/04_vscode-liveshare/img003.png)

ボタンを押してみると次のように案内が出ます。  

![""]({{ site.repository }}/assets/images/2023/02/04_vscode-liveshare/img004.png)

こちらは **Github** を選択すれば OK です。  
あとはブラウザが開いて Github にログインしたあと、再び VS Code に戻ってくるのでその間に出てくるメッセージに許可を与えてください。  

ここまでできたら画面左下のボタンが次の画像のように変わっているはずです。  

![""]({{ site.repository }}/assets/images/2023/02/04_vscode-liveshare/img005.png)

### 4. 共有を開始する

ここまでできたら共有の準備は OK です。
ボタンが **Shared** に変わったときに共有用の URL が発行されるので、それを共同作業をする人に教えてあげてください。  

![""]({{ site.repository }}/assets/images/2023/02/04_vscode-liveshare/img006.png)

それから共有を開始したときに画像のようなメッセージが出てきています。  

こちらは共有用のリンクをコピーしましたよ ! というメッセージです。  
またこの **Make read-only** のボタンを押せば、見せるだけのモードで共有をすることもできます。  

### 5. 誰かが共有に入ってきた場合の画面

共有したリンクから誰かが入ってきたとき、以下のようなメッセージがでてきます。  

![""]({{ site.repository }}/assets/images/2023/02/04_vscode-liveshare/img007.png)

これは Guest User (2) さんが共有に入ってきました、どうしますか。というメッセージです。  

**Accept read-only** を選んだ場合は、その人はコードを見ることだけできるようになります。  
**Accept read-write** を選んだ場合は、その人はコードを見ることと、変更を加えることができるようになります。  
**Reject** を選んだ場合は、その人への共有の拒否になります。  

名前をよく確認して適切に共有の権限を選択しましょう。  

### 6. 誰かの共有に入る場合の画面

逆に共有されたリンクに入った場合はどうなるのかも見てみましょう。  

まずリンクにアクセスすると [https://vscode.dev/](https://vscode.dev/) というサイトが開きます。  
これは Web 上で VS Code が利用できるサービスです。  

そして上記のようなウィンドウが表示されます。  

![""]({{ site.repository }}/assets/images/2023/02/04_vscode-liveshare/img008.png)

これはこのまま Web 上で閲覧をするか、それともインストールされている VS Code でコードを開くかの選択画面になります。  

Web で見る場合は **Continue in Web** を、VS Code で開く場合は **Open in Visual Studio Code** を選択しましょう。  

![""]({{ site.repository }}/assets/images/2023/02/04_vscode-liveshare/img009.png)

こちらはゲストとして共有に入る (**Continue as anonymous**) か、 Github アカウントにログインして共有に入る (**Sign in**) かの選択になります。  
特に何もなければゲストとして共有に入るで問題ないです。  

![""]({{ site.repository }}/assets/images/2023/02/04_vscode-liveshare/img010.png)

ゲストで入る場合は、名前の入力を求められます。  
こちら名前の入力をして `Enter` キーを押してください。

あとは共有をする側の人が認証をしてくれればコードの共有が開始されます。  

### 7. 共有を終了する

共有を終了したいときは画面左下の **Shared** ボタンを押してください。  
すると次のようなメニューが表示されます。  

![""]({{ site.repository }}/assets/images/2023/02/04_vscode-liveshare/img011.png)

このメニューの一番下にある **Stop Collaboration Session** をクリックすれば共有が停止します。  

## まとめ

ざっくりと Live Share での共有の始め方や共有への入り方などをいろいろ見て来ましたがいかがだったでしょうか。  

この他にもチャット機能など、共同作業に便利な機能も Live Share は備えているので、興味があればいろいろな使い方を調べてみてみましょう。  

## 参考になりそうなサイトへのリンク

- Visual Studio Live Share とは (Microsoft 公式)
  - [https://learn.microsoft.com/ja-jp/visualstudio/liveshare/use/install-live-share-visual-studio-code](https://learn.microsoft.com/ja-jp/visualstudio/liveshare/use/install-live-share-visual-studio-code)
- VSCode Live Share の使い方をしっかり知る
  - [https://qiita.com/irico/items/b67328fdaa2d9a306cba](https://qiita.com/irico/items/b67328fdaa2d9a306cba)
