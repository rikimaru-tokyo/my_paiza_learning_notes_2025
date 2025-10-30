<!-- omit in toc -->
# paiza Lesson 4: 実用的なLaravelアプリを作ろう

https://paiza.jp/works/laravel/primer/beginner-laravel4

<!-- omit in toc -->
[目次]
- [01:アプリの概要を整理しよう](#01アプリの概要を整理しよう)
  - [作業手順](#作業手順)
  - [公式・総論](#公式総論)
  - [チュートリアル](#チュートリアル)
  - [データベースの準備](#データベースの準備)
  - [ルーティング](#ルーティング)
  - [コントローラを作る](#コントローラを作る)
  - [詳細ページを作る](#詳細ページを作る)
  - [リレーション](#リレーション)
- [02:アプリケーションディレクトリを用意しよう](#02アプリケーションディレクトリを用意しよう)
  - [このチャプターで使用したコマンド](#このチャプターで使用したコマンド)
  - [アプリケーション用ディレクトリを自動生成する](#アプリケーション用ディレクトリを自動生成する)
  - [ディレクトリ作成を高速化するには](#ディレクトリ作成を高速化するには)
  - [Webサーバを起動](#webサーバを起動)
  - [.envファイルを修正する](#envファイルを修正する)
  - [参考になるWebページ](#参考になるwebページ)
  - [laravelのバージョンアップによる変更点](#laravelのバージョンアップによる変更点)
  - [artisan make:modelで作成したマイグレーションファイル](#artisan-makemodelで作成したマイグレーションファイル)
  - [AppServiceProvider.phpの関数の順番が異なる](#appserviceproviderphpの関数の順番が異なる)
  - [404エラーのデザインが変わっている](#404エラーのデザインが変わっている)
  - [laravelの更新情報（英語）](#laravelの更新情報英語)
- [03:モデルとコントローラを用意しよう](#03モデルとコントローラを用意しよう)
  - [モデルファイルを作成](#モデルファイルを作成)
  - [※　【Laravel】「 php artisan make:model 」コマンドのオプション解説](#laravel-php-artisan-makemodel-コマンドのオプション解説)
  - [カテゴリーのマイグレーションファイルにカラムを追加](#カテゴリーのマイグレーションファイルにカラムを追加)
  - [Shopsマイグレーションファイルにカラムを追加](#shopsマイグレーションファイルにカラムを追加)
  - [マイグレーション実行](#マイグレーション実行)
  - [参考になるWebページ](#参考になるwebページ-1)
- [04:お店とカテゴリのテーブルを関連付けよう](#04お店とカテゴリのテーブルを関連付けよう)
  - [Shopモデルにリレーションを設定](#shopモデルにリレーションを設定)
  - [※　Laravelのリレーション（hasOne、hasMany、belongsTo）](#laravelのリレーションhasonehasmanybelongsto)
  - [※　LaravelのEloquent ORMでどっちがhasでどっちがbelongsなのか？](#laravelのeloquent-ormでどっちがhasでどっちがbelongsなのか)
  - [phpmyadminでサンプルデータを投入](#phpmyadminでサンプルデータを投入)
  - [PaizaCloud用https対応](#paizacloud用https対応)
  - [※　LaravelでURLをHTTPS化させるメモ](#laravelでurlをhttps化させるメモ)
  - [参考になるWebページ](#参考になるwebページ-2)
- [05:お店の一覧ページを作ろう](#05お店の一覧ページを作ろう)
  - [お店一覧のルーティングを定義する](#お店一覧のルーティングを定義する)
  - [コントローラにお店一覧を記述する](#コントローラにお店一覧を記述する)
  - [お店一覧のビューを作成する](#お店一覧のビューを作成する)
  - [参考になるWebページ](#参考になるwebページ-3)
    - [ルーティング](#ルーティング-1)
    - [コントローラを作る](#コントローラを作る-1)
- [06:共通テンプレートにBootstrapを導入しよう](#06共通テンプレートにbootstrapを導入しよう)
  - [layout.blade.phpを分離する](#layoutbladephpを分離する)
  - [index.blade.phpに、セクションを追加](#indexbladephpにセクションを追加)
  - [共通テンプレートにBootstrapを割り当てる](#共通テンプレートにbootstrapを割り当てる)
- [07:お店の詳細ページを作ろう](#07お店の詳細ページを作ろう)
  - [ルーティングを設定する](#ルーティングを設定する)
  - [コントローラを記述する](#コントローラを記述する)
  - [ビューを追加する](#ビューを追加する)
  - [お店一覧をテーブルタグにして、リンクを追加](#お店一覧をテーブルタグにしてリンクを追加)
- [08:新規投稿フォームを作ろう](#08新規投稿フォームを作ろう)
  - [ルーティングを設定する](#ルーティングを設定する-1)
  - [コントローラのcreate()を記述する](#コントローラのcreateを記述する)
  - [新規投稿フォームのビューを追加する](#新規投稿フォームのビューを追加する)
- [09:投稿フォームの内容を保存しよう](#09投稿フォームの内容を保存しよう)
  - [コントローラのstore()を記述する](#コントローラのstoreを記述する)
  - [一覧ページから新規投稿フォームにリンクする](#一覧ページから新規投稿フォームにリンクする)
- [10:お店の編集フォームを作ろう](#10お店の編集フォームを作ろう)
  - [ルーティングを設定する](#ルーティングを設定する-2)
  - [コントローラのedit()を追記](#コントローラのeditを追記)
  - [editビューを作成する](#editビューを作成する)
- [11:編集内容を更新しよう](#11編集内容を更新しよう)
  - [コントローラのupdate()を追記](#コントローラのupdateを追記)
  - [詳細ページからリンク](#詳細ページからリンク)
- [12:お店の情報を削除しよう](#12お店の情報を削除しよう)
  - [ルーティングを設定する](#ルーティングを設定する-3)
  - [コントローラにdestroyメソッドを追記](#コントローラにdestroyメソッドを追記)
  - [詳細ページに削除ボタンを追加](#詳細ページに削除ボタンを追加)
- [13:Googleマップを表示しよう](#13googleマップを表示しよう)
  - [APIとは](#apiとは)
  - [Google Maps API](#google-maps-api)
  - [詳細ページのビューにマップを追加](#詳細ページのビューにマップを追加)



---


## 01:アプリの概要を整理しよう

![](./images/lesson0401.png)


![](./images/lesson0402.png)


![](./images/lesson0403.png)


![](./images/lesson0404.png)


### 作業手順
- アプリケーションディレクトリを準備する
- モデルとコントローラを用意する
- お店とカテゴリのテーブルを関連付ける
- お店一覧ページを作る
- 共通テンプレートにBootstrapを導入する
- 詳細ページを作る
- 新規投稿フォームを作る
- 投稿内容を保存する
- 編集フォームを作る
- 編集内容を更新する
- お店情報を削除する
- Googleマップを表示する


### 公式・総論
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


### データベースの準備
- Eloquent：利用の開始 5.7 Laravel
  - https://readouble.com/laravel/5.7/ja/eloquent.html

- Eloquent：リレーション 5.7 Laravel
  - https://readouble.com/laravel/5.7/ja/eloquent-relationships.html

- Laravelでの基本的なリレーションシップもしくはJOIN - Qiita
  - https://qiita.com/zaburo/items/d665804f8ea850502c64


### ルーティング

- ルーティング 5.6 Laravel
  - https://readouble.com/laravel/5.7/ja/routing.html

- Laravelルーティングの基本とよく使われるルーティングパターン
  - https://www.ritolab.com/entry/119



### コントローラを作る

- コントローラ 5.7 Laravel
  - https://readouble.com/laravel/5.7/ja/controllers.html

- 【Laravel入門】コントローラの作成とビュー表示 - Qiita
  - https://qiita.com/33yuki/items/7bab0d596ae9a0930f18


### 詳細ページを作る

- URL生成 5.7 Laravel
  - https://readouble.com/laravel/5.7/ja/urls.html


### リレーション

- 【Laravel入門】リレーションとユーザーの一覧表示 - Qiita
  - https://qiita.com/33yuki/items/b7186f05d1c266076a35

- Laravel5.4で基本的なリレーションを学んでみる | webOpixel
  - https://www.webopixel.net/php/1261.html


---



## 02:アプリケーションディレクトリを用意しよう

### このチャプターで使用したコマンド

カレントディレクトリの確認

```bash
$ pwd
```

ディレクトリの一覧
```bash
$ ls
```


PHPのバージョンを確認
```bash
$ php -v
```

Laravelのバージョンを確認
```bash
$ laravel -V
```


### アプリケーション用ディレクトリを自動生成する
```bash
$ laravel new lunchmap
```


### ディレクトリ作成を高速化するには

"laravel new"コマンドの実行前に以下のような設定をしておけば、コマンドの実行時間を短くできます。

```bash
$ composer config -g repositories.packagist composer 'https://packagist.jp'
$ composer global require hirak/prestissimo
```


###  Webサーバを起動
```bash
$ cd lunchmap
$ php artisan serve
```

ブラウザで以下にアクセスすると、アプリのWebページを表示する
```bash
https://localhost:8000/
```

Webサーバを停止するには、ターミナルで、キーボードで「CTRL」キー(コントロールキー)を押しながら「C」のキーを押す。


### .envファイルを修正する
lunchmap/.env

```ini
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=lunchmapdb
DB_USERNAME=root
# DB_PASSWORD=secret
```


### 参考になるWebページ

- Eloquent：利用の開始 5.7 Laravel
  - https://readouble.com/laravel/5.7/ja/eloquent.html
- Eloquent：リレーション 5.7 Laravel
  - https://readouble.com/laravel/5.7/ja/eloquent-relationships.html
- Laravelでの基本的なリレーションシップもしくはJOIN - Qiita
  - https://qiita.com/zaburo/items/d665804f8ea850502c64


### laravelのバージョンアップによる変更点
動画ではlaravel5.7を使用していますが、現在はより新しいLaravel5.8が公開されています。

`$ laravel new`で作成したプロジェクトはその時点で最新のLaravelがダウンロードされるため、時期によっては動画と全く同じコードでは無いかもしれませんが2019年3月現在大幅な変更はされていないので大きな影響はありません。


例えば、以下のような違いが見られる場合があります。


### artisan make:modelで作成したマイグレーションファイル
以前はidカラムが`increments`で定義されていましたが、新しく`bigIncrements`で定義されるようになります。

これはデータベースのカラムの型に影響し

```bash
increments() : 符号なし4byte整数
bigIncrements() : 符号なし8byte整数
```

となります。

`符号なし8byte整数(2\^64通り)`は、`符号なし4byte整数(2\^32通り)の2\^32倍 = 4,294,967,295倍`もの空間を持っています。

`bigIncrements()`でIDを定義すると`increments()`にくらべてこれだけの余裕ができ、より多くのデータを格納できるようになるというわけです。
```php
    public function up()
    {
        Schema::create('Shop', function (Blueprint $table) {
            // ここがbigIncrementsになっている
            $table->bigIncrements('id');
            $table->timestamps();
        });
    }
```

### AppServiceProvider.phpの関数の順番が異なる
`AppServiceProvider.php`の関数が動画と違う並び順になっている場合があります。
並び順が異なるだけでメソッドそのものは変わっていませんので、目的のメソッドの位置を確認してください。

paiza cloud向けのHTTPSの設定はboot()メソッドに記述します。
```php
class AppServiceProvider extends ServiceProvider
{
    // メソッドの並び順が逆になっている
    public function register()
    {
        //
    }

    public function boot()
    {
        //
    }
}
```

### 404エラーのデザインが変わっている
404エラーが発生した場合（アクセス先のURLを間違えた場合など）に表示されてるエラーページのデザインがシンプルなものへ変更されました。
paizaラーニングの講座でも存在しないURLへアクセスすれば表示されますので、興味があれば確認してみましょう。


### laravelの更新情報（英語）
- [Release Notes - Laravel](https://laravel.com/docs/5.8/releases)
- [Laravel News](https://laravel-news.com/)



---

## 03:モデルとコントローラを用意しよう

### モデルファイルを作成

```bash
$ cd lunchmap
$ php artisan make:model Category -m
$ php artisan make:model Shop -m -c -r
```

### ※　【Laravel】「 php artisan make:model 」コマンドのオプション解説

- https://qiita.com/Masahiro111/items/f6201b1e89fb6cfddc09
- https://qiita.com/RealXiaoLin/items/2e8dd653306c88e7e1df


- --controller, -c オプション : モデルの新しいコントローラを作成します。
- --resource, -r オプション : 生成されたコントローラをリソースコントローラにする必要があるかどうかを示します。CRUD を作成するアプリケーションに便利なオプションです。
- --migration, -m オプション : モデルの新しいマイグレーションファイルを作成します。



### カテゴリーのマイグレーションファイルにカラムを追加
database/migrations/2019_xx_xx_xxxxxxxx_create_categories_table.php

```php
    public function up()
    {
        Schema::create('categories', function (Blueprint $table) {
            $table->increments('id');
            $table->string('name');
            $table->timestamps();
        });
    }
```


### Shopsマイグレーションファイルにカラムを追加
database/migrations/2019_xx_xx_xxxxxxxx_create_shops_table.php

```php
    public function up()
    {
        Schema::create('shops', function (Blueprint $table) {
            $table->increments('id');
            $table->string('name');
            $table->string('address');
            $table->integer('category_id');
            $table->timestamps();
        });
    }
```

###  マイグレーション実行
```bash
$ php artisan migrate
```

### 参考になるWebページ
- Eloquent：利用の開始 5.7 Laravel
  - https://readouble.com/laravel/5.7/ja/eloquent.html
- Eloquent：リレーション 5.7 Laravel
  - https://readouble.com/laravel/5.7/ja/eloquent-relationships.html
- Laravelでの基本的なリレーションシップもしくはJOIN - Qiita
  - https://qiita.com/zaburo/items/d665804f8ea850502c64



---

## 04:お店とカテゴリのテーブルを関連付けよう


###  Shopモデルにリレーションを設定
app/Shop.php

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class Shop extends Model
{
    public function category()
    {
        //ShopモデルはCategoryに所属している
        return $this->belongsTo('App\Category');
    }
}
```

### ※　Laravelのリレーション（hasOne、hasMany、belongsTo）

- https://qiita.com/yukachin0414/items/726f3cbf4270f50f6028


- ① hasOne（1対1）：主テーブルのあるレコードに対して、従テーブルの1つのレコードが紐付けられる
- ② hasMany（1対多）：hasManyは主テーブルのあるレコードに対して、従テーブルの複数のレコードが紐付ける
- ③ belongsTo：従テーブルの複数レコードに対して、主テーブルの1つのレコードが紐付けるとき

### ※　LaravelのEloquent ORMでどっちがhasでどっちがbelongsなのか？

- https://qiita.com/kutarou197/items/bad6c9b5ee22cdd7e2d6

- https://readouble.com/laravel/5.8/ja/eloquent-relationships.html#one-to-one-polymorphic-relations

- https://dexall.co.jp/articles/?p=2509

> [!TIP]
> belongsToリレーションは、1対多（One-to-Many）関係における「多」側のモデルで定義されるリレーションです。



![](./images/lesson0405.png)


### phpmyadminでサンプルデータを投入

通常は`Laravel Seeder`でテストデータを作れる。

categoriesテーブル
```sql
INSERT INTO categories(name)
VALUES
    ('イタリアン'),
    ('中華'),
    ('和食');
```

shopsテーブル
```sql
INSERT INTO shops(name,address,category_id)
VALUES
    ('パイザ亭', '東京都港区南青山3丁目', 1),
    ('ラーメンLaravel', '東京都港区東青山', 2),
    ('そばの霧島', '東京都港区西青山', 3);
```


### PaizaCloud用https対応
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
        //生成されるURLのスキーム（プロトコル）を強制的に変更するためのメソッド
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

### ※　LaravelでURLをHTTPS化させるメモ

- https://qiita.com/ghibi/items/cb4faa2d86f5866cbfd4

### 参考になるWebページ
- Eloquent：利用の開始 5.7 Laravel
  - https://readouble.com/laravel/5.7/ja/eloquent.html
- Eloquent：リレーション 5.7 Laravel
  - https://readouble.com/laravel/5.7/ja/eloquent-relationships.html
- Laravelでの基本的なリレーションシップもしくはJOIN - Qiita
  - https://qiita.com/zaburo/items/d665804f8ea850502c64
- 【Laravel入門】リレーションとユーザーの一覧表示 - Qiita
  - https://qiita.com/33yuki/items/b7186f05d1c266076a35
- Laravel5.4で基本的なリレーションを学んでみる | webOpixel
  - https://www.webopixel.net/php/1261.html

---


## 05:お店の一覧ページを作ろう

### お店一覧のルーティングを定義する
routes/web.php

```php
<?php

Route::get('/shops', 'ShopController@index')->name('shop.list');

Route::get('/', function () {
    return redirect('/shops');
});
```

###  コントローラにお店一覧を記述する
app/Http/Controllers/ShopController.php

```php
<?php

namespace App\Http\Controllers;

use App\Shop;
use Illuminate\Http\Request;

class ShopController extends Controller
{
    public function index()
    {
        $shops = Shop::all();
        return view('index', ['shops' => $shops]);
    }
}
```


### お店一覧のビューを作成する
resources/views/index.blade.php
```php
<!DOCTYPE html>
<html>
    <head>
        <meta charset='utf-8'>
        <title>Lunchmap</title>
        <style>body {padding: 10px;}</style>
    </head>
    <body>
        <h1>お店一覧</h1>

        @foreach ($shops as $shop)
            <p>
                {{ $shop->category->name }},
                {{ $shop->name }},
                {{ $shop->address }}
            </p>
        @endforeach
    </body>
</html>
```

### 参考になるWebページ

#### ルーティング

- ルーティング 5.6 Laravel
  - https://readouble.com/laravel/5.7/ja/routing.html
- Laravelルーティングの基本とよく使われるルーティングパターン
  - https://www.ritolab.com/entry/119


#### コントローラを作る

- コントローラ 5.7 Laravel
  - https://readouble.com/laravel/5.7/ja/controllers.html
- 【Laravel入門】コントローラの作成とビュー表示 - Qiita
  - https://qiita.com/33yuki/items/7bab0d596ae9a0930f18



---


## 06:共通テンプレートにBootstrapを導入しよう

###  layout.blade.phpを分離する
resources/views/layout.blade.php

```php
<!DOCTYPE html>
<html>
    <head>
        <meta charset='utf-8'>
        <title>Lunchmap</title>
        <style>body {padding: 80px;}</style>
    </head>
    <body>
        @yield('content')
    </body>
</html>
```

### index.blade.phpに、セクションを追加

resources/views/index.blade.php

```php
@extends('layout')

@section('content')
    <h1>お店一覧</h1>

    @foreach ($shops as $shop)
        <p>
            {{ $shop->category->name }},
            {{ $shop->name }},
            {{ $shop->address }}
        </p>
    @endforeach
@endsection
```


### 共通テンプレートにBootstrapを割り当てる
resources/views/layout.blade.php

```php
<!DOCTYPE html>
<html>
    <head>
        <meta charset='utf-8'>
        <meta name='viewport' content='width=device-width, initial-scale=1, shrink-to-fit=no'>
        <link rel='stylesheet' href='https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css' >
        <title>Lunchmap</title>
        <style>body {padding-top: 80px;}</style>
    </head>
    <body>
        <nav class='navbar navbar-expand-md navbar-dark bg-dark fixed-top'>
            <a class='navbar-brand' href={{route('shop.list')}}>Lunchmap</a>
        </nav>
        <div class='container'>
            @yield('content')
        </div>
    </body>
</html>
```


---


## 07:お店の詳細ページを作ろう


### ルーティングを設定する

routes/web.php
```php
Route::get('/shops', 'ShopController@index')->name('shop.list');
Route::get('/shop/{id}', 'ShopController@show')->name('shop.detail');

Route::get('/', function () {
    return redirect('/shops');
});
```

### コントローラを記述する

app/Http/Controllers/ShopController.php

```php
    /**
     * Display the specified resource.
     *
     * @param  \App\Shop  $shop
     * @return \Illuminate\Http\Response
     */
    public function show($id)
    {
        $shop = Shop::find($id);
        return view('show', ['shop' => $shop]);
    }
```


### ビューを追加する
resources/views/show.blade.php

```php
@extends('layout')

@section('content')
    <h1>{{ $shop->name }}</h1>
    <div>
        <p>{{ $shop->category->name }}</p>
        <p>{{ $shop->address }}</p>
    </div>
    <div>
        <a href={{ route('shop.list') }}>一覧に戻る</a>
    </div>
@endsection
```


### お店一覧をテーブルタグにして、リンクを追加
resources/views/index.blade.php

```php
@extends('layout')

@section('content')
    <h1>お店一覧</h1>

    <table class='table table-striped table-hover'>
        <tr>
            <th>カテゴリ</th><th>店名</th><th>住所</th>
        </tr>
        @foreach ($shops as $shop)
            <tr>
                <td>{{ $shop->category->name }}</td>
                <td>
                    <a href={{ route('shop.detail', ['id' =>  $shop->id]) }}>
                        {{ $shop->name }}
                    </a>
                </td>
                <td>{{ $shop->address }}</td>
            </tr>
        @endforeach
    </table>
@endsection
```

---

## 08:新規投稿フォームを作ろう

### ルーティングを設定する
routes/web.php

```php
Route::get('/shops', 'ShopController@index')->name('shop.list');
Route::get('/shop/new', 'ShopController@create')->name('shop.new');
Route::post('/shop', 'ShopController@store')->name('shop.store');

Route::get('/shop/{id}', 'ShopController@show')->name('shop.detail');

Route::get('/', function () {
    return redirect('/shops');
});
```


### コントローラのcreate()を記述する
app/Http/Controllers/ShopController.php:

```php
<?php

namespace App\Http\Controllers;

use App\Shop;
use App\Category;
use Illuminate\Http\Request;


    /**
     * Show the form for creating a new resource.
     *
     * @return \Illuminate\Http\Response
     */
    public function create()
    {
        //pluck() : キーがidでバリューがnameのコレクションを生成
        $categories = Category::all()->pluck('name', 'id');
        return view('new', ['categories' => $categories]);
    }
```

### 新規投稿フォームのビューを追加する
resources/views/new.blade.php

```php
@extends('layout')

@section('content')
    <h1>新しいお店</h1>
    {{ Form::open(['route' => 'shop.store']) }}
        <div class='form-group'>
            {{ Form::label('name', '店名:') }}
            {{ Form::text('name', null) }}
        </div>
        <div class='form-group'>
            {{ Form::label('address', '住所:') }}
            {{ Form::text('address', null) }}
        </div>
        <div class='form-group'>
            {{ Form::label('category_id', 'カテゴリ:') }}
            {{ Form::select('category_id', $categories) }}
        </div>
        <div class="form-group">
            {{ Form::submit('作成する', ['class' => 'btn btn-outline-primary']) }}
        </div>
    {{ Form::close() }}

    <div>
        <a href={{ route('shop.list') }}>一覧に戻る</a>
    </div>

@endsection
```

---


## 09:投稿フォームの内容を保存しよう


### コントローラのstore()を記述する
app/Http/Controllers/ShopController.php:
```php
    /**
     * Store a newly created resource in storage.
     *
     * @param  \Illuminate\Http\Request  $request
     * @return \Illuminate\Http\Response
     */
    public function store(Request $request)
    {
        $shop = new Shop;
        $shop->name = request('name');
        $shop->address = request('address');
        $shop->category_id = request('category_id');
        $shop->save();
        return redirect()->route('shop.detail', ['id' => $shop->id]);
    }
```


### 一覧ページから新規投稿フォームにリンクする
resources/views/index.blade.php
```php
@extends('layout')

@section('content')
    <h1>お店一覧</h1>

    <table class='table table-striped table-hover'>
        <tr>
            <th>カテゴリ</th><th>店名</th><th>住所</th>
        </tr>
        @foreach ($shops as $shop)
            <tr>
                <td>{{ $shop->category->name }}</td>
                <td>
                    <a href={{ route('shop.detail', ['id' =>  $shop->id]) }}>
                        {{ $shop->name }}
                    </a>
                </td>
                <td>{{ $shop->address }}</td>
            </tr>
        @endforeach
    </table>

    <div>
        <a href={{ route('shop.new') }} class='btn btn-outline-primary'>新しいお店</a>
    <div>
@endsection
```



---


## 10:お店の編集フォームを作ろう


### ルーティングを設定する
routes/web.php
```php
Route::get('/shops', 'ShopController@index')->name('shop.list');
Route::get('/shop/new', 'ShopController@create')->name('shop.new');
Route::post('/shop', 'ShopController@store')->name('shop.store');
Route::get('/shop/edit/{id}', 'ShopController@edit')->name('shop.edit');
Route::post('/shop/update/{id}', 'ShopController@update')->name('shop.update');

Route::get('/shop/{id}', 'ShopController@show')->name('shop.detail');

Route::get('/', function () {
    return redirect('/shops');
});
```

### コントローラのedit()を追記
app/Http/Controllers/ShopController.php:
```php
    public function edit($id)
    {
        $shop = Shop::find($id);
        $categories = Category::all()->pluck('name', 'id');
        return view('edit', ['shop' => $shop, 'categories' => $categories]);
    }
```


### editビューを作成する
resources/views/edit.blade.php
```php
@extends('layout')

@section('content')
    <h1>{{$shop->name}}を編集する</h1>
    {{ Form::model($shop, ['route' => ['shop.update', $shop->id]]) }}
        <div class='form-group'>
            {{ Form::label('name', '店名:') }}
            {{ Form::text('name', null) }}
        </div>
        <div class='form-group'>
            {{ Form::label('address', '住所:') }}
            {{ Form::text('address', null) }}
        </div>
        <div class='form-group'>
            {{ Form::label('category_id', 'カテゴリ:') }}
            {{ Form::select('category_id', $categories) }}
        </div>
        <div class="form-group">
            {{ Form::submit('更新する', ['class' => 'btn btn-outline-primary']) }}
        </div>
    {{ Form::close() }}

    <div>
        <a href={{ route('shop.list') }}>一覧に戻る</a>
    </div>

@endsection
```


---


## 11:編集内容を更新しよう



> [!TIP]
> Laravelのコントローラーメソッドの引数の順番は、次の優先順位で解決されます。<br>
> フォームリクエスト： 引数の位置に関係なく、最初に解決されます。<br>
> ルーティングのパラメーター： $idなどのルートパラメーターは、ルーティングで記述された順番で渡されます。<br>
> ルートモデルバインディング： モデルの引数も、ルーティングのパラメーター名と順番に基づいて解決されます。


### コントローラのupdate()を追記
app/Http/Controllers/ShopController.php:
```php
/**
     * Store a newly created resource in storage.
     *
     * @param  \Illuminate\Http\Request  $request
     * @return \Illuminate\Http\Response
     */
     public function update(Request $request, $id, Shop $shop)
     {
         $shop = Shop::find($id);
         $shop->name = request('name');
         $shop->address = request('address');
         $shop->category_id = request('category_id');
         $shop->save();
         return redirect()->route('shop.detail', ['id' => $shop->id]);
     }
```

### 詳細ページからリンク
resources/views/show.blade.php
```php
@extends('layout')

@section('content')
    <h1>{{ $shop->name }}</h1>
    <div>
        <p>{{ $shop->category->name }}</p>
        <p>{{ $shop->address }}</p>
    </div>

    <div>
        <a href={{ route('shop.list' )}}>一覧に戻る</a>
         | <a href={{ route('shop.edit', ['id' =>  $shop->id]) }}>編集</a>
    </div>
@endsection
```


---

## 12:お店の情報を削除しよう

###  ルーティングを設定する
routes/web.php
```php
Route::get('/shops', 'ShopController@index')->name('shop.list');
Route::get('/shop/new', 'ShopController@create')->name('shop.new');
Route::post('/shop', 'ShopController@store')->name('shop.store');
Route::get('/shop/edit/{id}', 'ShopController@edit')->name('shop.edit');
Route::post('/shop/update/{id}', 'ShopController@update')->name('shop.update');

Route::get('/shop/{id}', 'ShopController@show')->name('shop.detail');
Route::delete('/shop/{id}', 'ShopController@destroy')->name('shop.destroy');

Route::get('/', function () {
    return redirect('/shops');
});
```


### コントローラにdestroyメソッドを追記
app/Http/Controllers/ShopController.php:
```php
    public function destroy($id)
    {
        $shop = Shop::find($id);
        $shop->delete();
        return redirect('/shops');
    }
```



### 詳細ページに削除ボタンを追加
resources/views/show.blade.php
```php
@extends('layout')

@section('content')
    <h1>{{ $shop->name }}</h1>
    <div>
        <p>{{ $shop->category->name }}</p>
        <p>{{ $shop->address }}</p>
    </div>

    <div>
        <a href={{ route('shop.list' )}}>一覧に戻る</a>
         | <a href={{ route('shop.edit', ['id' =>  $shop->id]) }}>編集</a>
        <p></p>
        {{ Form::open(['method' => 'delete', 'route' => ['shop.destroy', $shop->id]]) }}
            {{ Form::submit('削除') }}
        {{ Form::close() }}
    </div>
@endsection
```
---

## 13:Googleマップを表示しよう


### APIとは

APIとは、Application Programming Interfaceの略で、プログラムから別のプログラムの機能を呼び出すために用意された命令や関数のこと。

### Google Maps API
- Google Maps Platform - Geo-location API
  - https://cloud.google.com/maps-platform/
- Developer Guide | Maps Embed API | Google Developers
  - https://developers.google.com/maps/documentation/embed/guide

- APIキーの取得手順
1. Google Developers Consoleにアクセスする
     - Google Developers Console
       - https://console.developers.google.com/
2. プロジェクトを作成を選択
3. Google APIが表示されたら、Google Maps APIから「Google Maps Embed API」を選択
4. 「有効にする」をクリック
5. 「認証情報を作成」をクリックして、「必要な認証情報」ボタンをクリック
6. 表示されたAPIキーを記録する

※特定のWebサービスだけから利用できるよう、「API利用制限」を設定することをオススメします。
※この手順や利用範囲はGoogle側で変更される場合があります。


### 詳細ページのビューにマップを追加
resources/views/show.blade.php

```php
@extends('layout')

@section('content')
    <h1>{{ $shop->name }}</h1>
    <div>
        <p>{{ $shop->category->name }}</p>
        <p>{{ $shop->address }}</p>
    </div>

    <iframe id='map' src='https://www.google.com/maps/embed/v1/place?key=AIzaSyCJBgcuCowQa5-V8owXaUCHhUNBN8bfMfU&amp;q={{ $shop->address }}'
    width='100%'
    height='320'
    frameborder='0'>
    </iframe>

    <div>
        <a href={{ route('shop.list' )}>一覧に戻る</a>
    </div>
@endsection
```



---


【EOF】







[←　README](../README.md) 