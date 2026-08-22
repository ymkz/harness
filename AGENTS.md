# AGENTS.md

## このリポジトリの位置づけ

このリポジトリ（harness）は、`~/.agents/skills/` や `~/.codex/` などの**グローバル設定を管理・配布するためのAPMパッケージのソース**です。作業用のプロジェクトではありません。

## 絶対にしないこと

- **リポジトリ内で素の `apm install` / `apm update` を実行しない。** デプロイ成果物が `.agents/skills/` や `.codex/` に展開され、グローバル側と重複する。グローバルに反映するときは必ず `--global` を付ける。
- **生成物（`.agents/`、`.codex/`、`apm_modules/`）をコミットしない。** これらは `.gitignore` 済みのデプロイ成果物であり、ソースではない。
- **手書きのスキルをこのリポジトリにコピーしない。** `~/.agents/skills/` 側を正とする。

## スキルの追加・更新

1. 外部スキルは `apm.yml` の dependencies に追加し、`apm install <パッケージ指定> --global` でグローバルへ反映する
   - 注意: `apm install --global`（引数なし）はプロジェクトの `apm.yml` ではなく `~/.apm/apm.yml` を読むため、`apm.yml` に追加しただけの依存は**エラーなく無視される**
   - `apm install <owner/repo/.../skill> --global` を実行すると `~/.apm/apm.yml` も自動更新され、以降は引数なしの `--global` でも解決される
   - 実行後は `ls ~/.agents/skills/` で配置を必ず確認する
2. 手書きスキルは `~/.agents/skills/` に直接置く（このリポジトリでは管理しない）
3. 設定ファイルの再生成は `apm compile --global`
