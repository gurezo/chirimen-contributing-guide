# 既存 contribution ドキュメントの棚卸し

CHIRIMEN に現在存在する contribution 関連情報を、公開ページから棚卸しした結果です。初心者向けの手順書ではなく、重複・不足・暗黙知・要確認を可視化するための調査メモです。

このページは既存の公開情報を整理したものです。新しい運用ルールは定めません。対象リポジトリに `CONTRIBUTING.md` がある場合は、そちらの手順を優先してください。

このリポジトリは現在、コントリビュート方法を整理するための Draft / Incubation です。内容が固まったら、chirimen-oh Organization への移管や各リポジトリへの統合を検討します。移管方法の提案は [#8](https://github.com/gurezo/chirimen-contributing-guide/issues/8) の対象です。

調査日: 2026-09-17。公開情報だけを見ています。リンク切れや現行と食い違う記述は、推測で埋めず Needs confirmation に回しています。

## 調査対象（Sources）

Issue [#7](https://github.com/gurezo/chirimen-contributing-guide/issues/7) が挙げた情報源と、関連して確認したページです。

| 情報源 | 確認したこと | リンク |
| --- | --- | --- |
| Organization Discussions | 相談の場。Q&A / Ideas / General がある。CONTRIBUTING 整理の議論がある | [Discussions](https://github.com/orgs/chirimen-oh/discussions)、[#35](https://github.com/orgs/chirimen-oh/discussions/35)、[#36](https://github.com/orgs/chirimen-oh/discussions/36)、[#119](https://github.com/orgs/chirimen-oh/discussions/119) |
| `chirimen-oh/chirimen.org` | 公式サイトとチュートリアル。`CONTRIBUTING.md` あり。旧名 `tutorials` | [リポジトリ](https://github.com/chirimen-oh/chirimen.org)、[CONTRIBUTING.md](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md) |
| chirimen.org Wiki | サイトと URL の対応。contribution 手順そのものはほぼ無い | [Home](https://github.com/chirimen-oh/chirimen.org/wiki)、[コミュニティで公開しているサイト](https://github.com/chirimen-oh/chirimen.org/wiki/%E3%82%B3%E3%83%9F%E3%83%A5%E3%83%8B%E3%83%86%E3%82%A3%E3%81%A7%E5%85%AC%E9%96%8B%E3%81%97%E3%81%A6%E3%81%84%E3%82%8B%E3%82%B5%E3%82%A4%E3%83%88) |
| サイト側ページ | Feedback・行動規範。編集時の注意と相談先 | [Feedback](https://chirimen.org/feedback)、[行動規範](https://chirimen.org/code-of-conduct) |
| `pizero/src/esm-examples` | Pi Zero ESM Example の置き場所。専用の contribution 手順はリポジトリ内に見当たらない | [ディレクトリ](https://github.com/chirimen-oh/chirimen.org/tree/master/pizero/src/esm-examples) |
| `chirimen-oh/examples` | archived。現行の Example 変更先ではない | [リポジトリ](https://github.com/chirimen-oh/examples) |
| `chirimen-oh/chirimen-drivers` | I2C ドライバ。`CONTRIBUTING.md` と `docs/contributing/` が最も詳しい | [CONTRIBUTING.md](https://github.com/chirimen-oh/chirimen-drivers/blob/master/CONTRIBUTING.md)、[サイト版](https://chirimen.org/chirimen-drivers/CONTRIBUTING) |
| 各 README | 役割は書かれているが、contribution 手順はリポジトリ差が大きい | 下表 |
| 各 `CONTRIBUTING.md` | `chirimen.org` と `chirimen-drivers` にある。主要 runtime リポジトリには見当たらない | 下表 |
| 旧サイト | `www.chirimen.org` 用。メンテナンス終了の警告あり | [`chirimen-oh.github.io`](https://github.com/chirimen-oh/chirimen-oh.github.io) |

### README / CONTRIBUTING.md の有無

| リポジトリ | README | CONTRIBUTING.md |
| --- | --- | --- |
| [`chirimen.org`](https://github.com/chirimen-oh/chirimen.org) | サイト本文（トップページ） | [あり](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md) |
| [`chirimen-drivers`](https://github.com/chirimen-oh/chirimen-drivers) | 使い方と貢献ガイドへのリンク | [あり](https://github.com/chirimen-oh/chirimen-drivers/blob/master/CONTRIBUTING.md)（`docs/contributing/` に分割） |
| [`node-web-gpio`](https://github.com/chirimen-oh/node-web-gpio) | 使い方 | 見当たらない |
| [`node-web-i2c`](https://github.com/chirimen-oh/node-web-i2c) | 使い方 | 見当たらない |
| [`chirimen-lite`](https://github.com/chirimen-oh/chirimen-lite) | OS イメージの作り方・リリース | 見当たらない |
| [`chirimen`](https://github.com/chirimen-oh/chirimen) | Raspberry Pi 向け環境 | 見当たらない |
| [`chirimen-micro-bit`](https://github.com/chirimen-oh/chirimen-micro-bit) | micro:bit 向け実装 | 見当たらない |
| [`chirimen-oh.github.io`](https://github.com/chirimen-oh/chirimen-oh.github.io) | 旧サイトの編集手順（メンテナンス終了） | ファイルとしては無く、README に手順がある |

## Existing documentation

すでに明文化されている情報です。

### chirimen.org

- Fork、作業前の Issue 作成、ブランチ、Pull Request、レビュー待ちの手順（[CONTRIBUTING.md](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md)）
- ローカル起動（mise、Jekyll、`bundle exec jekyll serve`）
- `master` マージ後の GitHub Actions → Cloudflare Pages デプロイ
- サイト本文の編集注意（ファイル名は小文字、相対リンク、Cloudinary、多言語）（[Feedback](https://chirimen.org/feedback)）
- 書き込み権限があるメンバーは、ページ末尾の「現在のページを GitHub で編集する」からブラウザ編集できること（Feedback）
- コミュニティの行動規範（[code-of-conduct](https://chirimen.org/code-of-conduct)）
- サイトと URL の対応（[Wiki](https://github.com/chirimen-oh/chirimen.org/wiki)）

### chirimen-drivers

- 貢献の種類ごとのフローチャートと目次（[CONTRIBUTING.md](https://github.com/chirimen-oh/chirimen-drivers/blob/master/CONTRIBUTING.md)）
- GitHub UI での誤字修正、Git を使ったドキュメント修正、既存ドライバ修正、新規ドライバ追加、リリース
- Issues / Pull Request の基本ルール。ブランチ名 `type/short-description`、コミットは Conventional Commits（[はじめに・基本ルール](https://github.com/chirimen-oh/chirimen-drivers/blob/master/docs/contributing/getting-started.md)）
- サンプル単体・デバイス単体向けガイドは未整備であること（同ファイル、[#464](https://github.com/chirimen-oh/chirimen-drivers/issues/464)）

### Organization Discussions

- 方針やアイデアの相談先として使われている（例: [#35](https://github.com/orgs/chirimen-oh/discussions/35) CONTRIBUTING の整理、[#36](https://github.com/orgs/chirimen-oh/discussions/36)、[#119](https://github.com/orgs/chirimen-oh/discussions/119)）
- カテゴリの目安は、このガイドの [Discussion / Issue / Pull Request](./discussions-issues-pull-requests.md) に整理済み

### このガイドリポジトリ（v0.1 で追加済み）

- [Getting Started](./getting-started.md) — 貢献の種類と相談先（[#2](https://github.com/gurezo/chirimen-contributing-guide/issues/2)）
- [Where to Contribute](./where-to-contribute.md) — どのリポジトリを変更するか（[#3](https://github.com/gurezo/chirimen-contributing-guide/issues/3)）
- [GitHub workflow](./github-workflow.md) — Fork から Pull Request（[#4](https://github.com/gurezo/chirimen-contributing-guide/issues/4)）
- [Discussion / Issue / Pull Request](./discussions-issues-pull-requests.md) — 使い分け（[#5](https://github.com/gurezo/chirimen-contributing-guide/issues/5)）
- [Pi Zero ESM Example](./examples/pizero-esm-examples.md) — Example の追加・修正（[#6](https://github.com/gurezo/chirimen-contributing-guide/issues/6)）

## Duplicated documentation

複数箇所にあり、将来的に整理が必要な情報です。どちらを正とするかは、このページでは決めません。

| 内容 | ある場所 | ずれ |
| --- | --- | --- |
| Fork → clone → PR | [`chirimen.org` CONTRIBUTING.md](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md)、[`chirimen-drivers` の手順ガイド](https://github.com/chirimen-oh/chirimen-drivers/blob/master/CONTRIBUTING.md)、[このガイドの GitHub workflow](./github-workflow.md)、[旧 `chirimen-oh.github.io` README](https://github.com/chirimen-oh/chirimen-oh.github.io) | 共通の入口が Organization 側に無い。旧 README は現行サイトの手順ではない |
| サイト編集の手順と注意 | [CONTRIBUTING.md](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md)（全体の流れ・ローカル起動）、[Feedback](https://chirimen.org/feedback)（Markdown / 画像 / 多言語） | Feedback は CONTRIBUTING へ誘導している一方、Issue 先やリポジトリ名が古い（後述） |
| Issue / PR の使い方 | chirimen.org は作業前 Issue 必須。chirimen-drivers は typo を GitHub UI で可。このガイドは小さな修正の直接 PR を可（対象リポジトリの CONTRIBUTING 優先） | CHIRIMEN 全体の共通ルールとしては書かれていない |
| 相談先 | Organization Discussions、各リポジトリの Issue、Feedback の Slack | 初心者が最初にどれを使えばよいか、公式の単一案内が無い |
| サイトとリポジトリの対応 | [Wiki](https://github.com/chirimen-oh/chirimen.org/wiki)、[Where to Contribute](./where-to-contribute.md)、旧 `chirimen-oh.github.io` の警告文 | Wiki は配信の説明、Where to Contribute は変更先の説明。役割が近い |

## Missing documentation

初心者向けに不足している情報です。このガイドで既に補っているものは、その旨を書いてあります。

- Organization 共通の contribution 入口。各リポジトリの `CONTRIBUTING.md` を横断して「何から始めるか」を案内する公式ページは、chirimen-oh 配下には無い。本リポジトリが Draft / Incubation として担っている
- `node-web-gpio` / `node-web-i2c` の `CONTRIBUTING.md`。README は使い方のみ
- `chirimen` / `chirimen-micro-bit` / `chirimen-lite` の contribution 手順
- Pi Zero ESM Example（`pizero/src/esm-examples`）の、`chirimen.org` リポジトリ内の追加・修正手順。本ガイドの [Pi Zero ESM Example](./examples/pizero-esm-examples.md) で補完済み
- 初心者向けの「どのリポジトリを触るか」の公式マップ。本ガイドの [Where to Contribute](./where-to-contribute.md) で補完済み
- Discussion / Issue / Pull Request の Organization 共通の使い分け。本ガイドの [専用ページ](./discussions-issues-pull-requests.md) で補完済み
- Organization Discussions の Q&A の運用。カテゴリはあるが、このガイド作成時点では投稿がほとんど見当たらない
- micro:bit 向け Example / ドライバを、`chirimen.org` / `chirimen-micro-bit` / `chirimen-drivers` のどれに出すか
- `chirimen-drivers` のサンプル単体・デバイス単体向けガイド（[#464](https://github.com/chirimen-oh/chirimen-drivers/issues/464) が未整備と明記）

## Undocumented knowledge

実際には使われている、または公開情報から読み取れるが、初心者向けの共通文書としては落ちていない情報です。

- 書き込み権限があるメンバーは、GitHub の Web 編集からサイトを直せる（[Feedback](https://chirimen.org/feedback) にはあるが、Organization 共通ガイドには無い）
- Slack が相談先として案内されている（Feedback の「コミュニティ Slack」）。Organization Discussions との役割分担は書かれていない
- Conventional Commits と `type/short-description` ブランチは `chirimen-drivers` のルールであり、CHIRIMEN 全体の必須ではない（このガイドも、このリポジトリ内の慣習として使っている）
- `examples` リポジトリは archived。現行の Pi Zero ESM Example の変更先は `chirimen.org` の `pizero/src/esm-examples`
- `chirimen-oh/tutorials` は `chirimen.org` に改名されている。GitHub はリダイレクトするが、Feedback 内のリンク文言は旧名のまま
- 旧 `www.chirimen.org`（`chirimen-oh.github.io`）は 2025-09-22 以降メンテナンスされていない、と README が警告している
- ブラウザ版 WebGPIO / WebI2C の [`polyfills`](https://github.com/chirimen-oh/polyfills) は archived。現行の変更先は README だけでは分からない

## Needs confirmation

公開 README や CONTRIBUTING だけでは断定できないため、推測で決めません。分からなければ [Organization Discussions](https://github.com/orgs/chirimen-oh/discussions) で確認してください。

- ブラウザ版 WebGPIO / WebI2C（archived の [`polyfills`](https://github.com/chirimen-oh/polyfills) や [`chirimen`](https://github.com/chirimen-oh/chirimen) 環境）の、現行の変更先
- micro:bit 向け Example / ドライバを [`chirimen.org`](https://github.com/chirimen-oh/chirimen.org) / [`chirimen-micro-bit`](https://github.com/chirimen-oh/chirimen-micro-bit) / [`chirimen-drivers`](https://github.com/chirimen-oh/chirimen-drivers) のどれに出すか
- npm パッケージ `chirimen` が `node-web-gpio` / `node-web-i2c` をどこまで再エクスポートしているか。アプリから `chirimen` を import して使うことと、runtime 本体の修正先は別問題として扱う
- Slack を公式の相談先として、このガイドから案内してよいか
- `www.chirimen.org` / `chirimen-oh.github.io` を、まだ編集対象として案内するか
- [Feedback](https://github.com/chirimen-oh/chirimen.org/blob/master/feedback.md) の Issue リンク（`chirimen-oh/tutorials`）、GitHub Pages の説明、Slack 通知が現行運用か
- `chirimen-drivers` の構成に関する議論（[#461](https://github.com/chirimen-oh/chirimen-drivers/pull/461) など）を、共通ガイドの前提にしてよいか
- Organization Discussions の Q&A を、初心者の最初の相談先として勧めてよいか

上記のうちリポジトリ役割に関する項目は、[Where to Contribute](./where-to-contribute.md) の Needs confirmation と同じです。

## v0.1 で優先する文書化

親 Issue [#1](https://github.com/gurezo/chirimen-contributing-guide/issues/1) の対象と、棚卸し結果の対応です。新しいルールを足すのではなく、既存情報の穴をこのガイドで可視化することを優先しています。

| 親 Issue の対象 | 状態 | この棚卸しでの位置づけ |
| --- | --- | --- |
| Getting Started | 本ガイドで文書化済み（#2） | Missing のうち「何から始めるか」を補完 |
| Repository responsibility map | 本ガイドで文書化済み（#3） | Missing のうち「どのリポジトリか」を補完。未確認は Needs confirmation に残す |
| GitHub contribution workflow | 本ガイドで文書化済み（#4） | 分散している Fork → PR の説明を、初心者向けに一箇所へ |
| Discussion / Issue / Pull Request | 本ガイドで文書化済み（#5） | 相談先の分散を、判断材料として整理 |
| Pi Zero ESM Example | 本ガイドで文書化済み（#6） | Missing のうち公式リポジトリ内手順を補完 |
| 既存ドキュメントの棚卸し | このページ（#7） | Existing / Duplicated / Missing / Undocumented / Needs confirmation |
| `chirimen-oh` への移管・統合 | [#8](https://github.com/gurezo/chirimen-contributing-guide/issues/8)。本ページでは書かない | Duplicated の解消先と、Single source of truth の検討材料 |

v0.1 の対象外（親 Issue の Out of scope）は、ここでも扱いません。

- CHIRIMEN 本体コードの変更
- 全リポジトリの `CONTRIBUTING.md` の全面改訂
- 新しい開発ルールの一方的な制定
- CI/CD の変更
- コーディング規約全般の再設計
- 各デバイスドライバの実装変更

## 次に読む

- [Getting Started](./getting-started.md) — 貢献の種類と相談先
- [Where to Contribute](./where-to-contribute.md) — どのリポジトリを変更すればよいか
- [GitHub workflow](./github-workflow.md) — Fork から Pull Request までの進め方
- [Discussion / Issue / Pull Request](./discussions-issues-pull-requests.md) — 相談・報告・提案の使い分け
- [Pi Zero ESM Example](./examples/pizero-esm-examples.md) — Example の追加・修正手順
