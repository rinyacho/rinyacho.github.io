---
title: "Hugo + GitHubPagesを使用してブログ&プロフィールサイトを表示するまでのError一覧など"
date: 2022-08-09T17:04:49+09:00
tags: ["技術"]
draft: false
---
## なぜGitHubPagesを選んだのか
無料であり、広告がないのが魅力的でした。はてなブログやZennも検討しましたが、GitHubを使用した経験が乏しいので、練習も兼ねることが出来るのではと考えました。またGitHubを使い慣れておくとは、スキル💪として有用だとも考えていました。  
※記事をMarkdownで書くことは必須事項でしたが、どのサイトもその要件は満たしていました。
## 静的サイトジェネレーターになぜHugoを選んだのか
GitHubPagesを使用していく上で候補に挙がったのが、jekyllとHugoでした。jekyllはビルドに時間が遅い等の問題が見受けられました。調べるとjekyllからHugoに切り替えたというサイトもちらほらあり、かつ開発の継続性も見受けられましたので、Hugo（＋PaperMod）を選択しました。  
※ただ、jekyllはGitHub推奨の静的サイトジェネレーターの様ですし、最初はそこから入っても良かったかもしれません。  
## 参考にしたところ
- [GitHub Pagesで作るウェブサイト開発入門 - 自分だけのホームページを無料で公開](https://www.amazon.co.jp/GitHub-Pages%E3%81%A7%E4%BD%9C%E3%82%8B%E3%82%A6%E3%82%A7%E3%83%96%E3%82%B5%E3%82%A4%E3%83%88%E9%96%8B%E7%99%BA%E5%85%A5%E9%96%80-%E8%87%AA%E5%88%86%E3%81%A0%E3%81%91%E3%81%AE%E3%83%9B%E3%83%BC%E3%83%A0%E3%83%9A%E3%83%BC%E3%82%B8%E3%82%92%E7%84%A1%E6%96%99%E3%81%A7%E5%85%AC%E9%96%8B-%E3%83%8A%E3%82%AB%E3%83%8E%E3%83%92%E3%83%88%E3%82%B7-ebook/dp/B07FJNT3FS/ref=sr_1_2?__mk_ja_JP=%E3%82%AB%E3%82%BF%E3%82%AB%E3%83%8A&crid=14XX5DIQLN6GW&keywords=hugo+github+pages&qid=1660039652&sprefix=hugo+githubpage%2Caps%2C174&sr=8-2)
- [Hugo+Github Pagesでプロフィールページを作ってみた](https://zenn.dev/okaponta/articles/c302f58507febc)
## 受難の日々（Error一覧）😥
- configが従来生成された`config.toml`ではなく、`config.yml`を作る必要があった。これは選んだテーマにより違う部分の様なので、テーマの公式ドキュメントに書いてある内容だと思います。`config.yml`の書き方もなかなか掴めず苦労しました。最終的には下記の公式ページにたどり着き、何とか事なきを得ました。  
[hugo-PaperMod installation sample config.yml](https://github.com/adityatelange/hugo-PaperMod/wiki/Installation#sample-configyml)
- `hugo server`で生成したサイトがうまく表示できませんでした。http://localhost:1313/ にアクセスしても、Chromeが「このサイトにアクセスできません」と無情に表示するだけでした。しばらく生成された文章を眺めていると、`hugo server`が実行されている間しかlocalのWebサーバーは有効にならない、と気付きました。生成が終わったから実行を止めないといけないと勘違いしており、生成する度にctrl+cで止めてからアクセスしちゃってました。そりゃ表示されないですよね。
```none
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```
**Press Ctrl+C to stop!!**
- `git clone`で取得したPaperModがhttp://localhost:1313/ の段階で動きませんでした。いくつか同様の事例を調べていると、`git submodule`で導入している人が多かったので、実行してみたらうまくいきました（cloneしてきたフォルダは削除）。これは今のところ何が悪かったのか分かっていません。
- 上記の件と関連してURLやパスが異なるといったErrorが出ました（なぜかcloneで持ってきたフォルダは「PaperMod」、submoduleで持ってきたフォルダは「hugo-PaperMod」でした）。GitHub ActionsにこのURLやパスは存在しませんというErrorが出ており、気づきました。自分が誤った修正をしている場面もあり、なかなかErrorが治まりませんでした。
- `git init`の実行したパスが自分の想定と異なっており、GitHub上に上がるのが上位階層のフォルダ１つのみという状況が続きました。GitHub Actionsから`Docs`フォルダが見つかりませんというError内容が出ており気づきました。結局は、正しい位置で`Git init`を実行し直した上でadd → commit → pushの一連の流れを行うとうまくいきました。まだGit、GitHubの操作に慣れておらず、随分と右往左往しました。
- Repositoryの名前が不適切になっており、想定外のURLでGitHubPagesが公開されていました。それに伴い、baseurlが異なるのでサイト自体が全く表示されませんでした。Repositoryの名前を「github.io」にしていたのですが、「github.io」単体はURLとして指定出来ないことが分かり、「ユーザー名.github.io」に切り替えたところサイトを表示することが出来ました。
- `autocrlf`の関係からCSSが適用されませんでした。上記までの問題が解決された段階でGitHubPagesとしてこのサイトに問題なくアクセスすることが出来る状態でした。しかし、どう見てもCSSが適用されていない状態でした（htmlは表示されている）。Chromeで「ページの検証」を進めていると、CSSの部分で下記の様なErrorが起きていることが分かりました。Error内容で調べを進めると、Windowsでビルドを行うと改行コード（LF、CRLF）の関係から同様のErrorが出る場合があることが分かりました。  
[Hugoのtitle変更方法（CSSが反映されない理由）](https://snyt45.com/exJPd8zRS)  
```none
Failed to find a valid digest in the 'integrity' attribute for resource
```
`git config -l`でcore.autocrlfがtrueとなっていることを確認し、それを`git config --global core.autocrlf true`でfalseに変えてから`hugo`を実行しました。結果、Errorは解消され、何とかcssが適用された本サイトを拝むことが出来ました。最終的にこのErrorが一番時間を食いました。パッと見はパスのErrorかと思うので、パスを見直したりしていたのですが、全く問題は解決されず、キツかったです。尚、MacやLinux上でビルドすれば同様の問題は起こらない様です。  
[気をつけて！Git for Windowsにおける改行コード](https://qiita.com/uggds/items/00a1974ec4f115616580)
## 思ったこと
ビルドの段階でErrorを吐いてくれた方がまだマシなことに気づかされました。Error出てないのにうまく表示されない状態がキツかったです（GitHUb上のErrorに気づくのには時間を要しました）。 早く公式ドキュメントを読めるようにならないといけないですね。 
先見の知恵にとても助けられました。`autocrlf`のErrorとか、自分だけでは確実に見つけることが出来なかったと思います。知見とまとめて下さっている皆様、ありがとうございます😍
## 不明なこと
- ターミナルでcommitしても、VSCode上のcommitが必要な旨の表示が消えない。
- 上記の`autocrlf`のErrorを解決した後でも、htmlがクソ長一行で生成されてしまう。
## 今後
このサイト自体、もっとコンテンツを増やしていきたいと思っています。というか、今の状態だと本当に「表示した」だけって感じです。記事を増やす、プロフィールページを追加する、タグを追加する等々、今後も開発を進めて行きたいと思います😁