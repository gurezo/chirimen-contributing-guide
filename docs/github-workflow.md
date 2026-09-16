# GitHub workflow

GitHub や OSS へのコントリビュート経験が少ない人向けに、Fork から Pull Request までの一般的な進め方を説明します。

このページは一般的な GitHub 操作の案内です。新しい運用ルールは定めません。対象リポジトリに `CONTRIBUTING.md` がある場合は、そちらの手順を優先してください。

このリポジトリは現在、コントリビュート方法を整理するための Draft / Incubation です。内容が固まったら、chirimen-oh Organization への移管や各リポジトリへの統合を検討します。

## 全体の流れ

1. 対象リポジトリを確認する
2. Issue を確認する
3. 必要に応じて Discussion / Issue で相談する
4. Repository を Fork する
5. clone する
6. 作業ブランチを作成する
7. 変更する
8. テスト・動作確認を行う
9. commit / push する
10. Pull Request を作成する
11. Review に対応する

## 対象リポジトリを確認する

何を変えたいときにどのリポジトリを見るかは、[Where to Contribute](./where-to-contribute.md) を見てください。

対象リポジトリが分からないときは、まず [chirimen-oh Organization の Discussions](https://github.com/orgs/chirimen-oh/discussions) に書いてください。

対象リポジトリが決まったら、そのリポジトリに `CONTRIBUTING.md` があるかを確認します。あれば、このガイドより先に読んでください。リポジトリごとのビルド手順や、作業前の Issue 作成の要否は、そこで案内されていることがあります。

例: [`chirimen.org` の CONTRIBUTING.md](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md) は、作業前に Issue を立てる手順を書いています。これは CHIRIMEN 全体の共通ルールではなく、そのリポジトリの手順です。

## Issue を確認する

同じ内容の Issue が既にないかを、対象リポジトリの Issues で確認してください。既存 Issue があれば、新しい Issue を増やさず、そちらで作業できます。

typo やリンク切れなど、小さな修正では Issue を必須としない場合があります。一方で、対象リポジトリが「作業前に Issue を立てる」と書いているときは、その手順に従ってください。

Discussion / Issue / Pull Request の使い分けは [専用ガイド](./discussions-issues-pull-requests.md) を見てください。

## 必要に応じて相談する

変更内容がまだ固まっていないときや、進め方に迷うときは、先に相談してください。

迷ったら、まず [chirimen-oh Organization の Discussions](https://github.com/orgs/chirimen-oh/discussions) に書いてください。対象リポジトリが分かっている場合は、そのリポジトリの Issue でも構いません。

判断できなければ、Discussion からで問題ありません。

## Fork する

対象リポジトリの GitHub ページを開き、右上の **Fork** を押します。自分のアカウント配下にコピーが作られます。以降の clone と作業は、この Fork 先に対して行います。

## clone する

Fork したリポジトリを、自分の PC にコピーします。HTTPS の例です。`YOUR-USERNAME` と `REPO` は、実際のアカウント名とリポジトリ名に置き換えてください。

```sh
git clone https://github.com/YOUR-USERNAME/REPO.git
cd REPO
```

オリジナル（upstream）ではなく、自分の Fork を clone してください。

## 作業ブランチを作成する

`main` や `master` など、デフォルトブランチで直接作業しないでください。作業内容が分かる名前のブランチを作ります。

```sh
git checkout -b docs/fix-typo
```

ブランチ名の付け方はリポジトリによって異なります。このガイドリポジトリでは Conventional Commits に近い名前を使うことがありますが、それを CHIRIMEN 全体の必須ルールにはしません。対象リポジトリの `CONTRIBUTING.md` に指定があれば、それに従ってください。

## 変更する

目的に対して小さく、レビューしやすい差分にしてください。関係のない整形やリネームは混ぜない方が分かりやすくなります。

ビルド、ローカル起動、依存関係の入れ方など、リポジトリ固有の手順は各 `CONTRIBUTING.md` を見てください。例えば `chirimen.org` では、ローカルでサイトを起動する手順が [CONTRIBUTING.md](https://github.com/chirimen-oh/chirimen.org/blob/master/CONTRIBUTING.md) に書かれています。

## テスト・動作確認を行う

提出前に、自分の変更が意図どおりかを確認してください。

- ドキュメントの修正: リンク切れがないか、説明が通るか
- サイトやチュートリアル: 対象リポジトリの手順でローカル表示を確認する
- コードの変更: 対象リポジトリが案内しているテストや動作確認を行う

確認方法が分からなければ、`CONTRIBUTING.md` を見るか、Discussion で聞いてください。

## commit / push する

変更を記録し、自分の Fork へ送ります。

```sh
git add .
git commit -m "メッセージ"
git push -u origin HEAD
```

コミットメッセージは、何をなぜ変えたかが分かれば十分です。このガイドリポジトリでは Conventional Commits（例: `docs: add github workflow guide`）を使います。他の CHIRIMEN リポジトリまで同じ形式を必須にはしません。対象リポジトリの慣習があれば、それに合わせてください。

## Pull Request を作成する

GitHub で Fork したリポジトリを開き、**Compare & pull request** または **Contribute** から Pull Request を作ります。

- base: オリジナルリポジトリのデフォルトブランチ（多くの場合 `main` または `master`）
- compare: 自分の Fork の作業ブランチ

説明には「何を変えたか」と「なぜ必要か」を書いてください。関連する Issue があればリンクします。テンプレートがあるリポジトリでは、その項目を埋めてください。

## Review に対応する

レビューコメントが付いたら、指摘に沿って同じ作業ブランチを直します。追加の commit を push すれば、開いている Pull Request に自動で反映されます。履歴を書き換える force push は、求められない限り不要です。

修正が反映されたら、レビューした人に分かるように返信してください。承認後のマージは、通常はメンテナーが行います。

## 次に読む

- [Getting Started](./getting-started.md) — 貢献の種類と相談先
- [Where to Contribute](./where-to-contribute.md) — どのリポジトリを変更すればよいか
- [Discussion / Issue / Pull Request](./discussions-issues-pull-requests.md) — 相談・報告・提案の使い分け
- [Pi Zero ESM Example](./examples/pizero-esm-examples.md) — Example の追加・修正手順
