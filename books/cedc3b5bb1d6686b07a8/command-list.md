---
title: "開発必ず使うコマンドを叩く"
---

Gitにはたくさんのコマンドとオプションがありますが、その中でも開発で必ず使うコマンドを紹介するのがこのチャプターになります
開発で必ず使うコマンドだけでも人によってはたくさん出てくると思うので、以下に焦点を絞っています

* ローカルで完結するコマンド
  * リモートまで影響があるものは後ほど紹介します
* ファイルやGitコマンドの操作時にミスがない前提
  * ミスってしまったときに使えるコマンドも後ほど紹介します

# `git status`

まずは最初のチャプターで動作確認で使ったコマンドです
これは、**今のリポジトリの状態を表示する**コマンドです
具体的には以下の情報が見られます

1. Gitにまだ管理されていないファイルで、明示的に管理除外対象にしていないファイルの一覧
2. 何らかの操作が行われたファイルの一覧
3. `git add`されているが、まだコミットされていないファイルの一覧

この内、1番目はサクッと確認することができるので、これを確認してみます

:::message
2番目、3番目はそれぞれ`git add`、`git commit`というコマンドを知る必要があるので、そこで説明します
:::

最初のチャプターで作成したリポジトリで`git status`を叩くと↓のようになりました

```shell
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

このディレクトリに好きなファイルを追加してみます
例えば、`git_status.txt`を追加してから、`git status`を叩きます

```shell
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        git_status.txt

nothing to commit (create/copy files and use "git add" to track)
```

ディレクトリに何もない状態と比較して`Untracked files`から`git_status.txt`までの情報が追加されています
ここに、Gitにまだ管理されていないファイルで、明示的に管理除外対象にしていないファイルの一覧が表示されます

# `git add filename`

`git status`でリポジトリの状態が確認できたところで、次のコマンド`git add filename`です

| コマンド                             | 内容                            |
| -------------------------------- | ----------------------------- |
|                      | 前回コミット分から差分があるファイルを表示する       |
| `git add filename`               | filenameのファイル、ディレクトリ配下のファイルをステージングする |
| `git commit -m 'commit message'` | ステージングしたファイルをcommit messageでコミットする |
| `git push origin branch-name`    | リモートリポジトリoriginにブランチbranch-nameを反映する |
| `git clone remote-repository`    | remote-repositoryのリポジトリをローカルにダウンロードする |
