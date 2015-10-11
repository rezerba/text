# GitHub

- [GitHubとは](#p1)
- [ユーザ登録](#p2)
- [SSH接続できるようにするには](#p3)
- [GitHub Education](#p4)
- [GitHubにある機能](#p5)
- [Gist](#p6)
- [Explore GitHub](#p7)
- [Classroom for GitHub](#p8)

---

## <a id="p1"></a> GitHubとは
- gitのホスティングサイト
- リモートリポジトリを作成できる

## <a id="p2"></a> ユーザ登録
[GitHub](https://github.com)にアクセスして、ユーザ名・メールアドレス・パスワードを入力して登録  

## <a id="p3"></a> SSH接続できるようにするには
1. 秘密鍵と公開鍵を作成
2. 公開鍵をGitHubに登録
3. 接続確認

#### 秘密鍵と公開鍵を作成
ここは鍵がすでにある人はスルーしてok  

```shell
$ cd ~/.ssh
$ ssh-keygen -t rsa -C {mail_address}
```
作成されたid_rsaが秘密鍵、id_rsa.pubが公開鍵

#### 公開鍵をGitHubに登録
id_rsa.pubの中身をコピーして、ログインした状態で[ココ](https://github.com/settings/ssh)から登録。  
Titleはどのマシンでの鍵かわかるようにしておくと良い。

#### 接続確認
```shell
$ ssh -T git@github.com
```
何か言われると思うのでyesにする。
```
Hi t8m8! You've successfully authenticated, but GitHub does not provide shell access.
```
みたいに言われたらok

## <a id="p4"></a> GitHub Education
[GitHub Education](https://education.github.com/pack)  
登録するとプライベートリポジトリを5個まで無料で作れてお得(2年間)。  
学生のみ大学のメールアカウントを使用して申請することができて、英語で適当な志望理由を書けば1週間くらいで申請が通る。  
大学のサークルや研究室で作った団体アカウントで申請すると、プライベートリポジトリを10個まで無料で作れる。しかも期限がない。使いたい人は申請してくれー。

## <a id="p5"></a> GitHubにある機能

#### Star
いわゆるお気に入り機能。

#### Watch
Watchにしておくと、コミットなどがあったときにメールで通知が来るようになる。

#### issue
共有したい問題を書き込むことができる。

#### fork
cloneと似ているがforkには開発に貢献するという意図が含まれる。  
forkは開発者へ通知が送られる。

#### pull request
「こんな機能追加したよ！」「このバグ修正しといたぜ！」のように何らかの貢献を反映してもらえるように依頼すること。  
基本的にfork→pull requestという流れになる。

## <a id="p6"></a> Gist
[Gist](https://gist.github.com)  
コードの断片のみを管理できる。  
普通のリポジトリと同様にバージョン管理が可能。  

## <a id="p7"></a> Explore GitHub
[Explore GitHub](https://github.com/explore)  
最近の面白いリポジトリがまとめられている。  

#### [Showcases](https://github.com/showcases)  
ジャンルごとにまとまっている。

#### [Trending repositories](https://github.com/trending)  
期間や言語を指定して見ることができる。

#### [Stars](https://github.com/stars) 
フォローをしている人が直近でスターしたリポジトリが見れる。

## <a id="p8"></a> Classroom for GitHub
[Classroom for GitHub](https://classroom.github.com)  
最近できたプログラミング教育支援ツール。  
プライベートなURLで課題の配布、生徒からの課題提出とかできるらしい。  
教員向け(?)
