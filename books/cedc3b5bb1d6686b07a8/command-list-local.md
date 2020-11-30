---
title: "開発で必ず使うコマンドを叩く(ローカル編)"
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
2. `git add`されているが、まだコミットされていないファイルの一覧
3. 何らかの操作(編集、削除等)が行われた、Gitの管理対象になっているファイルの一覧

この内、1番目はサクッと確認することができるので、これを確認してみます

:::message
2番目、3番目は`git add`、`git commit`というコマンドを知る必要があるので、そこで説明します
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
一覧が表示されるので、複数ファイルが有るとすべて表示されます
`git_status2.txt`を追加してから、`git status`を叩きます

```shell
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        git_status.txt
        git_status2.txt

nothing to commit (create/copy files and use "git add" to track)
```

`git_status2.txt`も表示されるようになりました

# `git add filename`

`git status`でリポジトリの状態が確認できたところで、次のコマンド`git add filename`です
これは、**次回コミット時に対象とするファイル(filename)を設定する**コマンドになります

早速、`git_status.txt`を次回コミット時に対象とするファイルに設定してみます
`git add git_status.txt`で設定できます、実行してみましょう
・・・コマンドを実行しても何も表示されません、問題ないのでしょうか?と思う方もいるはず
ここで、`git status`で紹介した、2番目の効果

> `git add`されているが、まだコミットされていないファイルの一覧

を利用します、`git status`を実行します

```shell
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   git_status.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        git_status.txt

nothing to commit (create/copy files and use "git add" to track)
```

`Untracked files`にいた`git_status.txt`が`Changes to be committed`に移動しました
こうなっていれば、`git add`は実行に成功しています(つまり、何も表示されないのが仕様です)
ちなみに、存在しないファイルを指定すると、`fatal pathspec 'filename' did not match any files`と言った、ファイルが存在しないとエラーを表示します

# `git commit -m 'commit message'`

`git add`でコミットするファイルを設定できたら、実際に`git commit -m 'commit message'`でコミットします
これは、**コミットメッセージ(commit message)でコミットする**コマンドになります

聞き慣れないコミット、コミットメッセージが出てきたので、それぞれについて説明します
**コミット**とは、ファイル何らかの操作(変更や追加、削除など)を保存することです
例えるなら、ゲームのセーブになります
なお、コミットするときは、**コミットメッセージ**と呼ばれる、コミット時にそのコミットと一緒に添えるメッセージを書く必要があります
何でも書くことができますが、そのコミットでどういう修正、改修を行ったのかを書くことが推奨されています

:::message
コミットメッセージの例については後ほど書きます
:::

まずは、推奨されていることを無視して、`git commit -m '初めてのコミット'`でコミットします
以下のような情報が表示されたら成功です

```shell
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 git_status.txt
```

なお、`100644`はコミットIDという、コミット時にGitが作る英数字で構成された識別番号なので、ここだけ異なるはずです
