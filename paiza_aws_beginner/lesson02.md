<!-- omit in toc -->
# AWS入門編2:LAMP環境を構築しよう

<!-- omit in toc -->
[目次]
- [解約時の注意](#解約時の注意)
- [01:LAMP環境を理解しよう](#01lamp環境を理解しよう)
  - [LAMPとは](#lampとは)
  - [LAMP環境の構築手順](#lamp環境の構築手順)
- [02:PHPをインストールしよう](#02phpをインストールしよう)
  - [PHPインストールの作業手順](#phpインストールの作業手順)
  - [ここで利用したコマンド](#ここで利用したコマンド)
  - [SSHコマンドによる接続](#sshコマンドによる接続)
  - [設定ファイルのバックアップと復帰方法](#設定ファイルのバックアップと復帰方法)
  - [PHPの設定変更](#phpの設定変更)
  - [/var/www/html/index.phpに次のコードを入力](#varwwwhtmlindexphpに次のコードを入力)
  - [PHP設定の参考資料](#php設定の参考資料)
- [04:MySQLのインストール](#04mysqlのインストール)
  - [MySQLインストールの作業手順](#mysqlインストールの作業手順)
  - [ここで利用したコマンド](#ここで利用したコマンド-1)
  - [!!! MySQLの文字コード設定](#-mysqlの文字コード設定)
- [05:phpMyAdminのインストール](#05phpmyadminのインストール)
  - [MySQLインストールの作業手順](#mysqlインストールの作業手順-1)
  - [phpMyAdminの利用](#phpmyadminの利用)
- [06:掲示板を設置しよう](#06掲示板を設置しよう)
  - [Web掲示板を設置手順](#web掲示板を設置手順)
  - [bbs.phpのダウンロード](#bbsphpのダウンロード)
  - [データベースの作成情報](#データベースの作成情報)
- [07:HTMLを改良しよう](#07htmlを改良しよう)
  - [HTML部分の変更内容](#html部分の変更内容)
  - [今回のチャプターの変更が適応されたbbs.phpのダウンロード](#今回のチャプターの変更が適応されたbbsphpのダウンロード)
- [08:PHPを改良しよう](#08phpを改良しよう)
  - [PHP部分の変更内容](#php部分の変更内容)
  - [bbs.phpのダウンロード](#bbsphpのダウンロード-1)
  - [bbs.phpの修正箇所](#bbsphpの修正箇所)
  - [ここで利用したコマンド](#ここで利用したコマンド-2)
- [09:DBを改良しよう - 投稿の削除](#09dbを改良しよう---投稿の削除)
  - [データベース操作の修正手順](#データベース操作の修正手順)
  - [bbs.phpのダウンロード](#bbsphpのダウンロード-2)
- [10:DBを改良しよう - 投稿者名の追加](#10dbを改良しよう---投稿者名の追加)
  - [掲示板の機能追加の手順](#掲示板の機能追加の手順)
  - [bs.phpのダウンロード](#bsphpのダウンロード)


<br>

---

<br>


# 解約時の注意

> [!CAUTION]
> 無料期間内でも、停止・削除したインスタンスに割り当てたパブリックIPの設定を解除しておかないと料金が発生してしまいますので、忘れずに解約しておきましょう。<br>
> http://docs.aws.amazon.com/ja_jp/awsaccountbilling/latest/aboutv2/checklistforunwantedcharges.html#checkelasticipaddresses



<br>

---

<br>


# 01:LAMP環境を理解しよう


## LAMPとは

LAMP(ランプ)とは、Webアプリケーションの実行環境の組み合わせです。
Webアプリケーションの実行環境では、ふつう、OSとWebサーバー、データベース、スクリプト言語を組み合わせて利用します。
中でもLAMPは、Webサービスがはやり始めたころからある、オーソドックスな組み合わせです。OSにLinux(リナックス)、WebサーバにApache(アパッチ)、データベースにMySQL(マイエスキューエル)、スクリプト言語にPHP(ピーエイチピー)という組み合わせを、その頭文字をとって、LAMP(ランプ)と呼びます。


## LAMP環境の構築手順

  1. PHPをインストールする
  2. MySQLをインストールする
  3. サンプル掲示板を設置する
  4. HTMLベースで改良する
  5. PHPベースで改良する
  6. PHPベースで改良する





<br>

---

<br>

# 02:PHPをインストールしよう

## PHPインストールの作業手順

1. Webサーバーの動作確認
2. SSHでログインする
3. 管理者権限に切り替える
4. サーバの時間設定(UTCからJST)
5. PHPのインストール
6. PHPの設定
7. Apacheの再起動
8. PHPの動作確認


##  ここで利用したコマンド

sshコマンドでログイン

```bash
$ ssh -i ~/.ssh/FirstKey.pem ec2-user@(パブリックIP)

# 管理者権限に切り替える
$$ sudo su


# 時刻の確認
date


# ローカルタイムの設定
ln -sf /usr/share/zoneinfo/Japan /etc/localtime


# PHPをインストール
yum install -y php


## PHP設定ファイルのバックアップ
cp /etc/php.ini /etc/php.bak


# Apacheの再起動
service httpd restart
```

##  SSHコマンドによる接続

- Linux インスタンスへの接続 - Amazon Elastic Compute Cloud
  - https://docs.aws.amazon.com/ja_jp/AWSEC2/latest/UserGuide/AccessingInstances.html
- SSH を使用した Linux インスタンスへの接続 - Amazon Elastic Compute Cloud
  - http://docs.aws.amazon.com/ja_jp/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html
- ネットワーク管理の基本Tips - ＠IT - SSHサーバーにログインするには？ sshコマンド
  - http://www.atmarkit.co.jp/ait/articles/1503/23/news004.html
- 端末エミュレータ - Wikipedia
  - https://ja.wikipedia.org/wiki/%E7%AB%AF%E6%9C%AB%E3%82%A8%E3%83%9F%E3%83%A5%E3%83%AC%E3%83%BC%E3%82%BF


## 設定ファイルのバックアップと復帰方法
設定ファイルを変更する場合、事前にバックアップを取っておくと安心です。バックアップを取っておけば、もしも変更を間違えた場合も、すぐに復帰させることができます。


バックアップを取るには、次のように、ターミナルでファイルをコピーしておきます。「cp」コマンドは、ファイルをコピーするコマンドです。

```bash
cp (元々のファイル名) (バックアップファイル名)
```

例えば、PHPの設定ファイルをバックアップするには、次のコマンドを実行します。
```bash
cp /etc/php.ini /etc/php.bak
```


バックアップを復帰させるには、次のように、バックアップファイルを元のファイルに上書きします。
```bash
cp (バックアップファイル名) (元々のファイル名)
```

例えば、PHPの設定ファイルのバックアップを復帰させるには、次のコマンドを実行します。
```bash
cp /etc/php.bak /etc/php.ini
```

## PHPの設定変更
「& ~E_NOTICE」を追加
```bash
error_reporting = E_ALL & ~E_DEPRECATED & ~E_NOTICE
```

OffからOnへ
```bash
display_errors = On
```

## /var/www/html/index.phpに次のコードを入力

```php
<?php
echo "hello PHP!";
?>
```

## PHP設定の参考資料

-  【PHP】PHPをインストールしたらやっておきたい設定 - Qiita
  -  http://qiita.com/knife0125/items/0e1af52255e9879f9332



<br>

---

<br>


# 04:MySQLのインストール

## MySQLインストールの作業手順
   1. MySQLのインストール
   2. MySQLの起動
   3. MySQLの設定
   4. 文字コードの設定
   5. phpMyAdminのインストール
   6. phpMyadminの設定
   7. phpMyadminの動作確認


## ここで利用したコマンド
sshコマンドでログイン

```bash
$ ssh -i ~/.ssh/FirstKey.pem ec2-user@(パブリックIP)


# 管理者権限に切り替える
$$ sudo su

# MySQLのインストール
yum install -y mysql-server

# 追加プログラム(PHPのMySQLネイティブドライバ)のインストール
yum install -y php-mysqlnd

# MySQLの起動
service mysqld start

# MySQLの設定
mysql_secure_installation

# MySQLの文字コード設定のために、設定ファイルを開く
vi /etc/my.cnf

# MySQLの再起動
service mysqld restart
```


##  !!! MySQLの文字コード設定
```bash
character-set-server = utf8
```



<br>

---

<br>

# 05:phpMyAdminのインストール

## MySQLインストールの作業手順

   1. MySQLのインストール
   2. MySQLの起動
   3. MySQLの設定
   4. 文字コードの設定
   5. phpMyAdminのインストール
   6. phpMyadminの設定
   7. phpMyadminの動作確認


```bash

ここで利用したコマンド
# phpMyAdminのダウンロード先を追加

yum-config-manager --enable epel

# phpMyAdminのインストール
yum install -y phpmyadmin

# phpMyAdminの設定(アクセス制限) のために、設定ファイルを開く
vi /etc/httpd/conf.d/phpMyAdmin.conf

# Apacheの再起動
service httpd restart
```

## phpMyAdminの利用

```bash
http://(WebサーバーのグローバルIPアドレス)/phpmyadmin
```


<br>

---

<br>


# 06:掲示板を設置しよう

## Web掲示板を設置手順
   1. MySQL上にデータベースを作成
   2. テーブルを作成する
   3. カラムを作成する
   4. bbs.phpをダウンロードする
   5. bbs.phpをアップロードする
   6. 動作確認

## bbs.phpのダウンロード

bbs.php( https://paiza-webapp.s3.amazonaws.com/files/learning/bbs/6/bbs.php )

※Windows ：右クリック - 名前を付けてリンク先を保存

※Mac ：CTRL + クリック - リンクに名前を付けて保存


##  データベースの作成情報
```
データベース
DB名: lesson
照合順序: utf8_general_ci

テーブルの定義
テーブル名: bbs
カラム数: 3

カラムの定義
名前: id, データ型: INT, インデックス: PRIMARY, A_I: オン
名前: content, データ型: TEXT
名前: updated_at, データ型: DATETIME
照合順序: utf8_general_ci
```


<br>

---

<br>


# 07:HTMLを改良しよう


## HTML部分の変更内容
   1. 見出し１のテキストを変更
   2. 見出し２のテキストを変更
   3. 背景色を変更
   4. Bootstrap CDNを適用

```XML
<!-- bootstrap CDN -->
<link rel="stylesheet" href="http://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css"/>
<script src="http://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/js/bootstrap.min.js"></script>
```

## 今回のチャプターの変更が適応されたbbs.phpのダウンロード

- bbs.php( https://paiza-webapp.s3.amazonaws.com/files/learning/bbs/7/bbs.php )


<br>

---

<br>


# 08:PHPを改良しよう

## PHP部分の変更内容

1. 行番号を追加
2. 交互に色を変える


## bbs.phpのダウンロード
- 前チャプターの完成版コード
  - bbs.php( https://paiza-webapp.s3.amazonaws.com/files/learning/bbs/7/bbs.php )

- 本チャプターの完成版コード
  - bbs.php( https://paiza-webapp.s3.amazonaws.com/files/learning/bbs/8/bbs.php )

- ※Windows ：右クリック - 名前を付けてリンク先を保存
- ※Mac ：CTRL + クリック - リンクに名前を付けて保存


## bbs.phpの修正箇所
行番号を追加

```php
// 取得したデータをテーブルで表示
?>
<table class="table">
<tr>
  <th>No.</th>
  <th>日時</th>
  <th>投稿内容</th>
</tr>
<?php
while ($row = $stmt -> fetch(PDO::FETCH_ASSOC)) {
  $i++;
?>
<tr>
  <td><?php echo "$i"; ?></td>
  <td><?php echo "$row[updated_at]"; ?></td>
  <td><?php echo "$row[content]"; ?></td>
</tr>
<?php
}
?>


//交互に色を変える

// 取得したデータをテーブルで表示
?>
<table class="table">
  <tr>
    <th>No.</th>
    <th>日時</th>
    <th>投稿内容</th>
  </tr>
<?php
  while ($row = $stmt -> fetch(PDO::FETCH_ASSOC)) {
    $i++;
    if ($i % 2 == 1) {
?>
  <tr bgcolor="#cccccc">
<?php
  } else {
?>
 <tr>
<?php
  }
?>
    <td><?php echo "$i"; ?></td>
    <td><?php echo "$row[updated_at]"; ?></td>
    <td><?php echo "$row[content]"; ?></td>
 </tr>
<?php
  }
?>
</table>
```

##  ここで利用したコマンド
ファイルの転送
```bash
$ scp -i ~/.ssh/FirstKey.pem ~/Desktop/bbs.php ec2-user@(パブリックIP):/var/www/html
```



<br>

---

<br>


# 09:DBを改良しよう - 投稿の削除

## データベース操作の修正手順
  1. デバッグ用にidを表示
  2. 削除ボタンを追加
  3. 削除ボタンで送信されたidを表示
  4. 受信したidのデータを削除
  5. デバッグ用コードをコメントアウト



## bbs.phpのダウンロード
- 前チャプターの完成版コード
  - bbs.php( https://paiza-webapp.s3.amazonaws.com/files/learning/bbs/8/bbs.php )
- 本チャプターの完成版コード
  - bbs.php( https://paiza-webapp.s3.amazonaws.com/files/learning/bbs/9/bbs.php )


- ※Windows ：右クリック - 名前を付けてリンク先を保存
- ※Mac ：CTRL + クリック - リンクに名前を付けて保存


```php


//bbs.phpの修正箇所
// 送信されたid

// 変数の設定
$content = $_POST["content"];
$delete_id = $_POST["delete_id"];


// データを削除する
// データベースのデータの削除
$sql = "DELETE FROM bbs WHERE id = :delete_id;";
$stmt = $pdo->prepare($sql);
$stmt -> bindValue(":delete_id", $delete_id, PDO::PARAM_INT);
$stmt -> execute();


// 発言リストのテーブル
// 取得したデータをテーブルで表示
// echo "del_id:".$delete_id;
?>
<table class="table">
    <tr>
        <th>No.</th>
        <!-- <th>id</th> -->
        <th>日時</th>
        <th>投稿内容</th>
    </tr>
<?php
while ($row = $stmt -> fetch(PDO::FETCH_ASSOC)) {
    $i++;
    if ($i % 2 == 1) {
?>
    <tr bgcolor="#cccccc">
<?php
  } else {
?>
    <tr>
<?php
  }
?>
    <td><?php echo "$i"; ?></td>
    <!-- <td><?php // echo "$row[id]"; ?></td> -->
    <td><?php echo "$row[updated_at]"; ?></td>
    <td><?php echo "$row[content]"; ?></td>
    <td>
      <form action="bbs.php" method="post" role="form">
        <button type="submit" class="btn btn-danger">削除</button>
        <div class="form-group">
			<input type="hidden" name="delete_id" value="<?php echo $row[id]; ?>" class="form-control"/>
		</div>
      </form>
    </td>
    </tr>
<?php
}
?>
</table>

```


<br>

---

<br>


# 10:DBを改良しよう - 投稿者名の追加

## 掲示板の機能追加の手順
  1. 投稿フォームに、名前欄を追加
  2. 発言リストに、名前欄を追加
  3. データベースにuser_nameカラムを追加
  4. 名前情報を挿入するコードを追加


## bs.phpのダウンロード
- 前チャプターの完成版コード
  - bbs.php( https://paiza-webapp.s3.amazonaws.com/files/learning/bbs/9/bbs.php )
- 本チャプターの完成版コード
  - bbs.php( https://paiza-webapp.s3.amazonaws.com/files/learning/bbs/10/bbs.php )


- ※Windows ：右クリック - 名前を付けてリンク先を保存
- ※Mac ：CTRL + クリック - リンクに名前を付けて保存



```php

//bbs.phpの修正箇所
//投稿フォームに名前欄を追加

<h2>投稿フォーム</h2>
<form action="bbs_41.php" method="post" role="form">
  <div class="form-group">
    <label class="control-label">名前</label>
    <input type="text" name="user_name" class="form-control" placeholder="名前"/>
  </div>
  <div class="form-group">
    <label class="control-label">投稿内容</label>
    <input type="text" name="content" class="form-control" placeholder="投稿内容"/>
  </div>
  <button type="submit" class="btn btn-primary">送信</button>
</form>


//送信された名前情報
// 変数の設定
$content = $_POST["content"];
$user_name = $_POST["user_name"];
$delete_id = $_POST["delete_id"];


//名前情報をデータベースに挿入
// データベースへのデータの挿入
$sql  = "INSERT INTO bbs (content, updated_at, user_name) VALUES (:content, NOW(), :user_name);";
$stmt = $pdo->prepare($sql);
$stmt -> bindValue(":content", $content, PDO::PARAM_STR);
$stmt -> bindValue(":user_name", $user_name, PDO::PARAM_STR);
$stmt -> execute();


//発言リストに名前欄を追加
// 取得したデータをテーブルで表示
// echo "del_id:".$delete_id;
?>
<table class="table">
    <tr>
        <th>No.</th>
        <!-- <th>id</th> -->
        <th>名前</th>
        <th>日時</th>
        <th>投稿内容</th>
	<th></th>
    </tr>
<?php
while ($row = $stmt -> fetch(PDO::FETCH_ASSOC)) {
    $i++;
    if ($i % 2 == 1) {
?>
    <tr bgcolor="#cccccc">
<?php
  } else {
?>
    <tr>
<?php
  }
?>
    <td><?php echo "$i"; ?></td>
    <td><?php echo "$row[user_name]" ?></td>
    <!-- <td><?php // echo "$row[id]"; ?></td> -->
    <td><?php echo "$row[updated_at]"; ?></td>
    <td><?php echo "$row[content]"; ?></td>
    <td>
      <form action="bbs_41.php" method="post" role="form">
        <button type="submit" class="btn btn-danger">削除</button>
        <div class="form-group">
			<input type="hidden" name="delete_id" value="<?php echo $row[id]; ?>" class="form-control"/>
		</div>
      </form>
    </td>
    </tr>
<?php
}
?>
</table>


```

<br>

---

<br>


【EOF】



[←　README](../README.md)

