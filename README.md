# harness

エージェント向けの共通設定を配布するAPMパッケージです。

## インストール

```sh
apm install --global git@github.com:ymkz/harness.git
apm compile --global
```

`~/.codex/AGENTS.md` が手書きファイルと判定されてスキップされた場合は、既存ファイルを退避してから再度コンパイルします。

```sh
mv ~/.codex/AGENTS.md ~/.codex/AGENTS.md.bak
apm compile --global
```

## 更新

```sh
apm update --global ymkz/harness
apm compile --global
```
