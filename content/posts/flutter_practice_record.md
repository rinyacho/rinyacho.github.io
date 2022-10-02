---
title: "Flutter Challenge!💥 練習編"
date: 2022-08-19T22:18:17+09:00
tags: ["Flutter"]
draft: false
---
## 参考にしている書籍やサイトなど
- [Flutter実践入門](https://zenn.dev/kazutxt/books/flutter_practice_introduction/viewer/chapter0) <!-- - [Flutter研修【ミクシィ22新卒技術研修】](https://www.youtube.com/watch?v=oQCJZFqDwIo&t=707s) -->
- [スマホで動くアプリを作ろう！ゼロから始めるFlutter実践入門編](https://www.amazon.co.jp/%E3%82%B9%E3%83%9E%E3%83%9B%E3%81%A7%E5%8B%95%E3%81%8F%E3%82%A2%E3%83%97%E3%83%AA%E3%82%92%E4%BD%9C%E3%82%8D%E3%81%86%EF%BC%81%E3%82%BC%E3%83%AD%E3%81%8B%E3%82%89%E5%A7%8B%E3%82%81%E3%82%8BFlutter%E5%AE%9F%E8%B7%B5%E5%85%A5%E9%96%80%E7%B7%A8-%E2%91%A0-%E3%82%B7%E3%83%B3%E3%83%97%E3%83%AB%E3%81%AA%E3%82%A2%E3%83%97%E3%83%AA%E3%82%92%E4%BD%9C%E3%81%A3%E3%81%A6%E3%81%BF%E3%82%88%E3%81%86-%E6%B8%8B%E8%B0%B7-%E3%82%A8%E3%83%9F%E3%83%AA-ebook/dp/B09VKXCFCN/ref=sr_1_3?__mk_ja_JP=%E3%82%AB%E3%82%BF%E3%82%AB%E3%83%8A&crid=TPW10PMXYQXG&keywords=flutter&qid=1662303959&sprefix=flutter%2Caps%2C199&sr=8-3) ※1~3含めて  
- [Flutter 日本語ドキュメント](https://flutter.ctrnost.com/)

## STEP1
- 開発機の選定。
- マウス・キーボードの設定。
- Homebrewのインストール。
- AndroidStudioのインストール。
- Gitのインストール。
- ローカル＆リモートリポジトリの設定。
- 教材の選定。

## STEP2
- 画像と文字を画面に表示するアプリを作成（写経＋アレンジ）。
- 意義：基本的な使い方を把握する。
- `assets/`を作成して画像をコピーしてくる。`yml`を書き換えて画像ファイルを認識させる。
- `Image()`で画像を表示。
- `Text()`で文字を表示。
- `body: Centor()`（全体配置）、`Column()`（縦配置）、`Row()`（横配置）でレイアウト。
- `MainAxisAlignment.`で配置パターンを設定。
- `child: []`と`children: []`で入れ子構造の設定。  

[リポジトリ：flutter_practice_display](https://github.com/watobii/flutter_practice_display)

## STEP3
- 名前と日付を入力することで、生まれてから現在までの日数を計算するアプリを作成（写経＋アレンジ）。
- 意義：async・awaitの処理に触れる。小技を覚える。画面遷移の手法やその書き方を身につける。
- `appbar:`で画面上端のバー＋テキストを表示。
- `String`と`DateTime`の型で変数生成。
- `InputDecoration()`でテキスト入力欄のデザイン設定。
- `print()`でconsoleに値を出力。デバッグでも有効。
- `Icon:`でアイコンを表示。
- `Padding()`で4方向のレイアウト調整。
- `SingleChildScrollView()`画面内に治まらない時のスクロールに対応。
- `if文`で`null`回避。`hoge!`にてnullで無いことの証明。
-  `TextField()`や`ShowDatePicker()`を使用して入力パターンを設定。
- `onPressed:`を使用してタップ動作の検知。
- `aysnc`と`await`を使用して動作に時間差があるデータの格納に対応（カレンダーを表示する→日付を選択する）。
- 新たなclassを作成。
- `lib/`に`.dart`ファイルを追加して、新たな画面を作成。
- 変数の作成、変数の画面間渡し。
- `Navigator.push()`と`MaterialPageRoute(builder: (context) =>)`を使用して`main.dart`から画面遷移。  

[リポジトリ：flutter_practice_calc](https://github.com/watobii/flutter_practice_calc)

## STEP4
- 本記事の初回作成。
- プロフィールを表示して、シェアするアプリを作成中（写経＋アレンジ）。
- 意義：パッケージの導入方法とその適用の勘所を身につける。例外処理、async・awaitの処理に慣れる。
- `url_launcher`パッケージのインストールと適用。
- `launchURL`でメールアプリの自動起動と適用するテキストを設定。
- `Future<void>`、`async`、`await`で時間がかかる処理の対応。
- `if` + `throw`で例外処理。
- `fontSize:`と`fontWeight:`で、文字の大きさと強さを変更できる。
- `share_plus`packageを導入して、シェア動作を入れる。
- `screenshot`packageを導入して、スクリーンショットを取る動作を入れる。
- `path_provider`packageを導入して、スクリーンショットのデータとのパスを繋ぐ。
- `backgroundColor:`で背景色を指定する。
- 下記のErrorが発生。SDKの紐づけが出来ていなかった（NoSDK）のが原因っぽい。File→Project Structureで、SDKを設定したところ、解消された。  
[参考サイト：Android Studioで作成したFlutterプロジェクトがGradleまわりのErrorを...](https://shn-hsn.hatenablog.com/entry/2020/01/02/162242)
```none
Cannot resolve symbol 'Properties'
Cannot resolve symbol 'Properties'
```
- 書くコードの量が多くなってきており、手間取った。また入れ子構造への理解が薄い、VScodeもまだ使い慣れているとは言い難いので、時間を要してしまう。  

[リポジトリ：flutter_practice_share](https://github.com/watobii/flutter_practice_share)  

## STEP5
- 新規作成したいアプリの画面イメージを描いてみる。 

## STEP6
- リアルタイムに値を変更して表示するアプリを作成（写経）。
- 画面を最初に生成した時の変数の値は保持される。ただし、TextField等の入力形式の内容を除く。
- `Provider`packageを導入して、TextFieldに入力された値を他の場所でリアルタイムに反映させる。
- `TextChanged`で、入力された文字に変更があった場合に動作させる。
- 上記に`notifyListeners()`を入れ、で変数が変わったことを他のファイルに知らせる。
- `ChangeNotifierProvider`で作成したKクラスを`Provider.of<Hoge>(context, listen:false).hoge`を使用して呼び出す。  
- `print()`は`+`演算子を間に入れると変数と文字列を同時に表示できる。
```dart
print('hogeの値：'+Hoge.hoge);   // 文字列＋変数の形
```

[リポジトリ：flutter_practice_realtime](https://github.com/watobii/flutter_practice_realtime/settings)

## STEP7
- 押した回数を記録し、リアルタイムで表示するアプリを作成（写経）。
- アプリを閉じても回数の記録は残る。
- `provider`packageを導入して、数字が変わったことを明示的に通知する。
- `MaterialApp()`と`scaffold()`が同じクラスにある場合、`provider`が機能しない。クラスを新規作成。
- `MaterialApp()`の宣言はアプリ毎に一回だけにし、初期設定の内容を記載する。その他の動作は別のクラスを作成する。
- 下記で関数を呼び出し、`notifyListeners`を実行する。カウントする（`+= 1`）。
```dart
Provider.of<クラス名>(context, listen: false).関数名;
```
- `notifyListeners`で数字が変わったことを通知する。
- 下記でカウントした値を指定する。`text()`と組み合わせてそれを表示。
```dart
Provider.of<クラス名>(context).変数名
```
- `Hive`packageを導入して、端末内にデータを保存する。
- 下記をターミナルで実行し、`g.dart`を生成する（Type Adapterの登録）。
```
flutter packages run build_ runner build
```
- この辺りの挙動や記述が分かりにくいので、折を見て調べていきたい。

[リポジトリ：flutter_practice_pressed](https://github.com/watobii/flutter_practice_pressed)

## 終わりに
練習自体はここまでにしようかなと思います。