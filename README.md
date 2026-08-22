# harness

エージェント向けの共通設定を配布するAPMパッケージです。

## 注意: このリポジトリはグローバル管理用

このリポジトリは `~/.agents/skills/` などのグローバル設定を管理・配布するためのソースです。
リポジトリ内で `apm install` を実行すると、デプロイ成果物が `.agents/skills/` や `.codex/` に展開されてグローバル側と重複します。

- スキルの追加・更新は `apm install --global` / `apm update --global` で行う
- 生成物（`.agents/`、`.codex/`、`apm_modules/`）はコミットしない（`.gitignore` 済み）
- 手書きのスキルは `~/.agents/skills/` 側を正とし、このリポジトリにコピーしない

## インストール

```sh
apm install --global git@github.com:ymkz/harness.git
apm compile --global
```

`~/.codex/AGENTS.md` が手書きファイルと判定されてスキップされた場合は、既存ファイルを日時付きの名前で退避してから再度コンパイルします。

```sh
mv ~/.codex/AGENTS.md ~/.codex/AGENTS.md.bak.$(date +%Y%m%d-%H%M%S)
apm compile --global
```

## 更新

リポジトリへ変更をpushした後、利用環境でパッケージを更新し、Skillなどを再配置してから設定ファイルを再生成します。

```sh
apm update --global ymkz/harness
apm install --global
apm compile --global
```

更新内容を事前に確認する場合は、`--dry-run`を指定します。

```sh
apm update --global ymkz/harness --dry-run
apm install --global --dry-run
apm compile --global --dry-run
```

更新後は、起動中のエージェントを終了して新しいセッションを開始します。
