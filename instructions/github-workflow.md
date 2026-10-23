# GitHubとLinearの連携

> この節は、作業でLinearを利用する場合にのみ適用する。Linearを使わない作業では、Issueの作成・紐付けを要求しない。対象Issueが見つからない、またはLinearに接続できない場合はその状態を明示し、Issue IDを作成・推測して成功扱いしない。

## ブランチ・コミット

- ブランチ名にLinear Issue IDを含めない。

- コミットメッセージにLinear Issue IDを含めない。

- ブランチ名には `feat/description`、`fix/description` など、変更内容を表す名前を使用する。

- コミットメッセージはリポジトリの既存規約に従う。規約がない場合はConventional Commitsを使用する。

- Linearが生成したIssue ID付きブランチ名を、そのまま使用しない。

- コミットの本文やトレーラーにもLinear Issue IDを挿入しない。

## Pull Request

- PRタイトルにLinear Issue IDを含めない。

- PR本文には、対象のLinear Issue IDを公式GitHub連携が認識する形式で記載する。

- 通常の実装・バグ修正では `Fixes ABC-123` 形式を使用する。

- Issueを完了させない関連PRでは `Refs ABC-123` を使用する。

- ステータス連動が不要な関連付けには `Related to ABC-123` を使用する。

- `ABC-123` は実際のIssue IDに置き換える。架空のIssue IDを使用しない。

- PR本文にIssue IDを記載する場合、Linear IssueへのURLを重複して記載する必要はない。

- PR本文には変更概要、変更理由、テスト結果、必要な補足事項を記載する。

- 既存のPRテンプレートがある場合はそれを維持し、Linear参照を適切な位置に追加する。

- PR作成後、Linear Issue上にPRが公式GitHub連携として表示されていることを確認する。

- 紐付けが確認できない場合は原因を調査し、通常のURL添付だけで連携成功と判断しない。

- 子Issueに対応するPRは、原則として該当する子Issueに紐付ける。

- 親Issue全体を完了させる意図がない限り、子IssueのPRに親Issueへの `Fixes` を記載しない。

## 連携エラーへの対応

- PR作成後、Linear Issueとの紐付けを必ず検証する。

- 紐付けが失敗した場合は、Issue ID、GitHub Integrationの設定、PR本文の参照形式を確認する。

- PRコメントにMagic Wordsを投稿する方法を、紐付け手段として使用しない。

- 必要な場合はPR本文を修正し、公式連携による再認識を試みる。

- 公式連携で認識されない場合は、ユーザーに報告する。

- Linear連携の失敗を理由に、GitHub上の実装成果を破棄しない。

- API操作やツール呼び出しが失敗した場合、成功したと仮定しない。

## 禁止事項

- Linear Issue IDをブランチ名、コミットメッセージ、PRタイトルに記載すること。

- Linear Issue IDをソースコードやドキュメントへ不要に埋め込むこと。

- PRのマージ前に、単なる実装完了を理由としてIssueをCompletedにすること。

- 通常のURL添付を、公式GitHub IntegrationによるPR紐付けと同一視すること。

- 明示的な許可なしにforce push、共有履歴の書き換え、リモートブランチの削除を行うこと。

- LinearやGitHubの連携状態を確認せず、連携完了と報告すること。
