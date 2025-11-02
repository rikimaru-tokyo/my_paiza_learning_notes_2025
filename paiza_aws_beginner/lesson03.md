<!-- omit in toc -->
# AWS入門編3: SQLの基本文法を学ぶ

<!-- omit in toc -->
# [目次]

- [01:データベースを知ろう](#01データベースを知ろう)
  - [データベースの構成要素](#データベースの構成要素)
  - [SQLの参考情報](#sqlの参考情報)
- [02:データベースを準備しよう](#02データベースを準備しよう)
  - [簡単に手に入るLAMP環境](#簡単に手に入るlamp環境)
  - [phpMyAdminの参考資料](#phpmyadminの参考資料)
  - [サンプルデータベースを作成するSQL文](#サンプルデータベースを作成するsql文)
- [03:テーブルの中身を見てみよう](#03テーブルの中身を見てみよう)
  - [今回取り上げたSQL文の例](#今回取り上げたsql文の例)
  - [WHERE句の条件指定](#where句の条件指定)
- [04:いろいろな情報を取り出そう](#04いろいろな情報を取り出そう)
  - [今回取り上げたSQL文の例](#今回取り上げたsql文の例-1)
  - [GROUP BYの参考資料](#group-byの参考資料)
- [05:データを追加・更新・削除しよう](#05データを追加更新削除しよう)
  - [NSERT・UPDATE・DELETEの参考資料](#nsertupdatedeleteの参考資料)
- [06:2つのテーブルを結合しよう](#062つのテーブルを結合しよう)
  - [テーブルの関連付けとは](#テーブルの関連付けとは)
  - [今回取り上げたSQL文の例](#今回取り上げたsql文の例-2)
  - [内部結合](#内部結合)
  - [外部結合](#外部結合)
- [07:結合したテーブルを操作しよう](#07結合したテーブルを操作しよう)
  - [今回取り上げたSQL文の例](#今回取り上げたsql文の例-3)


<br>

---

<br>


# 01:データベースを知ろう



## データベースの構成要素

|構成要素|意味|
|-------|----|
|テーブル|データを格納する表|
|行 / レコード|テーブルの横のデータの並びを「行」とか「レコード」と呼びます。データは、この行ごとに、ひとつのかたまりになっています。|
|カラム / 列|各レコードが持つデータの要素。|
|リレーション|複数のテーブルを組み合わせる場合の関連付け|
|SQL|代表的なデータベース問い合わせ言語。データベースに対する操作は、プログラムのような文字ベースの命令をSQLの文法に従って記述します。|



## SQLの参考情報
- 初心者でもほぼ無料でSQLを勉強できるコンテンツ8選 - paiza開発日誌
  - http://paiza.hatenablog.com/entry/2015/06/10/%E5%88%9D%E5%BF%83%E8%80%85%E3%81%A7%E3%82%82%E3%81%BB%E3%81%BC%E7%84%A1%E6%96%99%E3%81%A7SQL%E3%82%92%E5%8B%89%E5%BC%B7%E3%81%A7%E3%81%8D%E3%82%8B%E3%82%B3%E3%83%B3%E3%83%86%E3%83%B3%E3%83%848%E9%81%B8
- 【まとめ】SQLコマンド一覧 - Qiita
  - http://qiita.com/KENJU/items/313b5640da05834a53aa
- SQL入門
  - http://nsa.kpu-m.ac.jp/gijutu/unix/man-postfix/www.kozupon.com/sql/sql1.html
- とりあえずこれだけ知っとけSQL
  - http://ash.jp/db/sql.htm
- １週間で学ぶIT基礎の基礎 - 忙しいあなたのためのSQL入門---目次：ITpro
  - http://itpro.nikkeibp.co.jp/article/COLUMN/20061213/256848/
- SQL攻略 - SQL攻略マップ
  - http://sql.main.jp/cont/sql/map.html
- 逆引きSQL構文集
  - http://www.sql-reference.com/
- MySQL :: MySQL 5.6 リファレンスマニュアル
  - https://dev.mysql.com/doc/refman/5.6/ja/




<br>

---

<br>


# 02:データベースを準備しよう

##  簡単に手に入るLAMP環境

- 就活パック LAMP環境を構築しよう - AWS編
  - https://paiza.jp/works/aws/primer



##  phpMyAdminの参考資料

- phpMyAdminの使い方
  - http://www.dbonline.jp/phpmyadmin/


## サンプルデータベースを作成するSQL文

```sql
CREATE TABLE players (
  id INT NOT NULL PRIMARY KEY,
  name VARCHAR(32),
  level INT,
  job_id INT
);

CREATE TABLE jobs (
  id INT NOT NULL PRIMARY KEY,
  job_name VARCHAR(10),
  vitality INT,
  strength INT,
  agility INT,
  intelligence INT,
  luck INT
);

INSERT
  INTO players(id,name,level,job_id)
  VALUES
    (1,"パイザ",12,6),
    (2,"ケン",7,2),
    (3,"リン",1,1),
    (4,"ユウ",3,3),
    (5,"クレア",10,4),
    (6,"ショウ",5,2),
    (7,"さくら",7,1),
    (8,"ジャック",5,4),
    (9,"ロック",12,6),
    (10,"じゅん",1,NULL);

INSERT
  INTO jobs(id, job_name, vitality, strength, agility, intelligence, luck)
  VALUES
    (1,"戦士",8,8,4,4,3),
    (2,"盗賊",3,3,8,5,7),
    (3,"狩人",5,5,7,5,4),
    (4,"魔法使い",3,2,6,8,6),
    (5,"僧侶",5,5,3,7,5),
    (6,"勇者",10,10,10,10,10);

```






<br>

---

<br>


# 03:テーブルの中身を見てみよう

## 今回取り上げたSQL文の例

```sql
-- 全てのデータを取り出す
SELECT * FROM players;


-- 一部のカラムだけ取得する
SELECT name, level FROM players;


-- 一部の行だけ取得する
SELECT * FROM players WHERE level >= 7;


-- 複数の条件を組み合わせる
SELECT * FROM players WHERE level >= 7 AND job_id <> 6;


-- 条件指定とカラム選択を組み合わせる
SELECT name, level FROM players WHERE level >= 7;
```


## WHERE句の条件指定
|構文|意味|例|
|----|---|---|
|a = b|a と b が等しい|level = 10|
|a < b|a が b よりも小さい|level < 15|
|a > b|a が b よりも大きい|level > 7|
|a <= b|a が b 以下である|level >= 15|
|a >= b|a が b 以上である|level >= 7|
|a <> b|a と b が等しくない|level <> 1|


|条件をつなげるキーワード|意味|
|---|---|
|AND|両方の条件が成立した場合|
|OR|どちらか一方の条件が成立した場合|


<br>

---

<br>


# 04:いろいろな情報を取り出そう

## 今回取り上げたSQL文の例

```sql
-- データ件数を表示する
SELECT COUNT(*) FROM players;


-- 条件に合ったデータの件数を表示する
SELECT COUNT(*) FROM players WHERE job_id = 6;


-- データを並び替えて取得する
SELECT * FROM players ORDER BY level;


-- データを並び替えて取得する 逆順
SELECT * FROM players ORDER BY level DESC;


-- 上位3件だけ表示す
SELECT * FROM players ORDER BY level DESC LIMIT 3;


-- 職業ごとに人数を集計する
SELECT job_id, COUNT(*) FROM players GROUP BY job_id;
```

## GROUP BYの参考資料

- 【初級編⑪】SQLのGROUP BYでレコードのグループ化と集計を行う
  -  http://kaya-soft.com/sqlserver2008-toranomaki/beginner/groupby/



<br>

---

<br>






# 05:データを追加・更新・削除しよう


今回取り上げたSQL文の例

```sql
-- データを追加する
INSERT INTO players(id,name,level,job_id) VALUES(11, "霧島1号", 1, 1);


-- データを追加して表示する
INSERT INTO players(id,name,level,job_id) VALUES(12, "霧島2号", 1, 1);
SELECT * FROM players;


-- 一度に複数のデータを追加する
INSERT INTO players(id,name,level,job_id)
VALUES
(13, "霧島3号", 1, 1),
(14, "霧島4号", 1, 1)
;
SELECT * FROM players;


-- データを更新する
UPDATE players SET level = 10 WHERE id = 11;
SELECT * FROM players;


-- データを更新する。1増加
UPDATE players SET level = level + 1 WHERE id = 12;
SELECT * FROM players;


-- データを削除する
DELETE FROM players WHERE id = 13;
SELECT * FROM players;


-- データを削除する
DELETE FROM players WHERE id >= 11;
SELECT * FROM players;
```

## NSERT・UPDATE・DELETEの参考資料

- SQL攻略 - INSERT文
  - http://sql.main.jp/cont/sql/in.html
- SQL攻略 - UPDATE文
  - http://sql.main.jp/cont/sql/up.html
- SQL攻略 - DELETE文
  - http://sql.main.jp/cont/sql/de.html




<br>

---

<br>



# 06:2つのテーブルを結合しよう

## テーブルの関連付けとは

- テーブルの関連付けとは、重複したデータのテーブルを分割しておいて、必要に応じて、仮想的な1つの表として結合して扱う方法です。




## 今回取り上げたSQL文の例

```sql
-- テーブルを結合して表示する（内部結合）
SELECT * FROM players INNER JOIN jobs ON jobs.id = players.job_id;

-- テーブルを結合して表示する(左結合)
SELECT * FROM players LEFT JOIN jobs ON jobs.id = players.job_id;

-- テーブルを結合して表示する(右結合)
SELECT * FROM players RIGHT JOIN jobs ON jobs.id = players.job_id;
```


## 内部結合

- 両方のテーブルに共通のデータを表示（INNER JOIN）

## 外部結合

- 左結合(LEFT JOIN): 左側テーブルを基準に表示
- 右結合(RIGHT JOIN): 右側テーブルを基準に表示



<br>

---

<br>



# 07:結合したテーブルを操作しよう


## 今回取り上げたSQL文の例

```sql
-- 結合したテーブルを操作する
SELECT * FROM players INNER JOIN jobs ON jobs.id = players.job_id;

-- 結合したテーブルで、指定カラムだけ表示
SELECT name, level, vitality FROM players INNER JOIN jobs ON jobs.id = players.job_id;

-- 結合したテーブルで、条件に合った行だけ表示
SELECT name, level, strength FROM players INNER JOIN jobs ON jobs.id = players.job_id WHERE strength >= 5;

-- 職業ごとに人数を集計する
SELECT job_id, job_name, COUNT(*) FROM players INNER JOIN jobs ON jobs.id = players.job_id GROUP BY job_id;

```


<br>

---

<br>


【EOF】



[←　README](../README.md)

