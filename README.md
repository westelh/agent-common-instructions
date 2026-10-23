# Coding Agent Instructions

複数のリポジトリで使う、個人用のコーディングエージェント指示を管理する公開リポジトリです。導入先プロジェクトの共有ルールを優先し、共通指示は作業別の文書に分けています。

## ファイル

- [`AGENTS.md`](AGENTS.md): このリポジトリ内で文書を保守するときの指示。導入先へはコピーしません。
- [`INSTRUCTIONS.md`](INSTRUCTIONS.md): 共通指示の入口と、作業別指示の読み方。
- [`instructions/linear-issues.md`](instructions/linear-issues.md): Linear Issueの作成、分割、進捗管理。
- [`instructions/github-workflow.md`](instructions/github-workflow.md): ブランチ、コミット、Pull Request、Linear公式GitHub連携。
- [`instructions/execution.md`](instructions/execution.md): 調査、実装、テスト、報告の進め方。
- [`INSTALL.md`](INSTALL.md): 対象プロジェクトへの初回導入手順。

## 導入

対象プロジェクト内で [`INSTALL.md`](INSTALL.md) を実行してください。`INSTRUCTIONS.md` と `instructions/` をセットで配置し、相対パスを保ちます。ビルドやファイル結合は不要です。

導入手順は個人用の配置を作成し、Gitリポジトリでは `.git/info/exclude` で配置を除外します。共有の `.gitignore` や既存の `AGENTS.md` は変更しません。ルートの `AGENTS.override.md` から既存 `AGENTS.md` と共通指示パッケージを読むようにします。

## 更新

自動同期ツールや自動更新の仕組みはありません。導入は各作業環境につき初回に一度行います。共通指示を更新する場合は、導入先で既存内容との差分を確認し、必要な変更を個別に反映してください。
