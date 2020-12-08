---
title: "開発で必ず使うコマンドを叩く(リモート編)"
---

無事にリモートリポジトリが作成できたので、ここからは実際にローカルからリモートに影響を与えるコマンドを実行していきます
ここでは、「開発で必ず使うコマンドを叩く(ローカル編)」と「リモートリポジトリを作成する」で作ったリポジトリを前提にしているので、それらの章をまだ見ていない方は先にそちらを見ると良いです
なお、「開発で必ず使うコマンドを叩く(ローカル編)」で作ったリポジトリをローカルリポジトリ、「リモートリポジトリを作成する」で作ったリポジトリをリモートリポジトリと呼称します

# `git remote add <name> <repository-url>`

ローカルリポジトリとリモートリポジトリをそれぞれで作成したので、それぞれのリポジトリが赤の他人です
まずは、この2つのリポジトリを関連付けます

今までと比べて、コマンドが長めなので、箇条書きでそれぞれを簡単に説明します
ただし、`git`は省略します

* `remote`
  * リモートに関するコマンドです
  * ローカルリポジトリにどのリモートリポジトリが登録されているか、もしくはそれらの設定の変更などができます
* `add`
  * ローカルリポジトリにリモートリポジトリを追加します
* `<name>`
  * 登録名を設定します
  * 最初は大抵`origin`が採用されます(理由は後述)
  * `<name>`さえ違えば、何個でもリモートリポジトリを設定することができます
* `<repository-url>`
  * リモートリポジトリのURLを設定します

なので、例えば`git remote add origin https://hogehoge.com/repository`というコマンドを実行すると、「`origin`という名前で`https://hogehoge.com/repository`をリモートリポジトリとして登録する」という意味になります
`<repository-url>`の具体的な値は`https://github.com/<Username>/test-upload-local-repository`の「Quick setup — if you’ve done this kind of thing before」という項目にあります
今回は`git remote add origin https://github.com/<Username>/test-upload-local-repository.git`というコマンドを実行することになります

# `git remote -v`

`git remote add <name> <repository-url>`が無事に実行されたか確認します
無事に実行されたら、リモートリポジトリが追加されていることになります
ローカルリポジトリに登録されたリモートリポジトリを確認するには、`git remote -v`です
`-v`のオプションを付けると、リモートリポジトリの詳細を見ることができます
実際に実行すると、

```shell
git remote -v
origin  https://github.com/LunaChevalier/test-upload-local-repository.git (fetch)
origin  https://github.com/LunaChevalier/test-upload-local-repository.git (push)
```

となるはずです(`LunaChevalier`の部分は`<Username>`になるので、ここだけアカウントで異なります)
最後に`fetch`と`push`がついていますが、これも後ほど説明します(今はこうなるんだーくらいののりでOKです)
