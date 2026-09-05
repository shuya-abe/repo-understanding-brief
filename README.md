# repo-understanding-brief

Cursor / Codex 向けの Agent Skill です。リポジトリを読んで、就活・研究利用・オンボーディング向けの **UNDERSTANDING ブリーフ**（口頭で説明できる単位）を構造化テキストで出します。

## Install（Cursor）

自動更新はありません。このリポジトリを更新したら、手元でもう一度取り直してください。

### A. ユーザー技能として置く（おすすめの単純ルート）

```bash
# Windows (PowerShell) の例 — ホームは環境に合わせて変える
git clone https://github.com/shuya-abe/repo-understanding-brief.git "$env:USERPROFILE\.cursor\skills\repo-understanding-brief"

# WSL / macOS / Linux
git clone https://github.com/shuya-abe/repo-understanding-brief.git ~/.cursor/skills/repo-understanding-brief
```

フォルダ名は `repo-understanding-brief`、中に `SKILL.md` がある必要があります。

Cursor を再起動（または Reload Window）したあと、**新規** Agent チャットで:

```text
/repo-understanding-brief
```

または「このリポを就活モードで理解ブリーフして」と依頼します。

> 注意: Windows と WSL では `~/.cursor` が別です。Agent が動いている側のホームに置いてください。Cloud Agent で使う場合は Sync Skills や、チャットに `SKILL.md` を添付する方法もあります。

### B. プロジェクトだけに置く

```bash
mkdir -p .cursor/skills/repo-understanding-brief
cp SKILL.md .cursor/skills/repo-understanding-brief/
```

そのリポジトリを開いているときだけ使えます。

## Usage

モード:

- `job-hunt` — 面接で話す用（デモ手順、想定質問への答えの骨子など）
- `research-use` — 他人のリポを研究・依存として読む（信頼できる点と再確認すべき点、拡張ポイントなど）
- `general` — オンボーディング全般

例:

```text
/repo-understanding-brief
https://github.com/OWNER/REPO を job-hunt モードで。日本語です・ます調。
```

## 出力内容

ブリーフには次のような内容が含まれます（モードにより一部が変わります）:

- 一言ピッチとランタイム契約（入力・環境・出力・不変条件）
- アーキテクチャの概略と、主要技術の説明（一般的な意味と、このリポジトリでの役割）
- 運用・デバッグの要点
- 優先度付きの学習チェックリスト

出力仕様の詳細は `SKILL.md` を参照してください。

## License

MIT
