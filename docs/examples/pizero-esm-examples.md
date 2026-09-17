# Pi Zero ESM Example

`chirimen-oh/chirimen.org` の `pizero/src/esm-examples` にある Example を追加・修正するときの案内です。

このページは既存の公開情報と実装から読み取れることを整理したものです。新しい運用ルールは定めません。対象リポジトリに `CONTRIBUTING.md` がある場合は、そちらの手順を優先してください。

このリポジトリは現在、コントリビュート方法を整理するための Draft / Incubation です。内容が固まったら、chirimen-oh Organization への移管や各リポジトリへの統合を検討します。

最初の版では、完全な手順書ではなく、確認できたことと未確認事項を分けて書きます。

## 対象

- リポジトリ: [`chirimen-oh/chirimen.org`](https://github.com/chirimen-oh/chirimen.org)
- ディレクトリ: [`pizero/src/esm-examples`](https://github.com/chirimen-oh/chirimen.org/tree/master/pizero/src/esm-examples)
- 一覧（CSV）: [`index_examples.csv`](https://github.com/chirimen-oh/chirimen.org/blob/master/pizero/src/esm-examples/index_examples.csv)
- 一覧（Web）: [https://chirimen.org/pizero/esm-examples/](https://chirimen.org/pizero/esm-examples/)
- コントリビュート手順: [`CONTRIBUTING.md`](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md)

アーカイブ済みの [`chirimen-oh/examples`](https://github.com/chirimen-oh/examples) は、現行の変更先ではありません。どのリポジトリを見るかは [Where to Contribute](../where-to-contribute.md) を見てください。

ドライバ本体（`@chirimen/*`）を追加・修正したいときは、このディレクトリではなく [`chirimen-drivers`](https://github.com/chirimen-oh/chirimen-drivers) です。手順は [Contributing Guidelines](https://chirimen.org/chirimen-drivers/CONTRIBUTING) にあります。

## 全体の流れ

[`CONTRIBUTING.md`](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md) は、作業前に Issue を立てる手順を書いています。Fork から Pull Request までの一般的な操作は [GitHub workflow](../github-workflow.md) を見てください。

```text
chirimen.org を Fork
        ↓
作業前に Issue を立てる（chirimen.org の手順）
        ↓
pizero/src/esm-examples/<id>/ を追加または修正
        ↓
index_examples.csv に登録
        ↓
必要なら _data/partslist.csv と画像
        ↓
実機または既存手順で確認
        ↓
 Pull Request
```

## 参考にするとよい既存 Example

近いものをコピー起点にすると、構成を推測しやすくなります。

| 種類 | ディレクトリ | 向いているとき |
| --- | --- | --- |
| GPIO | [`hello-real-world`](https://github.com/chirimen-oh/chirimen.org/tree/master/pizero/src/esm-examples/hello-real-world) | LED やモーターなど GPIO 出力 |
| I2C（従来の構成） | [`adt7410`](https://github.com/chirimen-oh/chirimen.org/tree/master/pizero/src/esm-examples/adt7410) | 温度センサーなど I2C デバイス |
| I2C（新しい最小構成） | [`sths34pf80`](https://github.com/chirimen-oh/chirimen.org/tree/master/pizero/src/esm-examples/sths34pf80) | 最近追加された Example。[PR #195](https://github.com/chirimen-oh/chirimen.org/pull/195) |
| Remote | [`remote_adt7410`](https://github.com/chirimen-oh/chirimen.org/tree/master/pizero/src/esm-examples/remote_adt7410) | Pi Zero 側と PC/スマホ側を組み合わせる |

自分のプログラム用ディレクトリの作り方は [`howToDev`](https://github.com/chirimen-oh/chirimen.org/tree/master/pizero/src/esm-examples/howToDev) にあります。Examples 集そのものへの追加手順ではありません。

## Known

公開されている README と既存ファイルから確認できることです。必須ルールとして新たに定めているわけではありません。

### ディレクトリ命名

ディレクトリ名は、一覧 CSV の ID と一致させます。

- I2C デバイス: 型番の小文字が多い（例: `adt7410`, `sht30`, `sths34pf80`）
- GPIO: 用途が分かる名前（例: `hello-real-world`, `gpio-inout`）
- 遠隔操作: `remote_` 接頭辞（例: `remote_adt7410`）

kebab-case（`gpio-inout`）と underscore（`sht30_led`）が混在しています。どちらが正しいかは Needs confirmation です。

### 必須に近いファイル

トップの [`readme.md`](https://github.com/chirimen-oh/chirimen.org/blob/master/pizero/src/esm-examples/readme.md) は、各 Example の構成を次のように案内しています。

| ファイル | 内容 |
| --- | --- |
| `main.js` | プログラム本体 |
| `package.json` | 使用するライブラリ（ドライバ）の一覧 |
| `readme.md` | 配線図・ドライバのインストール方法・サンプルコードの解説 |

通常の Example に `index.html` はありません。Pi Zero 上の Node.js で `main.js` を実行する構成です。HTML は Remote Example の PC 側（`pc/index.html`）にあります。

### HTML / JavaScript / ESM

通常 Example の JavaScript は ESM です。

- `package.json` に `"type": "module"` がある
- `import` 文を使う
- top-level await を使う（`async function main()` で包まない例が多い）

GPIO の例:

```js
import { requestGPIOAccess } from "node-web-gpio";
```

I2C の例:

```js
import { requestI2CAccess } from "node-web-i2c";
import ADT7410 from "@chirimen/adt7410";
```

Remote Example の PC 側は、だいたい次の構成です。

- `pc/index.html`
- `pc/pc.js`
- 必要に応じて `pc/sandbox.config.json`（CodeSandbox 用）

Pi Zero 側の `main.js` はセンサー値を RelayServer 経由で送り、PC 側のブラウザが受信して表示します。

### chirimen-drivers の利用方法

CHIRIMEN のデバイスドライバは [`chirimen-drivers`](https://github.com/chirimen-oh/chirimen-drivers) で開発され、npm に公開されています。Examples 集のトップ README は、使い方を 2 通り案内しています。

**1. デバイスごとの個別パッケージ（この Examples 集の方式）**

```sh
npm i node-web-i2c @chirimen/adt7410
```

```js
import { requestI2CAccess } from "node-web-i2c";
import ADT7410 from "@chirimen/adt7410";
```

**2. 全ドライバ入りの `chirimen` パッケージ**

```js
import { requestI2CAccess, ADT7410 } from "chirimen";
```

新しいドライバが必要なら、先に [`chirimen-drivers`](https://github.com/chirimen-oh/chirimen-drivers) 側の手順を見てください。手元の未公開ドライバを試す方法は [`howToDev`](https://github.com/chirimen-oh/chirimen.org/blob/master/pizero/src/esm-examples/howToDev/README.md) にあります。

### 対象デバイスの記述

I2C デバイスは、コンストラクタにポートとスレーブアドレスを渡す例が多いです。

```js
const i2cAccess = await requestI2CAccess();
const i2cPort = i2cAccess.ports.get(1);
const adt7410 = new ADT7410(i2cPort, 0x48);
await adt7410.init();
```

トップ README は、配線後の確認に次のコマンドを案内しています。

```sh
i2cdetect -y 1
```

- I2C の配線は基本 4 本（VCC・GND・SDA・SCL）。電源は 3.3V が多い
- 同じ型番でも基板によってアドレスが違うことがある
- GPIO はポート番号を指定する（例: `hello-real-world` は PORT 26）

### 回路図・配線情報

各 Example の `readme.md` に配線図画像を載せる例が多いです。

- 新しい例では `schematic.png` が多い（例: `sths34pf80`）
- 以前の例では `PiZero_ADT7410.png` のような名前もある
- Fritzing ファイル（`.fzz` / `.fzpz`）や SVG を同梱する例もある

一覧ページの「回路図」リンクは、特定の画像ファイルではなく、そのディレクトリの GitHub `#readme` を開きます。ファイル名の統一は Needs confirmation です。

### README の必要性

トップ README は `readme.md` を構成の一部として案内しています。最近追加された [`sths34pf80/readme.md`](https://github.com/chirimen-oh/chirimen.org/blob/master/pizero/src/esm-examples/sths34pf80/readme.md) には、次のような項目があります。

- 何をするサンプルか
- 配線（ピン対応表）
- 配線図
- ドライバのインストール
- ファイル説明（Fritzing など）
- 実行方法
- サンプルコード
- 実行結果

必須項目の公式リストは見つかっていません。近い既存 Example に合わせるのが安全です。

### Example 一覧への登録

[`index_examples.csv`](https://github.com/chirimen-oh/chirimen.org/blob/master/pizero/src/esm-examples/index_examples.csv) に 1 行追加すると、[一覧ページ](https://chirimen.org/pizero/esm-examples/) に出ます。カテゴリは次の 3 つです。

- `GPIO`
- `I2C`
- `REMOTE`

行の形式は `id,タイトル,概要` です。`id` はディレクトリ名と一致させます。

```csv
sths34pf80,赤外線温度センサ,I2CのSTHS34PF80で測った対象物温度と周辺温度を表示
```

[PR #195](https://github.com/chirimen-oh/chirimen.org/pull/195) では、同じカテゴリ内のアルファベット順付近に挿入しています。

### 対応ハードウェアの記載

最近の Example 追加 PR では、次も同時に更新していることがあります。

- [`_data/partslist.csv`](https://github.com/chirimen-oh/chirimen.org/blob/master/_data/partslist.csv) — デバイス情報の一覧
- `partsImgs/` — 部品画像

`partslist.csv` の `piZeroサンプルコードURL` 列は、一覧ページのアンカー（例: `https://chirimen.org/pizero/esm-examples/#I2C_sths34pf80`）を指すことがあります。Example 追加と同時に必ず更新するかは Needs confirmation です。

### 実機での動作確認

トップ README の実行手順です。

1. 各ディレクトリの `readme.md` を見て配線する
2. Raspberry Pi Zero にログインし、ライブラリがプリインストールされている `~/myApp` に `main.js` をコピーする
3. `node main.js` で実行する（停止は `Ctrl+C`）

I2C では、先に `i2cdetect -y 1` でデバイスが見えるかも確認します。サイト上の一覧や説明を確認するときは、[`CONTRIBUTING.md`](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md) のローカル起動（`bundle exec jekyll serve`）を使います。

Remote Example は、Pi Zero 側で `node main.js`、PC/スマホ側で `pc/` の webApp を動かします。一覧の「CSB EDIT」から CodeSandbox でも開けます。

マージ前に実機確認が必須かどうかは、公開手順からは断定できません。

### Pull Request に記載する内容

[`chirimen.org` の CONTRIBUTING.md](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md) は、作業前の Issue 作成とローカル起動を求めています。これは CHIRIMEN 全体の共通ルールではなく、そのリポジトリの手順です。

最近の追加 PR（例: [PR #195](https://github.com/chirimen-oh/chirimen.org/pull/195)）では、次を書いています。

- 追加したディレクトリとファイル
- 使ったドライバと I2C アドレス
- サンプルが何をするか
- `index_examples.csv` への追記

一般的な PR の作り方は [GitHub workflow](../github-workflow.md) を見てください。

## Needs confirmation

次の点は、公開 README だけでは断定できないため、推測で決めません。

- `package.json` の形。古い例は全ドライバ入りの巨大なコピー、新しい例（`sths34pf80`）と Remote は使うパッケージだけを書いている。どちらが推奨かは未確認
- 回路図のファイル名を `schematic.png` に統一する必要があるか
- `_data/partslist.csv` と `partsImgs/` を Example 追加と同時に必ず更新するか
- 通常 Example を追加するとき、対応する `remote_*` も同時に追加すべきか
- マージ前に実機での動作確認が必須か
- ディレクトリ名の kebab-case と underscore の使い分け

分からなければ、[Organization Discussions](https://github.com/orgs/chirimen-oh/discussions) か、[`chirimen.org` の Issues](https://github.com/chirimen-oh/chirimen.org/issues) で確認してください。

## Unknown

現状のばらつきとして残します。このガイドでは正しい形を決めません。

- [`ADT7410_`](https://github.com/chirimen-oh/chirimen.org/tree/master/pizero/src/esm-examples/ADT7410_) は `readme.md` がなく、現行の `adt7410` と重複しているように見える
- `max30102` / `i2c1602lcd` / `serial_gps` など、`package.json` や `readme.md` が欠けている例がある
- Examples 集トップの README は、[chirimen-drivers の node-examples](https://github.com/chirimen-oh/chirimen-drivers/tree/master/node-examples) を CommonJS 版として案内している。当該ディレクトリは [chirimen-drivers#462](https://github.com/chirimen-oh/chirimen-drivers/pull/462) で削除済みのため、記述が古い可能性がある

## 初心者が次に確認すること

1. 変更先は `chirimen.org` の `pizero/src/esm-examples` か。archived の `chirimen-oh/examples` ではない
2. 近い既存 Example をコピー起点にできないか
3. [`CONTRIBUTING.md`](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md) を先に読んだか。作業前の Issue 作成が書かれている
4. ドライバが無い、またはドライバ自体を直したい場合は [`chirimen-drivers`](https://github.com/chirimen-oh/chirimen-drivers) か
5. 迷ったら [Organization Discussions](https://github.com/orgs/chirimen-oh/discussions) に書いてよいか

判断できなければ、Discussion からで問題ありません。既存のメンテナーに個別で聞かなくても、コミュニティで相談できます。

## 次に読む

- [Getting Started](../getting-started.md) — 貢献の種類と相談先
- [Where to Contribute](../where-to-contribute.md) — どのリポジトリを変更すればよいか
- [GitHub workflow](../github-workflow.md) — Fork から Pull Request までの進め方
- [Discussion / Issue / Pull Request](../discussions-issues-pull-requests.md) — 相談・報告・提案の使い分け
