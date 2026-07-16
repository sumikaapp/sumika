# Smart Speaker — ダウンロード / 配布リポジトリ

ローカル動作型の音声アシスタント「Smart Speaker（AIコンシェルジュ）」の
**配布専用リポジトリ**です。アプリ本体のダウンロードはこちらの
[Releases](../../releases) から行ってください。

ウェイクワード検出 → 音声認識（Whisper）→ 応答生成（Ollama）→
音声合成（VOICEVOX）がすべて PC 内で完結します。クラウドに音声を送りません。

## ダウンロード

[Releases ページ](../../releases/latest) から環境に合わせて選択してください。

| ファイル | 形式 | 対象 |
|---------|------|------|
| `smart_speaker_*_cpu_x64-setup.exe` | インストーラー（推奨） | すべての Windows PC |
| `smart_speaker_*_cuda_x64-setup.exe` | インストーラー | NVIDIA GPU 搭載 PC（高速動作） |
| `smart_speaker-*-windows-cpu_portable.7z` | ポータブル版 | インストール不要で使いたい方 |
| `smart_speaker-*-windows-cuda_portable.7z` | ポータブル版 | 同上（NVIDIA GPU 向け） |

`latest-cpu.json` / `latest-cuda.json` はアプリの自動アップデート用ファイルです
（手動ダウンロード不要）。

## 動作要件

- Windows 10 / 11（64bit）
- マイクとスピーカー
- CUDA 版のみ: NVIDIA GPU + NVIDIA ドライバー 570.x 以上
- 外部コンポーネント（初回セットアップで導入）:
  - [Ollama](https://ollama.com/) — 応答生成（LLM）
  - [VOICEVOX](https://voicevox.hiroshiba.jp/) — 音声合成
  - Whisper モデル — 初回起動時に自動ダウンロード（約 0.1〜3GB、選択可）

## セットアップ（ポータブル版）

1. 7z を任意の場所（ユーザーフォルダ配下推奨）に展開
2. `setup.bat` を実行 — Ollama の自動インストールとモデル取得、VOICEVOX の案内
3. VOICEVOX をインストール
4. `START-Smart-Speaker.vbs` で起動（コンソール非表示のバックグラウンド起動）

インストーラー版はウィザードに従ってインストール後、スタートメニューから起動できます。

## トラブルシューティング（抜粋）

| 症状 | 対処 |
|------|------|
| CUDA 版で `cudart64_12.dll not found` | CUDA Toolkit 12.x をインストールして PC を再起動、または CPU 版を使用 |
| 応答が生成されない | Ollama が起動しているか確認（`ollama serve`） |
| 声が出ない | VOICEVOX が起動しているか確認（http://localhost:50021） |
| 音声認識が遅い | 小さめの Whisper モデル（small / base）へ設定変更 |

## ライセンス・クレジット

- アプリ本体: MIT License（同梱の LICENSE を参照）
- 音声合成は各エンジンの利用規約に従います。既定キャラクターの音声は
  `VOICEVOX:四国めたん` 等のクレジット表記が必要です（アプリ内に常時表示されます）。

## 不具合報告

このリポジトリの [Issues](../../issues) へお願いします。
