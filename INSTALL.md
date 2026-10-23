# INSTALL.md

この文書は、指示パッケージを作業環境へ初回導入する手順です。1環境につき一度だけ実行し、作業は対象プロジェクト内で行います。

## 取得元とダウンロード

- 取得元は公開GitHubリポジトリ [`westelh/agent-common-instructions`](https://github.com/westelh/agent-common-instructions) の `main` ブランチです。公開取得に認証情報は使いません。
- `INSTRUCTIONS.md` と `instructions/` を含むアーカイブをダウンロード・展開します。ビルドやファイル結合は不要です。
- 完了報告には取得コミットIDを記載します。取得できない場合や必須ファイルが欠けている場合は導入を中止し、部分配置を残しません。

プロジェクトルートで次を実行します。`<TEMP_DIR>` はプロジェクト内の一時ディレクトリ、`<COMMIT_SHA>` は1行目で得たコミットIDです。

```sh
git ls-remote --exit-code https://github.com/westelh/agent-common-instructions.git refs/heads/main
curl -fL https://codeload.github.com/westelh/agent-common-instructions/tar.gz/<COMMIT_SHA> -o <TEMP_DIR>/source.tar.gz
mkdir -p <TEMP_DIR>/source
tar -xzf <TEMP_DIR>/source.tar.gz --strip-components=1 -C <TEMP_DIR>/source
```

展開した一時ツリーから `INSTRUCTIONS.md` と `instructions/` だけを配置します。取得元URLとコミットIDをプロジェクト内に記録するファイルは作りません。

## 配置する内容

既存の配置慣習がなければ、次の場所に配置します。

```text
<project-root>/agent-instructions/
├── INSTRUCTIONS.md
└── instructions/
    ├── linear-issues.md
    ├── github-workflow.md
    └── execution.md
```

`INSTRUCTIONS.md` と `instructions/` はセットで配置し、相対パスを保ちます。`README.md` と `INSTALL.md` は導入先にコピーしません。

## 導入手順

### 1. 導入状態と既存指示を確認する

1. プロジェクトルートの `AGENTS.md`、`AGENTS.override.md` と配置先を確認します。
2. `agent-instructions/INSTRUCTIONS.md`、全リンク先、ルートの有効な指示からの参照が揃っていれば終了します。
3. コピー先に既存の `AGENTS.override.md` またはパッケージファイルがあれば上書きせず、衝突として止めます。

### 2\. 指示ファイルを配置する

衝突がなければ、アーカイブから `INSTRUCTIONS.md` と `instructions/` を配置先へコピーします。既存慣習に従う場合は、以降の参照パスもその配置先に合わせます。

### 3\. 個人用の読み込み入口を設定する

既存の `AGENTS.md` は変更しません。ルートに `AGENTS.md` がある場合は、それを読むよう明記した `AGENTS.override.md` を新規作成します。`AGENTS.md` がない場合は、共通指示パッケージだけを読む `AGENTS.override.md` を作成します。

`AGENTS.md` がある場合、`AGENTS.override.md` に次の指示を記載します。

> 作業を始める前に `AGENTS.md` を読み、その指示に従うこと。続けて `agent-instructions/INSTRUCTIONS.md` と該当する作業別指示を読み、従うこと。

`AGENTS.md` がない場合は、次の指示を記載します。

> 作業を始める前に `agent-instructions/INSTRUCTIONS.md` を読み、該当する作業別指示にも従うこと。

配置先が異なる場合はパスを合わせます。

この導入は個人用として扱います。Gitリポジトリでは `git rev-parse --git-path info/exclude` が示す除外ファイルに次を追加し、共有 `.gitignore` は変更しません。配置先を変えた場合は1行目のパスを合わせます。

```gitignore
/agent-instructions/
/AGENTS.override.md
```

既存の `AGENTS.override.md` がある場合は編集・上書きせず、衝突として止めます。

### 4\. 配置を確認する

- `INSTRUCTIONS.md` の全リンク先と、`AGENTS.override.md` の読み込み参照を確認します。Gitリポジトリでは上記の除外ファイルが配置ディレクトリと `AGENTS.override.md` を除外していることも確認します。依頼なしにステージングやコミットはしません。
- 失敗時は今回追加した不完全なファイルと参照だけを取り消し、既存内容を保ちます。

## 導入後の確認

新しいCodex実行またはセッションで、有効なルート指示、`INSTRUCTIONS.md`、該当する作業別指示が読み込まれることを確認します。

Codex Cloudでは、新しいタスクにも配置が保持されることを確認します。保持方法が未確定なら、コミットせずユーザーに確認します。

## 範囲

- 作業はプロジェクト内に限り、プロジェクト固有の指示を優先します。`CODEX_HOME` 等の変更は明示依頼がある場合だけ行います。
- この手順は初回導入のみを扱います。更新・再同期・解除は対象外です。

## 参考

- [Codexの `AGENTS.md` 指示読み込み](https://developers.openai.com/codex/agent-configuration/agents-md)
- [Codex Cloudの環境とタスク](https://developers.openai.com/codex/cloud)
