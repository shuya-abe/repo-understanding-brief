# repo-understanding-brief

Cursor / Codex 向けの Agent Skill です。リポジトリを読んで、就活・研究利用・オンボーディング向けの **UNDERSTANDING ブリーフ**（口頭で説明できる単位）を構造化テキストで出します。

ポンチ絵・用語集・インフォグラフィックは必須にしません。弱いモデルでも破綻しにくい、テキスト中心の型です。

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

- `job-hunt` — 面接で話す用（H セクション付き）
- `research-use` — 他人のリポを研究・依存として読む（G セクション付き）
- `general` — オンボーディング全般

例:

```text
/repo-understanding-brief
https://github.com/OWNER/REPO を job-hunt モードで。日本語です・ます調。
```

## Design notes

- 入力・環境・出力・失敗モードを優先
- 口頭必須 vs Lookup を分ける
- 各技術は「一般に何か」＋「このリポでの役割」
- AI が書いたコードでも、人間が負う判断は明示

詳細は `SKILL.md` を参照してください。

## License

MIT
