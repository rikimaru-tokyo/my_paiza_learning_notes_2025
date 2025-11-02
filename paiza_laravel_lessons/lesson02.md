<!-- omit in toc -->
# paiza Lesson 2: Laravelの動作を理解しよう

https://paiza.jp/works/laravel/primer/beginner-laravel2

<!-- omit in toc -->
[目次]
- [01:データベースとルーティングを理解しよう](#01データベースとルーティングを理解しよう)
  - [モデル・ビュー・コントローラの役割](#モデルビューコントローラの役割)
  - [Laravelでデータベースを操作する機能](#laravelでデータベースを操作する機能)
  - [参考になるWebページ](#参考になるwebページ)
    - [公式・総論](#公式総論)
  - [チュートリアル](#チュートリアル)
- [02:artisan tinkerでデータベースを確認しよう](#02artisan-tinkerでデータベースを確認しよう)
  - [artisan tinkerとは](#artisan-tinkerとは)
  - [artisan tinkerを起動する](#artisan-tinkerを起動する)
  - [artisan tinkerを終了する](#artisan-tinkerを終了する)
  - [主な操作コマンド](#主な操作コマンド)
  - [参考になるWebページ](#参考になるwebページ-1)
- [03:マイグレーションで、カラムを追加しよう](#03マイグレーションでカラムを追加しよう)
  - [マイグレーションとは](#マイグレーションとは)
  - [カラムを変更する前に、ライブラリを追加](#カラムを変更する前にライブラリを追加)
  - [マイグレーションファイルを自動生成する](#マイグレーションファイルを自動生成する)
  - [マイグレーションファイルにuser\_nameカラムを追加する](#マイグレーションファイルにuser_nameカラムを追加する)
  - [マイグレーションを実行する](#マイグレーションを実行する)
  - [参考になるWebページ](#参考になるwebページ-2)
- [04:モデルに追加したカラムをビューで表示しよう](#04モデルに追加したカラムをビューで表示しよう)
  - [indexビューにカラムを追加](#indexビューにカラムを追加)
  - [showビューにカラムを追加](#showビューにカラムを追加)
  - [参考になるWebページ](#参考になるwebページ-3)
- [05:Laravelのルーティングを理解しよう](#05laravelのルーティングを理解しよう)
  - [ルーティングとは](#ルーティングとは)
  - [通信方式を指定するメソッド](#通信方式を指定するメソッド)
  - [ルーティングでリダイレクトを設定](#ルーティングでリダイレクトを設定)
  - [参考になるWebページ](#参考になるwebページ-4)
- [06:データベースに書き込んでみよう](#06データベースに書き込んでみよう)
  - [新規投稿のルートを追加する](#新規投稿のルートを追加する)
  - [コントローラに、createメソッドを追加する](#コントローラにcreateメソッドを追加する)
  - [記事一覧のビューに、新規投稿リンクを追加する](#記事一覧のビューに新規投稿リンクを追加する)
  - [参考になるWebページ](#参考になるwebページ-5)
- [07:データベースから記事を削除しよう](#07データベースから記事を削除しよう)
  - [ルートを設定する](#ルートを設定する)
  - [詳細ページのビューに、削除ボタンを追加](#詳細ページのビューに削除ボタンを追加)
  - [コントローラのdestroyメソッドを追加する](#コントローラのdestroyメソッドを追加する)
  - [Webページのソースコードを確認する方法](#webページのソースコードを確認する方法)
  - [Form用ライブラリのインストールについて](#form用ライブラリのインストールについて)
  - [参考になるWebページ](#参考になるwebページ-6)


<br>

---

<br>

## 01:データベースとルーティングを理解しよう

### モデル・ビュー・コントローラの役割
- モデル：アプリで扱うデータを保持し、操作する
- ビュー：データの表示形式を記述する
- コントローラ：リクエストに応じて、モデル・ビューを呼び出す

### Laravelでデータベースを操作する機能
- artisan tinker：Laravelアプリの環境を有効にしたまま、コマンドで操作
- Eloquent：データベースのレコードをモデルクラスで処理する、O/Rマッパー
- マイグレーション：データベースの操作を一括実行・取り消し


![](./images/lesson0201.png)



### 参考になるWebページ

#### 公式・総論

- Laravel - The PHP Framework For Web Artisans
    - https://laravel.com/

- Laravel - ウェブ職人のためのPHPフレームワーク
    - http://laravel.jp/

- Laravel ドキュメント
    - https://readouble.com/laravel/

- Laravel - Wikipedia
    - https://ja.wikipedia.org/wiki/Laravel


### チュートリアル

- Laravel入門: 初心者でも10分でWebサービスを作れる！PHPフレームワークLaravelとPaizaCloudの使い方 - paiza開発日誌
    - https://paiza.hatenablog.com/entry/2018/02/16/paizacloud_laravel

- Laravel学習帳 - はじめてのLaravel入門サイト -
    - http://laraweb.net/

- Laravel5でシンプルなCRUDアプリを開発する - アシアルブログ
    - http://blog.asial.co.jp/1360


<br>

---

<br>


## 02:artisan tinkerでデータベースを確認しよう

### artisan tinkerとは

- Laravelに含まれているコマンドラインインターフェイス。
- artisan tinkerを使うと、Laravelアプリの環境を有効にしたまま、Laravelの機能をコマンドで操作できる

### artisan tinkerを起動する

```bash
$ cd bbs
$ php artisan tinker
```

### artisan tinkerを終了する
```bash
>>> exit
```

### 主な操作コマンド
すべてのデータを取り出す
```bash
>>> Article::all()
```

指定idのレコードを取り出し、カラムを出力
```bash
>>> $article = Article::find(1)
>>> $article->content
```

echo関数を使わずに、変数名を記述すると、そのまま値を出力する
```bash
>>> $article
```

レコードを追加する
```bash
>>> $article = new Article()
>>> $article->content = 'Hello tinker'
>>> $article->save()
```

指定idのレコードを取り出し、削除する
```bash
>>> $article = Article::find(1)
>>> $article->delete()
```


###  参考になるWebページ
- Artisanコンソール 5.6 Laravel
    - https://readouble.com/laravel/5.6/ja/artisan.html

- Laravel Artisan コマンド早見表 | Lindelin
    - https://jp.lindelin.org/blog/2017/artisan-quick-help/

- Artisanコマンドについて - Laravel学習帳
    - http://laraweb.net/environment/899/

- Laravel artisanコマンドメモ - Qiita
    - https://qiita.com/zaburo/items/37768b743ed6d0e28bf5

- もっとティンカー(tinker)を使おう！ – ララジャパン
  - https://www.larajapan.com/2017/12/27/%E3%82%82%E3%81%A3%E3%81%A8%E3%83%86%E3%82%A3%E3%83%B3%E3%82%


<br>

---

<br>


## 03:マイグレーションで、カラムを追加しよう


### マイグレーションとは
- 一般的に、マイグレーションとは、データベースの中身を一括して移行したり変更したりする作業です。
- Laravelのマイグレーション機能では、データベースの定義や変更を一度に行うことができます。
- マイグレーションは、2段階で行います。
  - まず、専用のコマンドを使ってマイグレーションファイルを作成して、それから必要な情報を修正して、データベースに適用します。

### カラムを変更する前に、ライブラリを追加
- Laravelでカラムを変更するには、doctrine/dbalというライブラリが必要になります。
- doctrine/dbalを追加するには、次のコマンドを実行します。

```bash
$ composer require doctrine/dbal
```
※この環境には、あらかじめdoctrine/dbalをインストールしてあります。


![](./images/lesson0202.png)


![](./images/lesson0203.png)



### マイグレーションファイルを自動生成する
```bash
$ cd bbs
$ php artisan make:migration add_column_username --table=articles
```

### マイグレーションファイルにuser_nameカラムを追加する
database/migrations/2019_xx_xx_xxxxxxxx_add_column_username.php
```php
<?php

use Illuminate\Support\Facades\Schema;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Database\Migrations\Migration;

class AddColumnNameTable extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::table('articles', function (Blueprint $table) {
            $table->string('user_name');
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::table('articles', function (Blueprint $table) {
            //
        });
    }
}
```

### マイグレーションを実行する
```bash
$ php artisan migrate
```

### 参考になるWebページ
- データベース：マイグレーション 5.7 Laravel
  - https://readouble.com/laravel/5.7/ja/migrations.html

- laravelでのマイグレーション作成手順 - Qiita
  - https://qiita.com/Thiru0000/items/83964c6ff8d8fecc4cfe

- LaravelのMigrationについて調べた結果 - Qiita
  - https://qiita.com/qiita-kurara/items/9a34f97a184a1d8c1c35

- Laravelのマイグレーション＆スキーマビルダでDBのテーブルやカラムを作成する
  - https://www.ritolab.com/entry/25

- LaravelのMigration（マイグレーション）でテーブルのカラムを追加・変更・削除する
  - https://www.ritolab.com/entry/26


<br>

---

<br>


## 04:モデルに追加したカラムをビューで表示しよう


### indexビューにカラムを追加
bbs/resources/views/index.blade.php
```php
<!DOCTYPE html>
<html>
    <head>
        <meta charset='utf-8'>
        <title>paiza bbs</title>
        <style>body {padding: 10px;}</style>
    </head>
    <body>
        <h1>paiza bbs</h1>
        <p>{{ $message }}</p>
        @foreach ($articles as $article)
            <p>
                <a href='{{ route("article.show", ["id" =>  $article->id]) }}'>
                    {{ $article->content }},
                    {{ $article->user_name }}
                </a>
            </p>
        @endforeach
    </body>
</html>
```



### showビューにカラムを追加
bbs/resources/views/show.blade.php

```php
<!DOCTYPE html>
<html>
    <head>
        <meta charset='utf-8'>
        <title>paiza bbs</title>
        <style>body {padding: 10px;}</style>
    </head>
    <body>
        <h1>paiza bbs</h1>
        <p>{{ $message }}</p>
        <p>{{ $article->content }}</p>
        <p>{{ $article->user_name }}</p>

        <p>
            <a href={{ route('article.list') }}>一覧に戻る</a>
        </p>
    </body>
</html>
```

### 参考になるWebページ
- データベース：マイグレーション 5.6 Laravel
  - https://readouble.com/laravel/5.6/ja/migrations.html

- laravelでのマイグレーション作成手順 - Qiita
  - https://qiita.com/Thiru0000/items/83964c6ff8d8fecc4cfe

- LaravelのMigrationについて調べた結果 - Qiita
  - https://qiita.com/qiita-kurara/items/9a34f97a184a1d8c1c35

- Laravelのマイグレーション＆スキーマビルダでDBのテーブルやカラムを作成する
  - https://www.ritolab.com/entry/25

- LaravelのMigration（マイグレーション）でテーブルのカラムを追加・変更・削除する
  - https://www.ritolab.com/entry/26


<br>

---

<br>


## 05:Laravelのルーティングを理解しよう

### ルーティングとは

- LaravelによるWebアプリケーションでは、機能に応じて、アドレスを割り当てておきます。
- そして、Laravelのルーティングで、リクエストに応じて、実行するコードを切り替えます。


![](./images/lesson0204.png)

![](./images/lesson0205.png)


### 通信方式を指定するメソッド

- Laravelでは、ブラウザとの通信にHTTPメソッドを指定します。
- 情報を表示するだけなら「GET」を使い、情報を投稿する場合は「POST」を使っています。
- また、記事を削除する場合は「DELETE」メソッドは指定します。
- このメソッドは、ブラウザとサーバ間の通信方式を指定するものです。
- クラスのコードを呼び出すメソッドと紛らわしいので注意してください。

### ルーティングでリダイレクトを設定
「/」にアクセスしたら、「/articles」にリダイレクトする

routes/web.php
```php
Route::get('/', function () {
    return redirect('/articles');
});

Route::get('/articles', 'ArticleController@index')->name('article.list');
Route::get('/article/{id}', 'ArticleController@show')->name('article.show');
```

### 参考になるWebページ
- ルーティング 5.7 Laravel
  - https://readouble.com/laravel/5.7/ja/routing.html

- Laravelルーティングの基本とよく使われるルーティングパターン
  - https://www.ritolab.com/entry/119

- これでLaravelのRouting(ルーティング）は完璧だ！ | Reffect Blog -
  - http://reffect.co.jp/blog/post/laravel-routing-perfect

- Laravelのルーティングチートシート - Qiita
  - https://qiita.com/fagai/items/a1bf55b6249aee03a624



<br>

---

<br>


## 06:データベースに書き込んでみよう


###  新規投稿のルートを追加する
bbs/routes/web.php
```php
<?php

Route::get('/', function () {
    return redirect('/articles');
});

// 上から順番にルートをたどるので{id}もアルファベットが入る可能性もある。順番に注意。
Route::get('/articles', 'ArticleController@index')->name('article.list');
Route::get('/article/new', 'ArticleController@create')->name('article.new');
Route::get('/article/{id}', 'ArticleController@show')->name('article.show');
```


### コントローラに、createメソッドを追加する
bbs/app/Http/Controllers/ArticleController.php
```php
public function create(Request $request)
    {
        $article = new Article();

        $article->content = 'Hello BBS';
        $article->user_name = 'paiza';
        $article->save();
        return redirect('/articles');
    }
```


### 記事一覧のビューに、新規投稿リンクを追加する
bbs/resources/views/index.blade.php
```php
<!DOCTYPE html>
<html>
    <head>
        <meta charset='utf-8'>
        <title>paiza bbs</title>
        <style>body {padding: 10px;}</style>
    </head>
    <body>
        <h1>paiza bbs</h1>
        <p>{{ $message }}</p>
        @foreach ($articles as $article)
            <p>
                <a href='{{ route("article.show", ["id" =>  $article->id]) }}'>
                    {{ $article->content }},
                    {{ $article->user_name }}
                </a>
            </p>
        @endforeach
        <div>
            <a href={{ route('article.new') }}>新規投稿</a>
        </div>
    </body>
</html>
```

###  参考になるWebページ
- Laravel・データベースからデータ取得する全実例 – console dot log
  - https://blog.capilano-fw.com/?p=665

- Laravel・データベースのデータ操作（追加／変更／削除）する全実例 – console dot log
  - https://blog.capilano-fw.com/?p=699


<br>

---

<br>


## 07:データベースから記事を削除しよう

### ルートを設定する
bbs/routes/web.php

```php
Route::get('/articles', 'ArticleController@index')->name('article.list');
Route::get('/article/new', 'ArticleController@create')->name('article.new');
Route::get('/article/{id}', 'ArticleController@show')->name('article.show');

//ブラウザはDeleteメソッドをサポートしていないことに注意
Route::delete('/article/{id}', 'ArticleController@destroy')->name('article.delete');
```


### 詳細ページのビューに、削除ボタンを追加
bbs/resources/views/show.blade.php

```php
<!DOCTYPE html>
<html>
    <head>
        <meta charset='utf-8'>
        <title>paiza bbs</title>
        <style>body {padding: 10px;}</style>
    </head>
    <body>
        <h1>paiza bbs</h1>
        <p>{{ $message }}</p>
        <p>{{ $article->content }}</p>
        <p>{{ $article->user_name }}</p>

        <p>
            <a href={{ route('article.list') }}>一覧に戻る</a>
        </p>
        <div>
            {{ Form::open(['method' => 'delete', 'route' => ['article.delete', $article->id]]) }}
                {{ Form::submit('削除') }}
            {{ Form::close() }}
        </div>
    </body>
</html>
```

### コントローラのdestroyメソッドを追加する
bbs/app/Http/Controllers/ArticleController.php

```php
public function destroy(Request $request, $id, Article $article)
    {
        $article = Article::find($id);
        $article->delete();
        return redirect('/articles');
    }
```


### Webページのソースコードを確認する方法
paiza cloud内のブラウザで、WebページのHTMLを確認するには、次のように操作します。

ここでは、Mac OS X版のChromeを例にしていますが、他のWebブラウザでも、ほぼ同じ操作で確認できます。

1. 右上にある「新しいウィンドウで開く」アイコンをクリック
2. HTMLを確認したいWebページを表示する
3. Chromeのメニューで「ページのソースを表示」を選択する


### Form用ライブラリのインストールについて

削除ボタンを追加するには、Laravelでフォームを使用する場合に必要となる「laravelcollective/html」というライブラリをインストールします。

これは、次のコマンドでインストールします。

```bash
$ cd bbs
$ composer require "laravelcollective/html":"^5.4.0"
```

このチャプターの環境には、このライブラリをインストール済みです。

###  参考になるWebページ
  - Laravel・データベースからデータ取得する全実例 – console dot log
    - https://blog.capilano-fw.com/?p=665

  - Laravel・データベースのデータ操作（追加／変更／削除）する全実例 – console dot log
    - https://blog.capilano-fw.com/?p=699


<br>

---

<br>

【EOF】







[←　README](../README.md) 
