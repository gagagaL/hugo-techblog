+++  
draft = false  
image = ""  
showonlyimage = false  
title = "【備忘録】LinuxとMacでのdateコマンドの差異について"  
date = "2021-06-30T22:12:03.284Z"  
description = "dateコマンドのオプション使用可能かどうかの差異"  
tags = ["Mac", "Linux", "コマンド"]  
+++    

  

Linux上にて、特定の日付での挙動を調べるために

```
date -s "12/31 12:00 2021"
```

というコマンドを実行して調査指定していました。  
これをMacのローカル環境でも調べようと思って同じコマンドを叩くと

```
date -s "12/31 12:00 2021"

date: illegal option -- s
usage: date [-jnRu] [-d dst] [-r seconds] [-t west] [-v[+|-]val[ymwdHMS]] ...
            [-f fmt date | [[[mm]dd]HH]MM[[cc]yy][.ss]] [+format]
```

と怒られました。
「"s"なんてオプションは無え！」ということらしいです。


### 何でこんなことになるのか


普段からはそこまで差を感じないので「なんとなく同じなんじゃないの」と思い込んでしまっていましたが、MacOSとLinuxはそもそも違います。  
まあ当然と言えば当然ですね。  
MacはBSDというUnixをベースに作られているらしいです。  



### 対処法

GNU Linuxにおけるdateコマンドと同様のものをbrewでインストールできます。

```
brew install coreutils
```



こうすることで、GNU Linuxにおけるdateコマンドと同じ働きをするgdateコマンドが使えます。
これをこのまま使ってもいいのですが、あくまでdateコマンドとして使いたい時は、.zshrcに

```
alias date=’/usr/local/bin/gdate’
```

を追記するなどして、エイリアスを定義しましょう。
一応、whichでgdateの保存先などを確認しておくとより確実ですね。

…

とまあ、ここまで説明しておいてアレですが、

```
sudo date 123112002021
```
でも変更できるみたいですね。


### +α


今回はdateコマンドでしたが、
- xargs
- sed
- grep
- base64
  もBSD UnixとGNU Linuxで挙動が違うコマンドの代表例らしいです。  
  ここら辺のある程度の知見を持っておきたい…。
  


Qiitaに投稿した元記事 : [https://qiita.com/DenverIA/items/f7b6fabdb332e1043fdd](https://qiita.com/DenverIA/items/f7b6fabdb332e1043fdd)