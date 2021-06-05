+++
draft = false
image = ""
showonlyimage = false
title = "『テスト駆動開発』のエッセンシャル"
date = "2021-05-13T22:12:03.284Z"
description = "書籍『テスト駆動開発』のまとめ"
tags = ["本", "テスト駆動開発"]
+++


# テスト駆動開発の手法

1. やることをTODOリストに書き出す(これは随時思いつき次第追加していく)
1. 小さいテストを一つ書く
1. 全てのテストを実行し、先程の一つだけが失敗することを確認する
1. コンパイルエラーを通す
1. テストを通すための最小限の変更を行い、全てのテストが成功することを確認する
1. リファクタリングを行い**重複**を除去する

# テスト駆動開発の心得

- 細かいステップを**踏み続けられるようにする**
- TDDの三つの戦略
    - **仮実装** ... コードでまずベタ書きの値をつかい、実装を進めるに従って徐々に変数に置き換えていく
    - **明白な実装** ... すぐに頭の中の実装をコードに落とす
    - **三角測量** ... 既存のコードに二つ目の実例を追加する(trueを確かめるものがあればfalseを吐き出すもの、など)