# プロジェクト設定: Claude Code Sample Game

## プロジェクト概要

- **種別**: Unity ゲーム開発
- **言語**: C# (.NET Standard 2.1)
- **エンジン**: Unity 2022.3 LTS
- **プラットフォーム**: Windows

## ディレクトリ構造

- `Assets/Scripts/` - C#スクリプト (MonoBehaviour, ScriptableObject など)
- `Assets/Scenes/` - Unityシーンファイル (.unity)
- `Assets/Prefabs/` - プレハブ (.prefab)
- `Assets/Materials/` - マテリアル (.mat)
- `Assets/Textures/` - テクスチャ画像 (.png, .jpg)
- `Assets/Audio/` - 音声ファイル (.wav, .mp3, .ogg)
- `Assets/Resources/` - Resources.Load()で動的にロードするアセット
- `Packages/manifest.json` - Unityパッケージ依存関係
- `ProjectSettings/` - Unityプロジェクト設定

## C# コーディングルール

### 命名規則
- クラス名・メソッド名: PascalCase (例: `PlayerController`, `TakeDamage()`)
- ローカル変数・引数: camelCase (例: `moveSpeed`, `targetPosition`)
- プライベートフィールド: _camelCase (例: `_rigidbody`, `_health`)
- 定数: UPPER_SNAKE_CASE (例: `MAX_HEALTH`, `DEFAULT_SPEED`)
- インターフェース: I + PascalCase (例: `IDamageable`, `IInteractable`)

### Unity固有のルール
- MonoBehaviourを継承するクラスは1ファイル1クラス
- [SerializeField] を使ってインスペクターに公開 (publicフィールドは避ける)
- GetComponent<T>() の呼び出しはAwake()またはStart()でキャッシュする
- Update()内でのアロケーション(new, LINQ等)を避ける
- コルーチン(Coroutine)よりasync/awaitを優先的に検討する

### コメント
- コメントは日本語で記述
- XMLドキュメントコメント(///)でpublicメンバーを説明する
- 複雑なロジックには「なぜそうするのか」を書く

### ファイル構成
- 1つのC#ファイルに1つのクラス (内部クラスは例外)
- ファイル名はクラス名と一致させる
- 機能ごとにサブフォルダで整理 (例: Scripts/Player/, Scripts/Enemy/)

## 禁止事項
- .meta ファイルを手動で編集しない
- Library/, Temp/, obj/ 以下のファイルをGitにコミットしない
- Resources/ フォルダの乱用 (ビルドサイズが肥大化するため)
- FindObjectOfType<T>() の多用 (パフォーマンスに悪影響)

## テスト
- Unity Test Framework (NUnit ベース) を使用
- テストスクリプトは `Assets/Tests/` に配置
- EditMode テストと PlayMode テストを分離する

## 作業ログ運用
- **重要: 作業完了時に必ず `.claude/WORK_LOG.md` を更新すること**
- フォーマット:
  ```
  ## YYYY-MM-DD

  ### HH:MM - 作業タイトル
  - 実施した内容1
  - 実施した内容2
  ```
- 新しい作業は常にファイルの末尾（テンプレートコメントの前）に追記
- 記録すべき内容:
  - ファイル作成・変更
  - 機能追加・バグ修正
  - Gitコミット
  - ディレクトリ構造変更
  - 重要な決定事項
