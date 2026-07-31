---
title: Getting Started
description: Akarenga UNO R4 Minima の開発環境をセットアップし、LED を点滅させるまでの手順を説明します。
tags:
  - UNO R4 Minima
  - インストール
  - Arduino IDE
---

# Getting Started

Akarenga UNO R4 Minima を初めて使うときの手順です。Arduino IDE をインストールし、ボードパッケージを追加して、LED を点滅させるところまでを説明します。

ボードの概要は [Akarenga UNO R4 Minima](../../index.md) を参照してください。

## 必要なもの

- Akarenga UNO R4 Minima ボード
- USB Type-C ケーブル (データ通信に対応したもの。充電専用ケーブルでは書き込みできません)
- Arduino IDE 2.x が動作する PC (Windows / macOS / Linux)

## 1. Arduino IDE をインストールする

[Arduino 公式サイト](https://www.arduino.cc/en/software) から Arduino IDE 2.x をダウンロードしてインストールします。すでにインストール済みであればこの手順は不要です。

## 2. ボードマネージャの URL を追加する

Akarenga UNO R4 は Arduino 標準のボード一覧には含まれないため、専用のボードマネージャ URL を登録します。

1. Arduino IDE の設定画面を開く
      - Windows / Linux: **ファイル → 基本設定**
      - macOS: **Arduino IDE → Settings...**
2. **追加のボードマネージャの URL** に以下を追加する

```
https://akarenga-oshw.github.io/arduino-board-index/dev/package_akarenga_index.json
```

すでに他の URL が登録されている場合は、右端のアイコンから複数行のエディタを開き、改行して追加してください。

3. **OK** で設定を閉じる

## 3. ボードパッケージをインストールする

1. 左サイドバーの **ボードマネージャ** を開く (または **ツール → ボード → ボードマネージャ**)
2. 検索欄に `Akarenga` と入力する
3. **Akarenga UNO R4 Boards** の **インストール** をクリックする

インストールには数分かかることがあります。コンパイラやツールチェーンを含むため、初回は数百 MB のダウンロードが発生します。

## 4. ボードとポートを選択する

1. ボードを USB ケーブルで PC に接続する
2. **ツール → ボード → Akarenga UNO R4 Boards → Akarenga UNO R4** を選択する
3. **ツール → シリアルポート** から、ボードが接続されているポートを選択する

> **TODO:** ポート名の例を OS ごとに記載する (Windows: `COM3` など / macOS: `/dev/cu.usbmodem...` / Linux: `/dev/ttyACM0`)。ボードの USB VID/PID が Arduino 純正と同じかどうかも確認して追記する。

## 5. 動作確認 (Blink)

書き込みが正しく行えるかを、内蔵 LED を点滅させるスケッチで確認します。

1. **ファイル → スケッチ例 → 01.Basics → Blink** を開く
2. ツールバーの **→ (書き込み)** ボタンをクリックする
3. コンパイルと書き込みが完了すると、ボード上の LED が 1 秒間隔で点滅する

点滅を確認できれば、開発環境のセットアップは完了です。

## うまくいかないときは

**シリアルポートが表示されない**

- USB ケーブルが充電専用でないか確認してください。データ通信対応のケーブルが必要です
- 別の USB ポートやケーブルで試してください
- ボードを接続し直してから、Arduino IDE のポート一覧を開き直してください

**書き込みに失敗する**

- ボードの選択が **Akarenga UNO R4** になっているか確認してください
- 他のアプリケーション (シリアルモニタなど) がポートを使用していないか確認してください

> **TODO:** ブートローダーモードへの入り方 (リセットボタンの操作) を確認して追記する。

**ボードマネージャに Akarenga が出てこない**

- 手順 2 の URL が正しく登録されているか確認してください
- ボードマネージャの再読み込み、または Arduino IDE の再起動を試してください
