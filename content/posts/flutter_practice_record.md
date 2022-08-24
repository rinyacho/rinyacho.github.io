---
title: "Flutter Challenge!💥 練習編（更新中）"
date: 2022-08-19T22:18:17+09:00
tags: ["Flutter"]
draft: false
---
## Day1
- 開発機の選定。
- マウス・キーボードの設定。
- Homebrewのインストール。
- AndroidStudioのインストール。
- Gitのインストール。
- ローカル＆リモートリポジトリの設定。

## Day2
- 画像と文字を画面に表示するアプリを作成（写経＋アレンジ）。
- `assets/`を作成して画像をコピーしてくる。`yml`を書き換えて画像ファイルを認識させる。
- `Image()`で画像を表示。
- `Text()`で文字を表示。
- `body: Centor()`（全体配置）、`Column()`（縦配置）、`Row()`（横配置）でレイアウト。
- `MainAxisAlignment.`で配置パターンを設定。
- `child: []`と`children: []`で入れ子構造の設定。  
[リポジトリ：flutter_practice_display](https://github.com/watobii/flutter_practice_display)

## Day3
- 名前と日付を入力することで、生まれてから現在までの日数を計算するアプリを作成（写経＋アレンジ）。
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
- `Navigator.push()`と`MaterialPageRoute(builder: (context) =>)`を使用して`main.dart`から画面遷移。  
[リポジトリ：flutter_practice_calc](https://github.com/watobii/flutter_practice_calc)

## Day4・5・6・7・8
- 本記事の初回作成。
- プロフィールを表示して、シェアするアプリを作成中。
- `url_launcher`パッケージのインストールと適用。
- `launchURL`でメールアプリの自動起動と適用するテキストを設定。
- `Future<void>`、`async`、`await`で時間がかかる処理の対応。
- `if` + `throw`で例外処理。
- `share_plus`packageを導入して、シェア動作を入れる。
- `screenshot`packageを導入して、スクリーンショットを取る動作を入れる。
- `path_provider`packageを導入して、スクリーンショットのデータとのパスを繋ぐ。
- `backgroundColor:`で背景色を指定する。  
[リポジトリ：flutter_practice_share](https://github.com/watobii/flutter_practice_share)


## 継続中の問題
- バーチャルiPhone機との接続ができず、アプリが立ち上げられない。Andoroid機は問題無し。
- 時間の確保が困難😥　少しずつでも、出来るだけ毎日進めていきたい。
- main.dartとは異なる部分でErrorが発生中。原因調査中。