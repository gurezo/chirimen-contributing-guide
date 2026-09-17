# Discussion / Issue / Pull Request

相談・報告・提案を、Discussion / Issue / Pull Request のどれで始めるかを判断するための案内です。

このページは既存の公開情報を整理したものです。新しい運用ルールは定めません。対象リポジトリに `CONTRIBUTING.md` がある場合は、そちらの手順を優先してください。

このリポジトリは現在、コントリビュート方法を整理するための Draft / Incubation です。内容が固まったら、chirimen-oh Organization への移管や各リポジトリへの統合を検討します。比較材料は [移管・統合提案](./migration-integration-proposal.md) にあります。

## 基本フロー

まだ内容が固まっていないときは、先に相談します。作業内容が具体化したら Issue にし、実装した変更を Pull Request で出します。

```text
まだ内容が固まっていない
        ↓
    Discussion
        ↓
作業内容が具体化
        ↓
      Issue
        ↓
      実装
        ↓
 Pull Request
```

typo やリンク切れなど、小さな修正は後述のとおり直接 Pull Request してよい場合があります。対象リポジトリの `CONTRIBUTING.md` が別の手順を書いているときは、そちらに従ってください。

Fork から Pull Request までの操作は [GitHub workflow](./github-workflow.md) を見てください。どのリポジトリを変更するかは [Where to Contribute](./where-to-contribute.md) を見てください。

## Discussion が適しているケース

次のようなときは Discussion から始めてください。

- 何を変えたいかは分かるが、進め方がまだ固まっていない
- どのリポジトリを変えればよいか分からない
- 方針やアイデアについて、先に意見を聞きたい
- 使い方や環境構築で困っている

迷ったら、まず [chirimen-oh Organization の Discussions](https://github.com/orgs/chirimen-oh/discussions) に書いてください。対象リポジトリが分かっている場合は、そのリポジトリの Issue でも構いません。

判断できなければ、Discussion からで問題ありません。

### Organization Discussions のカテゴリ

投稿先を選ぶときの目安です。カテゴリの必須化ではありません。

| カテゴリ | 向いていること | 例 |
| --- | --- | --- |
| Q&A | 使い方や進め方の質問 | カテゴリの説明は「Ask the community for help」です。現状このカテゴリの投稿は見当たらないため、質問は Q&A で始めて構いません |
| Ideas | 構成や機能の提案、意見募集 | [chirimen-drivers の構成変更提案](https://github.com/orgs/chirimen-oh/discussions/119)、[Polyfill 版と Node 版の差異](https://github.com/orgs/chirimen-oh/discussions/36) |
| General | コミュニティ運営や横断的な話題 | [CONTRIBUTING の整理](https://github.com/orgs/chirimen-oh/discussions/35) |

カテゴリに迷っても、投稿先が Organization Discussions であれば十分です。

## Issue が適しているケース

次のようなときは、対象リポジトリの Issue にしてください。

- 再現できる不具合を報告する
- 直したい箇所と、望ましい結果が具体的になっている
- 対象リポジトリが分かっており、作業として進めたい

同じ内容の Issue が既にないかを、先に確認してください。既存 Issue があれば、新しい Issue を増やさず、そちらで作業できます。

対象リポジトリが作業前の Issue 作成を求めている場合は、その手順に従ってください。例: [`chirimen.org` の CONTRIBUTING.md](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md) は、作業前に Issue を立てる手順を書いています。これは CHIRIMEN 全体の共通ルールではなく、そのリポジトリの手順です。

## Pull Request が適しているケース

変更をレビューしてもらう段階になったら、Pull Request を作成します。

- 実装や文章の修正が終わっている
- レビューしてマージしてほしい差分がある
- 関連する Issue があれば、説明からリンクする

作り方と Review への対応は [GitHub workflow](./github-workflow.md) を見てください。

## 直接 Pull Request してよいケース

次のような軽微な修正は、Issue を立てずに直接 Pull Request して構いません。

- typo
- リンク切れの修正
- 明らかな表記ミス
- 小規模な文章改善

一方で、対象リポジトリが「作業前に Issue を立てる」と書いているときは、小さな修正でもその手順に従ってください。

## リポジトリ固有ルールが優先されること

このガイドより先に、対象リポジトリの `CONTRIBUTING.md` を読んでください。ビルド手順、作業前の Issue 作成の要否、レビューの進め方は、そこで案内されていることがあります。

例: [`chirimen.org` の CONTRIBUTING.md](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md) は、作業前の Issue 作成とローカル起動の手順を書いています。

## 判断できない場合

迷ったら、まず [chirimen-oh Organization の Discussions](https://github.com/orgs/chirimen-oh/discussions) に書いてください。

対象リポジトリが分かっている場合は、そのリポジトリの Issue でも構いません。既存のメンテナーに個別で聞かなくても、コミュニティで相談できます。

判断できなければ、Discussion からで問題ありません。

## 次に読む

- [Getting Started](./getting-started.md) — 貢献の種類と相談先
- [Where to Contribute](./where-to-contribute.md) — どのリポジトリを変更すればよいか
- [GitHub workflow](./github-workflow.md) — Fork から Pull Request までの進め方
- [Pi Zero ESM Example](./examples/pizero-esm-examples.md) — Example の追加・修正手順
- [既存 contribution ドキュメントの棚卸し](./existing-contribution-docs.md) — 既存情報の重複・不足・要確認
- [chirimen-oh への移管・統合提案](./migration-integration-proposal.md) — 将来の配置の比較材料
