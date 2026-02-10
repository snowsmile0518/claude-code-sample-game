# 実装計画: Unity(C#)ゲーム開発プロジェクト ディレクトリ構造

## 概要

Windows環境でUnity(C#)ゲーム開発を開始するための、標準的かつ最小限のディレクトリ構造を構築します。Unityが自動生成するファイル群と、開発者が管理すべきファイル群を明確に分離し、Git管理とClaude Code連携の基盤を整えます。

## 前提知識

- Unityプロジェクトは通常 **Unity Hub** または **Unity Editor** から新規作成しますが、今回は「ディレクトリ構造の雛形」を手動で準備します
- Unity Editorで初回オープンすると `Library/`, `Logs/`, `Temp/`, `obj/` などが**自動生成**されるため、これらはGitに含めません
- `.meta` ファイルはUnityがアセット管理に使う重要なファイルで、**Gitに含める必要があります**

## 最終的なディレクトリ構造

```
d:\dev\claude-code-sample-game\
│
├── .claude/
│   ├── CLAUDE.md                    # プロジェクト固有のClaude Code設定
│   └── PLAN.md                      # 本ファイル：実装計画
│
├── .gitignore                       # Unity向けGit除外設定
├── README.md                        # プロジェクト説明
├── claude-code-sample-game.code-workspace  # (既存) VS Code ワークスペース
│
├── Assets/                          # ★ Unityのメインアセットフォルダ
│   ├── Scripts/                     # C#スクリプト
│   │   └── .gitkeep
│   ├── Scenes/                      # シーンファイル (.unity)
│   │   └── .gitkeep
│   ├── Prefabs/                     # プレハブ
│   │   └── .gitkeep
│   ├── Materials/                   # マテリアル
│   │   └── .gitkeep
│   ├── Textures/                    # テクスチャ画像
│   │   └── .gitkeep
│   ├── Audio/                       # 音声ファイル
│   │   └── .gitkeep
│   └── Resources/                   # Resourcesフォルダ (動的ロード用)
│       └── .gitkeep
│
├── Packages/
│   └── manifest.json                # Unityパッケージ依存関係
│
└── ProjectSettings/
    └── .gitkeep                     # Unity Editor初回起動時に自動生成
```

## 実装手順

### Phase 1: Git基盤 (最優先)

#### Step 1. `.gitignore` の作成

**ファイル:** `d:\dev\claude-code-sample-game\.gitignore`

**理由:** 最初にGit管理対象を定義しないと、Unity Editorで開いた瞬間に大量の自動生成ファイルがGit追跡対象になってしまうため

**リスク:** 低

---

#### Step 2. `README.md` の作成

**ファイル:** `d:\dev\claude-code-sample-game\README.md`

**理由:** プロジェクトの概要と開発環境のセットアップ手順を記録するため

**リスク:** 低

---

### Phase 2: Claude Code設定

#### Step 3. `.claude/CLAUDE.md` の作成

**ファイル:** `d:\dev\claude-code-sample-game\.claude\CLAUDE.md`

**理由:** Claude Codeがこのプロジェクトのコンテキスト(Unity/C#)を正しく理解するための設定ファイル

**リスク:** 低

---

### Phase 3: Unityプロジェクト構造

#### Step 4. `Assets/` サブディレクトリの作成

**対象ディレクトリ:**
- `Assets/Scripts/.gitkeep`
- `Assets/Scenes/.gitkeep`
- `Assets/Prefabs/.gitkeep`
- `Assets/Materials/.gitkeep`
- `Assets/Textures/.gitkeep`
- `Assets/Audio/.gitkeep`
- `Assets/Resources/.gitkeep`

**理由:** Gitは空ディレクトリを追跡できないため、`.gitkeep` を置いてディレクトリ構造を維持します。Unity Editorで初回オープン時に各ディレクトリの `.meta` が自動生成されます。

**リスク:** 低

---

#### Step 5. `Packages/manifest.json` の作成

**ファイル:** `d:\dev\claude-code-sample-game\Packages\manifest.json`

**理由:** Unityが依存パッケージを解決するために必須のファイル。Unity Editorで開く前にこのファイルが存在しないとエラーになる場合があります。

**リスク:** 中 (Unityバージョンとの互換性を確認する必要あり)

**補足:** これは Unity 2022.3 LTS の標準的な依存関係です。Unity Editorで新規プロジェクトを作成した場合のデフォルトに近い構成です。実際にUnity Editorで開くとバージョンが自動調整される場合があります。

---

#### Step 6. `ProjectSettings/.gitkeep` の作成

**ファイル:** `d:\dev\claude-code-sample-game\ProjectSettings\.gitkeep`

**理由:** `ProjectSettings.asset` などの実ファイルは**Unity Editorの初回起動に自動生成を任せる**ため、空ディレクトリ維持のために `.gitkeep` のみ配置します。手動作成はフォーマット不整合のリスクがあるためです。

**リスク:** 低

---

### Phase 4: 確認と初期化

#### Step 7. Git リポジトリの初期化

**コマンド:**
```bash
cd d:\dev\claude-code-sample-game
git init
git add .
git commit -m "Initial commit: Unity project structure setup"
```

**リスク:** 低

---

## 作成ファイル一覧 (まとめ)

| # | ファイルパス | 種別 |
|---|-------------|------|
| 1 | `.gitignore` | 新規作成 |
| 2 | `README.md` | 新規作成 |
| 3 | `.claude/PLAN.md` | 新規作成（本ファイル） |
| 4 | `.claude/CLAUDE.md` | 新規作成 |
| 5 | `Assets/Scripts/.gitkeep` | 新規作成 |
| 6 | `Assets/Scenes/.gitkeep` | 新規作成 |
| 7 | `Assets/Prefabs/.gitkeep` | 新規作成 |
| 8 | `Assets/Materials/.gitkeep` | 新規作成 |
| 9 | `Assets/Textures/.gitkeep` | 新規作成 |
| 10 | `Assets/Audio/.gitkeep` | 新規作成 |
| 11 | `Assets/Resources/.gitkeep` | 新規作成 |
| 12 | `Packages/manifest.json` | 新規作成 |
| 13 | `ProjectSettings/.gitkeep` | 新規作成 |

## リスクと対策

| リスク | 影響度 | 対策 |
|--------|--------|------|
| `manifest.json` のパッケージバージョンがUnityバージョンと不一致 | 中 | Unity Editorで初回オープン時に自動解決される。問題が出たらUnity Editorから新規プロジェクトを作り直してmanifest.jsonを差し替える |
| `ProjectSettings.asset` を手動作成するとフォーマットが壊れる | 高 | 手動作成せず、Unity Editorの初回起動に自動生成を任せる (Step 6で `.gitkeep` のみ配置) |
| `.meta` ファイルがGit管理から漏れる | 中 | `.gitignore` で `.meta` を除外しないよう注意。Unity Editor の Version Control設定を「Visible Meta Files」にする |

## 成功基準

- [ ] `git status` で不要ファイル(Library/, Temp/等)が追跡されていないこと
- [ ] Unity Hub からプロジェクトフォルダを開けること
- [ ] Unity Editor 起動後、Assets/ 以下のサブディレクトリが正しく表示されること
- [ ] Claude Code がプロジェクトを開いた際に `.claude/CLAUDE.md` を認識すること
- [ ] チームメンバーがクローン後、Unity Editorで問題なく開発を開始できること

## 補足: Unity Editorで初回オープン後に自動生成されるもの

以下は `.gitignore` で除外済みなので、Git管理の心配は不要です。

- `Library/` - インポートキャッシュ(数百MB~数GB)
- `Temp/` - 一時ファイル
- `Logs/` - Editorログ
- `UserSettings/` - 個人設定
- `obj/` - ビルド中間ファイル
- `*.csproj`, `*.sln` - IDE用プロジェクトファイル(自動再生成される)

---

## 実装ログ

### 2026-02-10

- [x] .claude/PLAN.mdファイル作成
- [x] .gitignore作成
- [x] README.md作成
- [x] .claude/CLAUDE.md作成
- [x] Assets/サブディレクトリ作成
- [x] Packages/manifest.json作成
- [x] ProjectSettings/.gitkeep作成
- [x] Git初期化とコミット完了
