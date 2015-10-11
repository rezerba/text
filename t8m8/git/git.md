# git

- [gitとは](#p1)
- [gitの良いところ](#p2)
- [ローカルリポジトリとリモートリポジトリ](#p3)
- [ローカルブランチ、リモートブランチ、追跡ブランチ](#p3)
- [できること](#p5)
- [クライアント](#p6)
- [ホスティングサイト](#p7)

---

## <a id="p1"></a> gitとは
ギットと読む。  
分散型バージョン管理システム。

## <a id="p2"></a> gitの良いところ
一番はユーザが多いこと。  
分散型であるが故のメリットはいろいろある。  

## <a id="p3"></a> ローカルリポジトリとリモートリポジトリ 
ユーザの手元にあるリポジトリをローカルリポジトリ、共通で使用するサーバに設置されたリポジトリをリモートリポジトリという。  
ローカル環境内には、ワーキングツリー、インデックス、ローカルリポジトリがある。  
ワーキングツリーは実際に作業をしているディレクトリのこと。  
インデックスはローカルリポジトリに反映するファイルを入れる場所のこと。実態があるわけではない。インデックスを挟むことで必要なファイルだけを反映させることができる。  

## <a id="p4"></a> ローカルブランチ、リモートブランチ、追跡ブランチ
ローカルブランチはその名の通りローカルのブランチ。  
リモートブランチもその名の通りリモートのブランチ。  
追跡ブランチは、リモートブランチの状態を監視するローカルにあるブランチ。  
始めに作成されるmasterブランチの他にorigin/masterブランチというものがあり、これはリモートのmasterを見ている追跡ブランチ。

## <a id="p5"></a> できること

講習会では絵を描いたり、実際にいじりながら説明

- [init](#init)
- [add](#add)
- [commit](#commit)
- [push](#push)
- [clone](#clone)
- [fetch](#fetch)
- [branch](#branch)
- [checkout](#checkout)
- [merge](#merge)
- [pull](#pull)
- [diff](#diff)
- [log](#log)
- [reset](#reset)

他にもrebase、status、stash、config、update-index、ls-files、cherry-pickなどいろいろあるけど今回は省略。

---

### <a id="init"></a> init
リポジトリを作成する。  
gitの管理下とする空のディレクトリを作成し、そのディレクトリ内でinitすると中に.gitディレクトリが作成され、gitの管理下になる。  
このディレクトリ以下のディレクトリは全てgit管理下になる。
このディレクトリ内にファイルを置くだけではそのファイルはローカルリポジトリに反映できない。

```shell
$ mkdir /path/to/{repository_name}/ # gitプロジェクトのディレクトリを作成
$ cd /path/to/{repository_name}/    # 移動
$ git init                          # ローカルリポジトリ作成
```

### <a id="add"></a> add
ステージングとか言ったりする。  
ファイルをインデックスに追加する。  
インデックスに追加してもローカルリポジトリ内には反映されていない。

```shell
$ git add {file_name} # ファイル名を指定して追加
$ git add .           # 全てのファイルを追加
```

addはファイルの更新時に毎回行う必要がある。

### <a id="commit"></a> commit
インデックス内のファイルの変更をローカルリポジトリに反映させる。  
この時に、どのような変更を加えたかをコミットメッセージとして記述できる。というか記述するべき。  
変更前の状態は履歴として残る。

```shell
$ git commit - m {message}
```

### <a id="push"></a> push
ローカルリポジトリのコミット内容をリモートリポジトリに反映させる。  
ローカルリポジトリのコミット毎にpushする必要はなく、ある程度溜めてからでもできる。

```shell
$ git push origin master # origin(リモートリポジトリ)にローカルのmasterブランチの内容を反映
```

### <a id="clone"></a> clone
リモートリポジトリからローカルにコピーしてくる。  
```shell
$ git clone {url}
```

### <a id="fetch"></a> fetch
リモートリポジトリから情報を取得する。  
追跡ブランチを更新するだけ。
```shell
$ git fetch origin        # リモートリポジトリの変更を取得
$ git fetch origin master # リモートリポジトリの指定したブランチの変更を取得
$ git fetch --all         # リモートリポジトリの変更をすべて取得
```

### <a id="branch"></a> branch
ブランチ操作をする。

```shell
$ git branch                    # ローカルのブランチ一覧を表示
$ git branch {branch_name}      # ブランチを作成
$ git branch -r                 # リモートのブランチ一覧を表示
$ git branch -a                 # ローカルとリモートのブランチ一覧を表示

$ git branch -d {branch_name}   # ブランチを削除
$ git branch -m {branch_name}   # 現在のブランチ名を変更
```

### <a id="checkout"></a> checkout
ファイル、ブランチの状態を変更する。
```shell
$ git checkout {branch_name}    # ブランチを移動
$ git checkout {commit}         # 指定コミット時の状態にする
$ git checkout {commit} {file}  # 指定ファイルを指定コミット時の状態にする
```

### <a id="merge"></a> merge
マージ操作を行う。

```shell
$ git merge {branch_name} # 今いるブランチに指定ブランチをマージする
$ git merge -m {message} {branch_name} # マージメッセージをつけてマージ
$ git merge --no-ff {branch_name} # マージコミットを必ず行う
```

### <a id="pull"></a> pull
リモートリポジトリの内容をローカルリポジトリに反映させる。  
fetchとmergeの組み合わせ(pullを使わずに、fetch,mergeの使用を推奨する人もいる)。  
pull -rebaseとするとfetchとrebaseの組み合わせになる。  
コンフリクトした場合には知らせてくれるので、どちらを採用するか選択する。
```shell
$ git pull {repository_name}
```

### <a id="diff"></a> diff
差分を表示。

```shell
$ git diff                    # ワークツリーとインデックスの差分を表示
$ git diff HEAD               # ワークツリーとHEAD(今いるブランチの最新のコミット)の差分を表示
$ git diff --staged(--cached) # インデックスとHEADの差分を表示
$ git diff --stat             # 差分統計を表示
```

### <a id="log"></a> log
ログを確認する。

```shell
$ git log           # ログを表示
$ git log --oneline # ログを簡潔に表示
$ git log --stat    # 変更箇所を詳しく表示
```

### <a id="reset"></a> reset
ワークツリー、インデックス、HEADの内容を元に戻す

```shell
$ git reset (--mixed) HEAD # addを取り消す
$ git reset --hard HEAD^   # コミットを取り消す
```

## <a id="p6"></a> クライアント

- [SourceTree](https://ja.atlassian.com/software/sourcetree/overview)
- [GitHub Desktop](https://desktop.github.com)

## <a id="p7"></a> ホスティングサイト

- [GitHub](https://github.com)
	- 有名どころ
- [Bitbucket](https://bitbucket.org)
	- 無料でプライベートリポジトリを無制限に作れて良い
