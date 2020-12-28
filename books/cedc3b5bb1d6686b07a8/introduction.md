---
title: "環境を作る"
---

これから、実際にコマンドを実行するのですが、環境が無いと実行できません
まずは環境構築をします
なお、ここではWindows版の環境構築について説明します

# インストール

Gitをインストールしていきますが、方法はいくつかあります
ここでは一番最短になるであろう[scoop](https://scoop.sh/)という、CLIで様々なツールをインストールできるツールを使います

:::message
すでにインストールしていたり、別の方法でインストールする方は次の[Gitを使うディレクトリを用意する](#gitを使うディレクトリを用意する)
:::

## scoopのインストール

PowerShellコンソールで以下のコマンドを実行します

```shell
Set-ExecutionPolicy RemoteSigned -scope CurrentUser; iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
```

以下のコマンドを実行して、バージョン情報が出てきたら成功です

```shell
scoop -v
```

## Gitのインストール

続いてGitをインストールします
以下のコマンドを実行します

```shell
scoop install git
```

以下のコマンドを実行して、バージョン情報が出てきたら成功です

```shell
git --version
```

# Gitを使うディレクトリを用意する

これでGitはインストールされましたが、Gitを十分使える状態ではありません
試しに以下のGitコマンドを実行してみましょう

```shell
git status
```

`fatal: not a git repository (or any of the parent directories): .git`というエラーが表示されるはずです

Gitを使うようにするには、「リポジトリ」というファイルやディレクトリの状態を管理する場所が必要になります
さっきのエラーは実行したときのカレントディレクトリが「リポジトリ」ではなかったのでエラーになりました

それでは、そのリポジトリを作成します
どこでもOKなので、リポジトリを作成するディレクトリを用意します
ディレクトリを用意したら、カレントディレクトリを用意したディレクトリにして、以下のコマンドを実行します

```shell
git init
```

ディレクトリ直下に`.git`というディレクトリがあれば、カレントディレクトリがリポジトリになりました
さっきのGitコマンドを実行してみましょう

```shell
git status
```

今度はエラーにならず、以下のような情報が表示されたらOKです

```shell
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```
