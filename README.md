# harness

エージェント向けの共通設定を配布するAPMパッケージです。

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

リポジトリへ変更をpushした後、利用環境でパッケージを更新してから設定ファイルを再生成します。

```sh
apm update --global ymkz/harness
apm compile --global
```

更新内容を事前に確認する場合は、`--dry-run`を指定します。

```sh
apm update --global ymkz/harness --dry-run
apm compile --global --dry-run
```

更新後は、起動中のエージェントを終了して新しいセッションを開始します。
