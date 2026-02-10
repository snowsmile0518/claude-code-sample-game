# Claude Code Sample Game

## 概要

Unity(C#)で開発するサンプルゲームプロジェクトです。

## 開発環境

| 項目 | バージョン |
|------|-----------|
| Unity | 2022.3 LTS (推奨) |
| IDE | Visual Studio 2022 / VS Code / Rider |
| .NET | Unity標準の .NET Standard 2.1 |
| OS | Windows 10/11 |

## セットアップ手順

1. Unity Hub をインストール
2. Unity 2022.3 LTS をインストール
3. このリポジトリをクローン
4. Unity Hub から「Open」でプロジェクトフォルダを指定
5. 初回起動時に Library/ 等が自動生成されます (数分かかる場合があります)

## ディレクトリ構成

```
Assets/
├── Scripts/      # C#スクリプト
├── Scenes/       # シーンファイル
├── Prefabs/      # プレハブ
├── Materials/    # マテリアル
├── Textures/     # テクスチャ
├── Audio/        # 音声ファイル
└── Resources/    # 動的ロード用アセット
```

## コーディング規約

- 命名規則: PascalCase (クラス/メソッド), camelCase (ローカル変数)
- コメント: 日本語で記述
- 詳細は `.claude/CLAUDE.md` を参照
