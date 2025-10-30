<!-- omit in toc -->
# paiza Lesson 1: Laravelの基本を理解しよう

https://paiza.jp/works/laravel/primer/beginner-laravel1/9101

<!-- omit in toc -->
[目次]
- [01:Laravelの基本を理解しよう](#01laravelの基本を理解しよう)
  - [Webアプリケーションフレームワークとは](#webアプリケーションフレームワークとは)
  - [Laravelの特徴](#laravelの特徴)
  - [参考になるWebページ](#参考になるwebページ)
- [02:アプリケーションを用意しよう](#02アプリケーションを用意しよう)
  - [このチャプターで使用したコマンド](#このチャプターで使用したコマンド)
  - [アプリケーション用ディレクトリを自動生成する](#アプリケーション用ディレクトリを自動生成する)
  - [Webサーバーを起動](#webサーバーを起動)
  - [Artisanとは](#artisanとは)
  - [参考になるWebページ](#参考になるwebページ-1)
- [03:Laravel で HelloWorld](#03laravel-で-helloworld)
  - [Welcomeページを修正する](#welcomeページを修正する)
  - [参考になるWebページ](#参考になるwebページ-2)
  - [データベース構成](#データベース構成)
  - [アプリケーションのデータベース設定](#アプリケーションのデータベース設定)
  - [参考になるWebページ](#参考になるwebページ-3)
- [05:モデルとコントローラを用意する](#05モデルとコントローラを用意する)
  - [モデルとマイグレーション、コントローラを作成](#モデルとマイグレーションコントローラを作成)
  - [contentカラムを追加](#contentカラムを追加)
  - [マイグレーション実行](#マイグレーション実行)
  - [参考になるWebページ](#参考になるwebページ-4)
- [06:ルーティングを定義しよう](#06ルーティングを定義しよう)
  - [ルーティングとは](#ルーティングとは)
  - [1行掲示板のルーティング(一覧画面、詳細画面)](#1行掲示板のルーティング一覧画面詳細画面)
  - [paiza-cloud用https対応](#paiza-cloud用https対応)
  - [参考になるWebページ](#参考になるwebページ-5)
- [07:コントローラとビューを作成しよう](#07コントローラとビューを作成しよう)
  - [コントローラからデータを渡す](#コントローラからデータを渡す)
  - [ビューでデータを表示する](#ビューでデータを表示する)
  - [参考になるWebページ](#参考になるwebページ-6)
- [08:記事一覧を作成しよう](#08記事一覧を作成しよう)
  - [コントローラで、記事一覧を取得する](#コントローラで記事一覧を取得する)
  - [ビューで記事一覧を表示する](#ビューで記事一覧を表示する)
  - [参考になるWebページ](#参考になるwebページ-7)
- [09:詳細画面を作ろう](#09詳細画面を作ろう)
  - [bbs/app/Http/Controllers/ArticleController.php:](#bbsapphttpcontrollersarticlecontrollerphp)
  - [showビューで、指定の記事を表示する](#showビューで指定の記事を表示する)
  - [記事一覧から個別の記事にリンクする](#記事一覧から個別の記事にリンクする)
  - [参考になるWebページ](#参考になるwebページ-8)



---




## 01:Laravelの基本を理解しよう


### Webアプリケーションフレームワークとは
- Webアプリを開発するために便利な部品やツールをひとまとめにしたもの。
- Webアプリケーションを短期間に効率よく開発できる。

### Laravelの特徴
- テンプレートエンジン(Blade)
- データベース(O/Rマッパー：Eloquent)
- 対話型コンソール(artisan tinker)
- ユーザー認証 など


### 参考になるWebページ
- Laravel - The PHP Framework For Web Artisans
  - https://laravel.com/

- Laravel - Wikipedia
  - https://ja.wikipedia.org/wiki/Laravel

- Laravel入門: 初心者でも10分でWebサービスを作れる！
PHPフレームワークLaravelとPaizaCloudの使い方 - paiza開発日誌
  - https://paiza.hatenablog.com/entry/2018/02/16/paizacloud_laravel

---

## 02:アプリケーションを用意しよう

### このチャプターで使用したコマンド

- カレントディレクトリの確認
```shell
$ pwd
```

- ディレクトリの一覧
```shell
$ ls
```

- PHPのバージョンを確認
```shell
$ php -v
```

- Laravelのバージョンを確認
```shell
$ laravel -V
```

### アプリケーション用ディレクトリを自動生成する
```shell
$ laravel new bbs
```


> [!TIP]
> `/usr/local/bin/laravel` は、Laravelのコマンドラインツール（CLI）がインストールされているディレクトリパスであり、`php artisan`コマンドのようなLaravelプロジェクトを管理するためのコマンドを実行する際に使われます。
> PHPのパッケージマネージャーであるComposerを使ってLaravelをインストールした場合、このパスにLaravelの実行ファイルが配置されることが一般的です



### Webサーバーを起動

```shell
$ cd bbs
$ php artisan serve
```

- ブラウザで以下にアクセスすると、アプリのWebページを表示する
    - https://localhost:8000/


なお、LaravelのサーバはHTTPで動作していますが、PaizaCloudではこれをHTTPSに変換しています。
また、サーバはlocalhostで動作していますが、PaizaCloudでは下記URLからlocalhostに接続できるようになっています。

 - https://localhost-*****.learning.paiza-user-learning.cloud:8000/

「*****」は、ランダムな値となります。


これらを実現するために、この講座であらかじめ用意されるLaravelアプリケーションでは、下記のとおりすべてのプロキシを信頼するように設定をしております。（この設定はPaizaCloud環境で演習をするために必要なものであり、例えば、ローカル環境などでLaravelアプリケーションを動作させるために必要な設定ではございません。）

app/Http/Middleware/TrustProxies.php の一部
```shell
protected $proxies = '*';

```

```shell
HTTP Requests - Laravel 7.x - The PHP Framework For Web Artisans
https://laravel.com/docs/7.x/requests#configuring-trusted-proxies
```

- プロキシ - Wikipedia
  - https://ja.wikipedia.org/wiki/%E3%83%97%E3%83%AD%E3%82%AD%E3%82%B7


Webサーバーを停止するには、ターミナルで、キーボードで「CTRL」キーを押しながら「C」のキーを押します。

### Artisanとは
  - ターミナルで「artisan」(アーティサン)コマンドを使ってLaravelの機能を呼び出すことができます。LaravelでWebアプリケーションを開発するときに役に立つ、数多くのコマンドを提供しています。

### 参考になるWebページ
Laravel - The PHP Framework For Web Artisans
https://laravel.com/

Artisan Console - Laravel 7.x - The PHP Framework For Web Artisans
https://laravel.com/docs/7.x/artisan

Laravel - Wikipedia
https://ja.wikipedia.org/wiki/Laravel

Laravel入門: 初心者でも10分でWebサービスを作れる！
PHPフレームワークLaravelとPaizaCloudの使い方 - paiza開発日誌
https://paiza.hatenablog.com/entry/2018/02/16/paizacloud_laravel

---

## 03:Laravel で HelloWorld

### Welcomeページを修正する
bbs/resources/views/welcome.blade.php

<div class='title m-b-md'>
    paiza bbs
</div>
<p><?= date('Y/m/d H:i:s') ?></p>


###  参考になるWebページ
- Laravel - The PHP Framework For Web Artisans
  - https://laravel.com/

- Artisan Console - Laravel 7.x - The PHP Framework For Web Artisans
  - https://laravel.com/docs/7.x/artisan

- Laravel - Wikipedia
  - https://ja.wikipedia.org/wiki/Laravel

- Laravel入門: 初心者でも10分でWebサービスを作れる！
PHPフレームワークLaravelとPaizaCloudの使い方 - paiza開発日誌
  - https://paiza.hatenablog.com/entry/2018/02/16/paizacloud_laravel


---

### データベース構成
1行掲示板のデータベースには、次の情報が必要になります。

- データベース : mybbs
- テーブル : articles
- カラム : id, content, created_at, updated_at

このデータベースは、phpMyAdminで用意しておきます。

###  アプリケーションのデータベース設定


アプリケーションからデータベースを呼び出すには、次のデータベース設定が必要です。

「.env」ファイルは、隠しファイルになっているので、「bbs」ディレクトリを右クリック->「隠しファイルを表示」で表示しておきます。

```shell
bbs/.env

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=mybbs
DB_USERNAME=root
# DB_PASSWORD=secret
```

### 参考になるWebページ
- Laravel - The PHP Framework For Web Artisans
  - https://laravel.com/

- Artisan Console - Laravel 7.x - The PHP Framework For Web Artisans
  - https://laravel.com/docs/7.x/artisan

- Laravel - Wikipedia
  - https://ja.wikipedia.org/wiki/Laravel

- Laravel入門: 初心者でも10分でWebサービスを作れる！
PHPフレームワークLaravelとPaizaCloudの使い方 - paiza開発日誌
  - https://paiza.hatenablog.com/entry/2018/02/16/paizacloud_laravel



---



## 05:モデルとコントローラを用意する


### モデルとマイグレーション、コントローラを作成
```shell
$ cd bbs
$ php artisan make:model Article -m -c -r
```


### contentカラムを追加

database/migrations/xxxx_xx_xx_xxxxxxxx_create_articles_table.php

```php
public function up()
    {
        Schema::create('articles', function (Blueprint $table) {
            $table->increments('id');
            $table->string('content');
            $table->timestamps();
        });
    }
```

###  マイグレーション実行

```php
$ php artisan migrate
```

###  参考になるWebページ
- Laravel - The PHP Framework For Web Artisans
  - https://laravel.com/

- Artisan Console - Laravel 7.x - The PHP Framework For Web Artisans
  - https://laravel.com/docs/7.x/artisan

- Laravel - Wikipedia
  - https://ja.wikipedia.org/wiki/Laravel

- Laravel入門: 初心者でも10分でWebサービスを作れる！
PHPフレームワークLaravelとPaizaCloudの使い方 - paiza開発日誌
  - https://paiza.hatenablog.com/entry/2018/02/16/paizacloud_laravel


---

## 06:ルーティングを定義しよう

### ルーティングとは
- どのアドレスにアクセスした時、どの機能を呼び出すか設定できます。
- LaravelによるWebアプリケーションでは、機能に応じて、アドレスを割り当てておきます。
- そして、ルーティングで、リクエストに応じて実行するコードを切り替えます。


### 1行掲示板のルーティング(一覧画面、詳細画面)

bbs/routes/web.php
```php
Route::get('/', function () {
    return view('welcome');
});

Route::get('/articles', 'ArticleController@index')->name('article.list');
Route::get('/article/{id}', 'ArticleController@show')->name('article.show');
```



###  paiza-cloud用https対応
app/Providers/AppServiceProvider.php
```php
class AppServiceProvider extends ServiceProvider
{
    /**
     * Bootstrap any application services.
     *
     * @return void
     */
    public function boot()
    {
        \URL::forceScheme('https');
    }

    /**
     * Register any application services.
     *
     * @return void
     */
    public function register()
    {
        //
    }
}
```


### 参考になるWebページ
- Laravel - The PHP Framework For Web Artisans
  - https://laravel.com/

- Artisan Console - Laravel 7.x - The PHP Framework For Web Artisans
  - https://laravel.com/docs/7.x/artisan

- Laravel - Wikipedia
  - https://ja.wikipedia.org/wiki/Laravel

- Laravel入門: 初心者でも10分でWebサービスを作れる！ PHPフレームワークLaravelとPaizaCloudの使い方 - paiza開発日誌
  - https://paiza.hatenablog.com/entry/2018/02/16/paizacloud_laravel


---

## 07:コントローラとビューを作成しよう

### コントローラからデータを渡す
bbs/app/Http/Controllers/ArticleController.php:
```php
<?php

namespace App\Http\Controllers;

use App\Article;
use Illuminate\Http\Request;

class ArticleController extends Controller
{
    /**
     * Display a listing of the resource.
     *
     * @return \Illuminate\Http\Response
     */
    public function index()
    {
        $message = 'Welcome to my BBS';
        return view('index', ['message' => $message]);
    }
}
```

### ビューでデータを表示する
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
    </body>
</html>
```


###  参考になるWebページ
- Laravel - The PHP Framework For Web Artisans
  - https://laravel.com/

- Artisan Console - Laravel 7.x - The PHP Framework For Web Artisans
  - https://laravel.com/docs/7.x/artisan

- Laravel - Wikipedia
  - https://ja.wikipedia.org/wiki/Laravel

- Laravel入門: 初心者でも10分でWebサービスを作れる！PHPフレームワークLaravelとPaizaCloudの使い方 - paiza開発日誌
  - https://paiza.hatenablog.com/entry/2018/02/16/paizacloud_laravel

---

## 08:記事一覧を作成しよう


### コントローラで、記事一覧を取得する
bbs/app/Http/Controllers/ArticleController.php:
```php
<?php

namespace App\Http\Controllers;

use App\Article;
use Illuminate\Http\Request;

class ArticleController extends Controller
{
    /**
     * Display a listing of the resource.
     *
     * @return \Illuminate\Http\Response
     */
    public function index()
    {
        $message = 'Welcome to my BBS';
        $articles = Article::all();
        return view('index', ['message' => $message, 'articles' => $articles]);
    }

}
```


### ビューで記事一覧を表示する
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
            <p>{{ $article->content }}</p>
        @endforeach
    </body>
</html>
```

### 参考になるWebページ
- Laravel - The PHP Framework For Web Artisans
  - https://laravel.com/

- Artisan Console - Laravel 7.x - The PHP Framework For Web Artisans
  - https://laravel.com/docs/7.x/artisan

- Laravel - Wikipedia
  - https://ja.wikipedia.org/wiki/Laravel

- Laravel入門: 初心者でも10分でWebサービスを作れる！PHPフレームワークLaravelとPaizaCloudの使い方 - paiza開発日誌
- https://paiza.hatenablog.com/entry/2018/02/16/paizacloud_laravel

---



## 09:詳細画面を作ろう


### bbs/app/Http/Controllers/ArticleController.php:
```php
public function show(Request $request, $id, Article $article)
{
    $message = 'This is your article ' . $id;
    $article = Article::find($id);
    return view('show', ['message' => $message, 'article' => $article]);
}
```

### showビューで、指定の記事を表示する
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

        <p>
            <a href={{ route('article.list') }}>一覧に戻る</a>
        </p>
    </body>
</html>
```

### 記事一覧から個別の記事にリンクする
bbs/resources/views/index.blade.php

```php
<!DOCTYPE html>
<html>
    <head>
        <mata charset="utf-8">
        <title>paiza bbs</title>
        <style>body {padding: 10px;}</style>
    </head>
    <body>
        <h1>paiza bbs</h1>
        <p>{{ $message }}</p>
        @foreach ($articles as $article)
            <p>
                <a href='{{ route("article.show", ["id" =>  $article->id]) }}'>
                    {{ $article->content }}
                </a>
            </p>
        @endforeach
    </body>
</html>
```

###  参考になるWebページ
- Laravel - The PHP Framework For Web Artisans
  - https://laravel.com/

- Artisan Console - Laravel 7.x - The PHP Framework For Web Artisans
  - https://laravel.com/docs/7.x/artisan

- Laravel - Wikipedia
  - https://ja.wikipedia.org/wiki/Laravel

- Laravel入門: 初心者でも10分でWebサービスを作れる！PHPフレームワークLaravelとPaizaCloudの使い方 - paiza開発日誌
  - https://paiza.hatenablog.com/entry/2018/02/16/paizacloud_laravel



---

【EOF】







[←　README](../README.md) 


