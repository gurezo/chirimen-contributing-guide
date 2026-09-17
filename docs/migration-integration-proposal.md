# chirimen-oh への移管・統合提案

`gurezo/chirimen-contributing-guide` で整理した内容を、将来的に `chirimen-oh` Organization へどのように移管・統合するかの比較材料です。

このページはコミュニティが判断するための提案文です。新しい運用ルールは定めません。どの構成を採用するかも、ここでは決めません。

実際の移管・統合は、コミュニティの合意後に進める想定です。Organization Discussions に貼れる文章は、末尾の [投稿用ドラフト](#organization-discussions-投稿用ドラフト) にあります。このリポジトリの作業としては投稿しません。

## この文書の位置づけ

このリポジトリは、最初から独立した恒久プロジェクトとすることを目的としていません。

まず `gurezo` 配下で既存の暗黙知を整理し、コミュニティでレビュー可能な状態を作ったうえで、正式な配置を検討します。親 Issue [#1](https://github.com/gurezo/chirimen-contributing-guide/issues/1) の v0.1 では、移管そのものではなく、判断材料を揃えるところまでを対象にしています。

対象 Issue: [#8](https://github.com/gurezo/chirimen-contributing-guide/issues/8)

## 現状

- リポジトリ: [`gurezo/chirimen-contributing-guide`](https://github.com/gurezo/chirimen-contributing-guide)
- 位置づけ: Draft / Incubation。`gurezo` 配下で管理している
- Organization 側に、各リポジトリの `CONTRIBUTING.md` を横断して「何から始めるか」を案内する公式ページは見当たらない（[既存ドキュメントの棚卸し](./existing-contribution-docs.md) の Missing）

### v0.1 で揃ったページ

| ページ | 内容 |
| --- | --- |
| [Getting Started](./getting-started.md) | 貢献の種類と相談先 |
| [Where to Contribute](./where-to-contribute.md) | どのリポジトリを変更するか |
| [GitHub workflow](./github-workflow.md) | Fork から Pull Request |
| [Discussion / Issue / Pull Request](./discussions-issues-pull-requests.md) | 相談・報告・提案の使い分け |
| [Pi Zero ESM Example](./examples/pizero-esm-examples.md) | Example の追加・修正 |
| [既存 contribution ドキュメントの棚卸し](./existing-contribution-docs.md) | 既存情報の重複・不足・要確認 |

## 情報の分け方（判断材料）

移管・統合を考えるとき、いまのページはおおよそ次のように分かれます。これは現時点の切り分けであり、正しい配置を決めるものではありません。

### 共通情報

複数リポジトリにまたがる案内です。Organization 側の入口になり得ます。

- [Getting Started](./getting-started.md)
- [Where to Contribute](./where-to-contribute.md)
- [GitHub workflow](./github-workflow.md)
- [Discussion / Issue / Pull Request](./discussions-issues-pull-requests.md)
- [既存 contribution ドキュメントの棚卸し](./existing-contribution-docs.md)（調査メモ。公開入口に残すかは未定）

### リポジトリ固有情報

対象リポジトリの近くで管理した方が、更新しやすい情報です。すでに `CONTRIBUTING.md` があるものもあります。

- [Pi Zero ESM Example](./examples/pizero-esm-examples.md) → [`chirimen.org`](https://github.com/chirimen-oh/chirimen.org) の `pizero/src/esm-examples`
- サイト編集・ローカル起動 → 既存の [`chirimen.org` CONTRIBUTING.md](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md)
- ドライバの追加・修正 → 既存の [`chirimen-drivers` CONTRIBUTING](https://chirimen.org/chirimen-drivers/CONTRIBUTING)

Issue [#8](https://github.com/gurezo/chirimen-contributing-guide/issues/8) が挙げる分割イメージです。

```text
共通情報
  ↓
Organization-level contribution guide

Repository 固有情報
  ↓
各 Repository の CONTRIBUTING.md / docs
```

## Option A: Repository transfer

`chirimen-contributing-guide` 自体を `chirimen-oh` Organization に移管する。

例: `gurezo/chirimen-contributing-guide` → `chirimen-oh/chirimen-contributing-guide`

### メリット

- 文書の置き場所が 1 リポジトリのままなので、Single source of truth を保ちやすい
- Issue・コミット履歴を維持したまま移せる
- 初心者から見た入口が 1 つになる
- メンテナンス責任を「このリポジトリ」単位で説明しやすい

### 課題

- 各リポジトリの `CONTRIBUTING.md` との重複は、移管だけでは減らない
- 公式サイトや Organization からの導線は、移管とは別に決める必要がある
- Wiki / Discussions との役割分担も、移管だけでは決まらない
- Pi Zero ESM Example などリポジトリ固有の手順が、共通ガイド側に残り続ける

## Option B: Split and integrate

共通情報とリポジトリ固有情報を分割し、それぞれ既存の置き場所へ統合する。

### メリット

- 重複を減らせる。固有手順はコードの近くに置ける
- 既存の `chirimen.org` / `chirimen-drivers` の `CONTRIBUTING.md` を活かせる
- 更新は、そのリポジトリの担当範囲に寄せやすい

### 課題

- Single source of truth が複数箇所に分かれる
- 共通ガイドをどこに置くかを、別途決める必要がある
- 初心者が複数箇所を探すことになる
- 各 `CONTRIBUTING.md` への反映は、親 Issue の Out of scope（全面改訂）に近く、実施するなら段階的になる

### 共通ガイドの置き場所（サブ選択肢）

Option B を採る場合でも、共通部分の置き場所はまだ分かれる。ここでは列挙するだけで、採用しない。

| 候補 | 向いていること | 論点 |
| --- | --- | --- |
| `chirimen.org` のサイトページ | 公式サイトが初心者の入口になる | サイト編集手順に乗る。チュートリアル本文との役割分担が要る |
| Organization の `.github` / profile README | GitHub 上の Organization 入口になる | 長文ガイド向きかは要確認。サイトからの導線は別途 |
| `chirimen-oh` 配下の専用リポジトリ | ガイドを独立して版管理できる | Option A に近い形になる。入口がサイトから離れる |

## Option C: Hybrid

Organization 共通ガイドを残しつつ、詳細手順を各 Repository 側で管理する。

共通側は「何から始めるか」「どのリポジトリか」「どこで相談するか」の入口と、各 `CONTRIBUTING.md` へのリンクに寄せる。固有側は既存の手順を正とする。

### メリット

- 初心者の入口と、リポジトリ固有の詳細を分けられる
- 既存の `chirimen.org` / `chirimen-drivers` の `CONTRIBUTING.md` を活かせる
- 共通ガイドは薄く保てる。固有の変更は各リポジトリで完結しやすい

### 課題

- 入口と詳細の二重管理になる。リンク切れや内容のずれが起きやすい
- どちらを正とするか（Single source of truth）を明示しないと、更新が止まりやすい
- メンテナンス責任が「共通ガイド」と「各リポジトリ」の二層になる
- 共通ガイドの置き場所は、Option A に近い独立リポジトリか、Option B のサブ選択肢か、別途決める必要がある

## 検討観点の比較

Issue [#8](https://github.com/gurezo/chirimen-contributing-guide/issues/8) が挙げた観点です。優劣の結論は書きません。

| 観点 | Option A | Option B | Option C |
| --- | --- | --- | --- |
| Single source of truth | ガイドリポジトリ 1 つに寄せやすい。各 `CONTRIBUTING.md` との関係は残る | 共通と固有で正が分かれる。共通の置き場所も複数候補がある | 共通は入口、固有は各 `CONTRIBUTING.md`、と役割を分ければ正を示しやすい。明示が無いと曖昧になる |
| メンテナンス責任 | ガイドリポジトリ単位で説明しやすい | 各リポジトリの担当に寄せやすい。共通部分の担当は別途決める | 共通と固有の二層。どちらが直すかを決めておく必要がある |
| Repository 固有情報との重複 | 移管だけでは残る | 分割すれば減らせる。統合作業のコストがある | 入口と詳細で重複し得る。リンク中心にすれば減らせる |
| Wiki との役割分担 | 移管後も、Wiki は配信・サイト対応、ガイドはコントリビュート案内、と分ける余地がある。自動では決まらない | 固有情報を各リポジトリへ移すと、Wiki とサイト手順の重なりを個別に見ることになる | 共通ガイドから Wiki と各 `CONTRIBUTING.md` へ誘導する形を取りやすい |
| Discussions との役割分担 | ガイドは手順の文書、Discussions は相談の場、という切り分けを移管後も使える | 共通案内の置き場所がサイトや README になると、Discussions への誘導元が変わる | 共通ガイドで相談先を案内し、詳細は各リポジトリ、相談は Discussions、と分けやすい |
| Webサイトからの導線 | 移管とは別に、`chirimen.org` からのリンクが要る | サイト自身に共通ガイドを置く案と相性がよい | サイトは入口へ、入口から各 `CONTRIBUTING.md` へ、と二段にできる |
| 初心者から見た分かりやすさ | 入口が 1 リポジトリで分かりやすい。固有手順も同じ場所に残る | 最初に読む場所が分散しやすい | 最初の入口は 1 つにできる。次に各リポジトリへ進む |
| 長期的な更新のしやすさ | ガイド側の更新はしやすい。リポジトリ固有の変更を追う負担は残る | 固有情報はコードと一緒に更新しやすい。共通側の同期は別問題 | 役割が分かれていれば更新しやすい。リンクと重複のメンテが続く |

棚卸しで見えた重複（Fork → PR の説明、相談先、サイト編集の注意）の解消先は、Option によって変わる。どれを正とするかは、このページでは決めません。詳細は [既存 contribution ドキュメントの棚卸し](./existing-contribution-docs.md) を見てください。

## 現行ドキュメントの行き先（参考マッピング）

採用した場合の置き場所の目安です。決定ではありません。

| 現ページ | Option A | Option B | Option C |
| --- | --- | --- | --- |
| Getting Started | 移管後も同じリポジトリ | Organization 共通ガイド | Organization 共通ガイド |
| Where to Contribute | 同じ | Organization 共通ガイド | Organization 共通ガイド |
| GitHub workflow | 同じ | 共通ガイド、または各 `CONTRIBUTING.md` へ寄せる | 共通ガイドは概要、固有手順は各 `CONTRIBUTING.md` |
| Discussion / Issue / Pull Request | 同じ | Organization 共通ガイド | Organization 共通ガイド |
| Pi Zero ESM Example | 同じリポジトリに残る | `chirimen.org` の `CONTRIBUTING.md` / docs | `chirimen.org` 側。共通ガイドからはリンク |
| 既存ドキュメントの棚卸し | 同じ。公開入口に残すかは未定 | 作業メモとして残すか、提案後にアーカイブするか | 作業メモとして残すか、共通ガイドの付録にするか |

導線の候補も、ここでは決めません。

- `chirimen.org` の Feedback や新規ページ
- Organization の README
- 各 `CONTRIBUTING.md` からのリンク
- Organization Discussions の案内
- `chirimen.org` Wiki

## この提案で決めないこと

- どの Option を採用するか
- 共通ガイドの最終的な置き場所
- 公式サイト・Wiki・Discussions からの導線の最終形
- 全リポジトリの `CONTRIBUTING.md` の全面改訂
- 新しい開発ルールの制定
- リポジトリの transfer 操作そのもの

親 Issue [#1](https://github.com/gurezo/chirimen-contributing-guide/issues/1) の Out of scope（CHIRIMEN 本体コードの変更、CI/CD、コーディング規約の再設計、デバイスドライバの実装変更）も、ここでも扱いません。

分からなければ、[Organization Discussions](https://github.com/orgs/chirimen-oh/discussions) で確認してください。判断できなければ、Discussion からで問題ありません。

## Organization Discussions 投稿用ドラフト

コミュニティでレビューするときの投稿文案です。カテゴリの目安は Ideas です。必須化ではありません。このリポジトリの作業としては投稿しません。

```text
タイトル案:
CHIRIMEN コントリビュート案内の移管・統合について（比較材料）

本文案:

gurezo/chirimen-contributing-guide で、CHIRIMEN へのコントリビュート方法の v0.1 を整理しています。

このリポジトリは Draft / Incubation で、最初から恒久的な独立プロジェクトにする意図はありません。内容がレビューできる状態になったので、将来的な配置の比較材料をまとめました。

比較している候補:

- Option A: リポジトリごと chirimen-oh へ移管する
- Option B: 共通情報とリポジトリ固有情報を分割し、既存の置き場所へ統合する
- Option C: Organization 共通ガイドを残しつつ、詳細は各リポジトリで管理する

推奨構成は決めていません。Single source of truth、メンテナンス責任、既存 CONTRIBUTING.md との重複、Wiki / Discussions / 公式サイトからの導線、初心者から見た分かりやすさ、長期的な更新のしやすさを並べています。

提案の本文:
https://github.com/gurezo/chirimen-contributing-guide/blob/main/docs/migration-integration-proposal.md

関連:
- https://github.com/gurezo/chirimen-contributing-guide/issues/8
- https://github.com/gurezo/chirimen-contributing-guide/issues/1
```

移管後に投稿する場合は、本文中の URL を移管先に合わせてください。

## 次に読む

- [Getting Started](./getting-started.md) — 貢献の種類と相談先
- [Where to Contribute](./where-to-contribute.md) — どのリポジトリを変更すればよいか
- [GitHub workflow](./github-workflow.md) — Fork から Pull Request までの進め方
- [Discussion / Issue / Pull Request](./discussions-issues-pull-requests.md) — 相談・報告・提案の使い分け
- [Pi Zero ESM Example](./examples/pizero-esm-examples.md) — Example の追加・修正手順
- [既存 contribution ドキュメントの棚卸し](./existing-contribution-docs.md) — 既存情報の重複・不足・要確認
