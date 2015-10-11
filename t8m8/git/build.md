# 環境構築
OS毎にいくつかのインストール方法があるので、好きな方法で入れる。  

- [Windows](#p1)
- [Mac](#p2)
- [Linux](#p3)
- [インストール後](#p4)
- [GUIを使えるようにする](#p5)

---

## <a id="p1"></a> Windows
- [Git for Windows](https://git-for-windows.github.io)からインストーラーをダウンロードして、インストール
	- Bash OnlyがデフォルトなのでCommand Promptで使えるように選択しておいた方が良いらしい
	- その他設定はお好みで 
- [GitHub for Windows](http://windows.github.com)からインストーラーをダウンロードして、インストール

## <a id="p2"></a> Mac
- Xcode Command Line Toolsをインストール
- [Git](http://git-scm.com/downloads)からインストーラーをダウンロードして、インストール
- Homebrewを使用
```shell
$ brew install git
```

## <a id="p3"></a> Linux
自分のディストリビューションのパッケージ管理システムを使用してインストール。
#### Debian/Ubuntu
```shell
$ apt-get install git
```
#### Fedora
```shell
$ yum install git
```
#### Gentoo
```shell
$ emerge --ask --verbose dev-vcs/git
```
#### Arch Linux
```shell
$ pacman -S git
```
#### openSUSE
```shell
$ zypper install git
```
#### FreeBSD
```shell
$ cd /usr/ports/devel/git
$ make install
```
#### Solaris 11 Express
```shell
$ pkg install developer/versioning/git
```
#### OpenBSD
```shell
$ pkg_add git
```

## <a id="p4"></a> インストール後
コマンドライン上で以下を実行し、正しくversionが表示されればインストール完了。
```shell
$ git --version
```

#### ユーザ情報を設定
```shell
$ git config --global user.name "{user_name}"   # ユーザ名を登録
$ git config --global user.email "{email}"      # メールアドレスを登録
$ git config --global color.ui auto             # 出力をカラーリング(任意)

$ git config --list                             # 現在の設定を確認
```

##<a id="p5"></a> GUIを使えるようにする
gitをインストールするとgit gui/gitkというGUIツールが付いてくるが、これを使うくらいなら以下のクライアントを使ったほうが良いと思う。

- [SourceTree](https://ja.atlassian.com/software/sourcetree/overview)
- [GitHub Desktop](https://desktop.github.com)
- 他にもいろいろあるっぽい


