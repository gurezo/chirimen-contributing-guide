# Where to Contribute

「何を変更したいとき、どのリポジトリを使うのか」を判断するための案内です。

このリポジトリは現在、コントリビュート方法を整理するための Draft / Incubation です。内容が固まったら、chirimen-oh Organization への移管や各リポジトリへの統合を検討します。

このページは既存の公開情報を整理したものです。新しい運用ルールは定めません。役割がまだはっきりしない点は、末尾の Needs confirmation に分けて書いてあります。

## 迷ったら

対象リポジトリが分からないときは、まず [chirimen-oh Organization の Discussions](https://github.com/orgs/chirimen-oh/discussions) に書いてください。

対象リポジトリが分かっている場合は、そのリポジトリの Issue でも構いません。Discussion / Issue / Pull Request の使い分けは [専用ガイド](./discussions-issues-pull-requests.md) を見てください。

判断できなければ、Discussion からで問題ありません。

## やりたいこと → 主な対象

| やりたいこと | 主な対象 |
| --- | --- |
| Webサイト・チュートリアルの修正 | [`chirimen.org`](https://github.com/chirimen-oh/chirimen.org) |
| Pi Zero ESM Example の修正・追加 | [`chirimen.org`](https://github.com/chirimen-oh/chirimen.org) の `pizero/src/esm-examples` |
| I2C デバイスドライバの修正・追加 | [`chirimen-drivers`](https://github.com/chirimen-oh/chirimen-drivers) |
| GPIO runtime（Node.js）の変更 | [`node-web-gpio`](https://github.com/chirimen-oh/node-web-gpio) |
| I2C runtime（Node.js）の変更 | [`node-web-i2c`](https://github.com/chirimen-oh/node-web-i2c) |
| 対象が分からない | [Organization Discussions](https://github.com/orgs/chirimen-oh/discussions) |

## 主要リポジトリ

### chirimen.org

- リポジトリ: [chirimen-oh/chirimen.org](https://github.com/chirimen-oh/chirimen.org)
- 役割: CHIRIMEN の公式サイトと、各ボード向けチュートリアル
- 向いている変更: サイト本文、チュートリアル、Pi Zero ESM Example の追加・修正
- コントリビュート手順: [CONTRIBUTING.md](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md)

Pi Zero ESM Example の置き場所は、このリポジトリの `pizero/src/esm-examples` です。アーカイブ済みの [`chirimen-oh/examples`](https://github.com/chirimen-oh/examples) ではありません。追加・修正の詳しい手順は [Pi Zero ESM Example ガイド](./examples/pizero-esm-examples.md) を見てください。

### chirimen-drivers

- リポジトリ: [chirimen-oh/chirimen-drivers](https://github.com/chirimen-oh/chirimen-drivers)
- 役割: I2C デバイスドライバ（npm: `chirimen` / `@chirimen/*`）
- 向いている変更: センサーやアクチュエータ向けドライバの追加・修正、ドライバ向けドキュメント
- コントリビュート手順: [Contributing Guidelines](https://chirimen.org/chirimen-drivers/CONTRIBUTING)

GPIO や I2C そのものの runtime 実装ではなく、個別デバイスを扱うドライバ本体の変更先です。

### node-web-gpio

- リポジトリ: [chirimen-oh/node-web-gpio](https://github.com/chirimen-oh/node-web-gpio)
- 役割: Node.js から Web GPIO 相当の API を使う runtime
- 向いている変更: GPIO アクセスそのものの不具合修正や API 実装の変更

個別センサーのロジックではなく、ピンの入出力など GPIO runtime を変えたいときに使います。

### node-web-i2c

- リポジトリ: [chirimen-oh/node-web-i2c](https://github.com/chirimen-oh/node-web-i2c)
- 役割: Node.js から Web I2C 相当の API を使う runtime
- 向いている変更: I2C アクセスそのものの不具合修正や API 実装の変更

個別デバイスのドライバではなく、I2C バスへのアクセス runtime を変えたいときに使います。

## 関連リポジトリ（参考）

初心者が混同しやすいものだけ挙げます。全部のカタログではありません。

| リポジトリ | いま分かっている役割 |
| --- | --- |
| [chirimen-lite](https://github.com/chirimen-oh/chirimen-lite) | Pi Zero 用 CHIRIMEN の OS イメージを作るツール。Example 本体ではない |
| [chirimen](https://github.com/chirimen-oh/chirimen) | Raspberry Pi 向け CHIRIMEN 環境。チュートリアル本文は `chirimen.org` |
| [chirimen-micro-bit](https://github.com/chirimen-oh/chirimen-micro-bit) | micro:bit 向け実装。チュートリアルは `chirimen.org` の `microbit/` にもある |
| [examples](https://github.com/chirimen-oh/examples) | archived。現行の Pi Zero ESM Example の変更先ではない |

## Needs confirmation

次の点は、公開 README だけでは断定できないため、推測で決めません。

- ブラウザ版 WebGPIO / WebI2C（archived の [`polyfills`](https://github.com/chirimen-oh/polyfills) や [`chirimen`](https://github.com/chirimen-oh/chirimen) 環境）の、現行の変更先
- micro:bit 向け Example / ドライバを [`chirimen.org`](https://github.com/chirimen-oh/chirimen.org) / [`chirimen-micro-bit`](https://github.com/chirimen-oh/chirimen-micro-bit) / [`chirimen-drivers`](https://github.com/chirimen-oh/chirimen-drivers) のどれに出すか
- npm パッケージ `chirimen` が `node-web-gpio` / `node-web-i2c` をどこまで再エクスポートしているか。アプリから `chirimen` を import して使うことと、runtime 本体の修正先は別問題として扱う

分からなければ、[Organization Discussions](https://github.com/orgs/chirimen-oh/discussions) で確認してください。

## 次に読む

- [Getting Started](./getting-started.md) — 貢献の種類と相談先
- [GitHub workflow](./github-workflow.md) — Fork から Pull Request までの進め方
- [Discussion / Issue / Pull Request](./discussions-issues-pull-requests.md) — 相談・報告・提案の使い分け
- [Pi Zero ESM Example](./examples/pizero-esm-examples.md) — Example の追加・修正手順
- [既存 contribution ドキュメントの棚卸し](./existing-contribution-docs.md) — 既存情報の重複・不足・要確認
