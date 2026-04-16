# Kotoba-Jot

日本語特化の音声認識モデル [kotoba-whisper-v2.0](https://huggingface.co/kotoba-tech/kotoba-whisper-v2.0-faster) を使った、グローバルホットキーで呼び出せる日本語音声入力デスクトップアプリ。Windows / macOS 対応。

![Version](https://img.shields.io/github/v/release/nappa0326/kotoba-jot-releases?label=version)
![Platforms](https://img.shields.io/badge/platforms-Windows%20%7C%20macOS-lightgrey)
![Downloads](https://img.shields.io/github/downloads/nappa0326/kotoba-jot-releases/total)

## 特徴

- **Push-to-talk 音声入力**: ホットキーを長押しして話し、離すと文字起こし → アクティブウィンドウへ自動でテキスト注入
- **日本語特化の高精度**: kotoba-whisper-v2.0 による日本語認識
- **常駐型**: システムトレイに常駐、必要な時だけ呼び出せる
- **マルチディスプレイ対応**: カーソルのあるモニターに録音状態オーバーレイを表示
- **GPU 推論 (CUDA)**: Windows の NVIDIA GPU で高速化。失敗時は CPU に自動フォールバック
- **無音区切り逐次出力**: 話している途中でも、区切りごとに文字起こし結果を順次注入
- **後処理辞書**: 誤認識しがちな固有名詞などを自動で置換
- **ホットキー設定**: Discord 風キー記録 UI で好きなコンビネーションに変更可能
- **自動更新**: 新バージョンのダウンロード・インストール・再起動まで自動化

## 動作環境

### Windows

- Windows 10 以降（x86_64）
- CUDA 対応の NVIDIA GPU（任意、あると高速）

### macOS

- macOS 11 Big Sur 以降
- Apple Silicon (aarch64) / Intel (x86_64) 両対応
- **Accessibility 権限** が必要（ホットキー監視とテキスト注入のため）
- **マイクアクセス権限** が必要

## ダウンロード

**[最新リリースをダウンロード](https://github.com/nappa0326/kotoba-jot-releases/releases/latest)**

| OS | ファイル |
|---|---|
| Windows | `Kotoba-Jot_x.x.x_x64-setup.exe` |
| macOS (Apple Silicon) | `Kotoba-Jot_x.x.x_aarch64.dmg` |
| macOS (Intel) | `Kotoba-Jot_x.x.x_x64.dmg` |

> Apple Developer ID で署名・Notarization 済みです。通常は Gatekeeper 警告なしで起動できます。

## インストール

### Windows

1. Releases ページから `.exe` インストーラーをダウンロード
2. ダウンロードした `.exe` を実行
3. インストーラーの指示に従ってインストール

### macOS

1. Releases ページから `.dmg` をダウンロード
2. DMG を開き、アプリケーションフォルダにドラッグ
3. 初回起動時に以下の権限を付与:
   - システム設定 → プライバシーとセキュリティ → **アクセシビリティ** → Kotoba-Jot を有効化
   - マイクアクセスのダイアログで「許可」を選択

初回起動時に音声認識モデル（約 1.5GB）を自動ダウンロードします。

## 使い方

1. アプリを起動するとシステムトレイに常駐します
2. 入力したいウィンドウにフォーカスを合わせる
3. ホットキーを **長押し** して話す
4. キーを離すと文字起こしが実行され、アクティブウィンドウにテキストが注入される

### デフォルトのホットキー

| OS | ホットキー |
|---|---|
| Windows | `Ctrl + Win` |
| macOS | `Cmd + Ctrl` |

メインウィンドウの設定画面から好きなキーに変更できます。

録音中はカーソル位置のモニターに小さなオーバーレイ（マイクレベルバー）が表示されます。変換中はスピナーに変わります。

## 設定

トレイアイコンをクリックするとメインウィンドウが開き、以下が設定できます:

- **ホットキー**: Discord 風のキー記録 UI でカスタマイズ
- **GPU (CUDA) 使用**: Windows のみ、NVIDIA GPU がある場合に有効化
- **無音区切り逐次出力**: 長文を話す場合に順次注入するモード
- **辞書**: 誤認識しがちな語句を登録すると自動置換される。発言履歴のテキストを選択してポップアップから直接登録も可能
- **OS 自動起動**: ログイン時の自動起動を切り替え

## トラブルシューティング

### Windows: ホットキー使用時にシステム UI が開くことがある

`Ctrl+Win` は Windows Shell のショートカットと競合することがあります。気になる場合は設定画面からホットキーを `Ctrl+Alt` などに変更してください。

### macOS: ホットキーが反応しない

Accessibility 権限が付与されていない可能性があります。システム設定 → プライバシーとセキュリティ → アクセシビリティで Kotoba-Jot が有効になっているか確認してください。

### macOS: 「開発元を検証できません」と表示される

Notarization 済みですが、ネットワーク状態等により稀に表示されることがあります。システム設定 → プライバシーとセキュリティ → 「このまま開く」を選択してください。

## 更新履歴

各バージョンの変更内容は [Releases ページ](https://github.com/nappa0326/kotoba-jot-releases/releases) を参照してください。

## リンク

- **配布ページ**: https://github.com/nappa0326/kotoba-jot-releases/releases
- **音声認識モデル**: https://huggingface.co/kotoba-tech/kotoba-whisper-v2.0-faster
