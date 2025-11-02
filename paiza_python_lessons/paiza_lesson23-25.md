<!-- omit in toc -->
paiza ラーニング　：　新・Python入門編 Lesson 23 ～ 25

<!-- omit in toc -->
# 目次
- [23: モジュールを理解しよう](#23-モジュールを理解しよう)
  - [01:ローカル環境で Python コードを実行](#01ローカル環境で-python-コードを実行)
  - [py ファイルを作成してコードを書く](#py-ファイルを作成してコードを書く)
  - [02:ローカル環境で入力値を受け取るコードを実行](#02ローカル環境で入力値を受け取るコードを実行)
    - [ローカル環境で入力値を受け取る](#ローカル環境で入力値を受け取る)
  - [03:モジュールをインポート (import)](#03モジュールをインポート-import)
    - [import 文](#import-文)
  - [from 節](#from-節)
  - [05:インポートしたオブジェクトが代入される変数の名前を指定 (as)](#05インポートしたオブジェクトが代入される変数の名前を指定-as)
    - [as 節](#as-節)
    - [from 節を使った場合も as 節を使うことができる](#from-節を使った場合も-as-節を使うことができる)
  - [06:モジュール内の変数やクラスを利用](#06モジュール内の変数やクラスを利用)
  - [07:複数のモジュールを一括で管理](#07複数のモジュールを一括で管理)
    - [パッケージ](#パッケージ)
  - [08:モジュールの名前を確認 (__name__)](#08モジュールの名前を確認-name)
    - [変数 __name__](#変数-name)
    - [`__mro__` を使ったときに出力された `__main__` について](#__mro__-を使ったときに出力された-__main__-について)
  - [!!!!! 09:モジュールの処理を制御 (if __name__ == "__main__")](#-09モジュールの処理を制御-if-name--main)
    - [!!! if __name__ == "__main__"](#-if-name--main)
  - [10:モジュールの利点](#10モジュールの利点)
  - [11:標準ライブラリ](#11標準ライブラリ)
    - [標準ライブラリ](#標準ライブラリ)
    - [リンク](#リンク)
  - [12:random モジュール](#12random-モジュール)
    - [random モジュール](#random-モジュール)
  - [13:math モジュール](#13math-モジュール)
  - [14:sys モジュール](#14sys-モジュール)
- [Lesson 24: 例外処理を理解しよう](#lesson-24-例外処理を理解しよう)
  - [01:例外・例外処理とはなにか](#01例外例外処理とはなにか)
    - [例外とはなにか](#例外とはなにか)
    - [例外処理とはなにか](#例外処理とはなにか)
  - [02:try 文の書き方 (try - except)](#02try-文の書き方-try---except)
  - [03:はじめての try 文](#03はじめての-try-文)
    - [try 文の書き順](#try-文の書き順)
  - [04:複数の例外を受ける except 節](#04複数の例外を受ける-except-節)
  - [05:複数の except 節](#05複数の-except-節)
    - [except 節は複数用意することができる](#except-節は複数用意することができる)
  - [06:例外クラスの継承関係と except 節](#06例外クラスの継承関係と-except-節)
    - [動画内で使う try 文のコード](#動画内で使う-try-文のコード)
    - [except 節で受ける例外](#except-節で受ける例外)
    - [BaseException クラスと Exception クラスの違い](#baseexception-クラスと-exception-クラスの違い)
  - [07:例外クラスのインスタンスを生成](#07例外クラスのインスタンスを生成)
    - [例外クラスのインスタンスを生成することができる](#例外クラスのインスタンスを生成することができる)
  - [08:例外を意図的に発生させる (raise)](#08例外を意図的に発生させる-raise)
    - [raise 文](#raise-文)
  - [09:独自の例外クラスを定義](#09独自の例外クラスを定義)
    - [※　【初心者向け】エラーを握りつぶすことの問題と対処法](#初心者向けエラーを握りつぶすことの問題と対処法)
      - [なぜ例外を握りつぶしてはいけないのか](#なぜ例外を握りつぶしてはいけないのか)
      - [例外を握りつぶさないための対処法](#例外を握りつぶさないための対処法)
- [Lesson 25: !!!!! イミュータブルとミュータブルを学習しよう](#lesson-25--イミュータブルとミュータブルを学習しよう)
  - [「オブジェクト」は抽象的で、幅広く使われる](#オブジェクトは抽象的で幅広く使われる)
  - [02:オブジェクトのid](#02オブジェクトのid)
    - [id 関数](#id-関数)
    - [累算代入をしたときのオブジェクトの id](#累算代入をしたときのオブジェクトの-id)
  - [03:イミュータブルなオブジェクトとはなにか](#03イミュータブルなオブジェクトとはなにか)
  - [04:ミュータブルなオブジェクトとはなにか](#04ミュータブルなオブジェクトとはなにか)
  - [05:idと変数と代入](#05idと変数と代入)
  - [06:イミュータブルなオブジェクトが代入された変数](#06イミュータブルなオブジェクトが代入された変数)
  - [07:ミュータブルなオブジェクトが代入された変数](#07ミュータブルなオブジェクトが代入された変数)
    - [※　Python のミュータブルとイミュータブル：違いと意味解説](#python-のミュータブルとイミュータブル違いと意味解説)
      - [1.1 不変オブジェクト（Immutable Objects）](#11-不変オブジェクトimmutable-objects)
      - [1.2 可変オブジェクト（Mutable Objects）](#12-可変オブジェクトmutable-objects)
      - [2. 不変オブジェクトのメリットとデメリット](#2-不変オブジェクトのメリットとデメリット)
      - [2.1 メリット](#21-メリット)
      - [2.2 デメリット](#22-デメリット)
      - [3. 可変オブジェクトのメリットとデメリット](#3-可変オブジェクトのメリットとデメリット)
      - [3.1 メリット](#31-メリット)
      - [3.2 デメリット](#32-デメリット)
      - [4. 適切な使用シーン](#4-適切な使用シーン)
      - [4.1 不変オブジェクトの適切な使用シーン](#41-不変オブジェクトの適切な使用シーン)
      - [4.2 可変オブジェクトの適切な使用シーン](#42-可変オブジェクトの適切な使用シーン)
      - [5. ベストプラクティス](#5-ベストプラクティス)
  - [08:関数の引数](#08関数の引数)
    - [関数の仮引数の渡され方](#関数の仮引数の渡され方)
    - [関数内の処理が与える影響](#関数内の処理が与える影響)




<br>

---

<br>

# 23: モジュールを理解しよう

## 01:ローカル環境で Python コードを実行

- Python のコードを、各自のコンピュータのターミナルなどで実行することを「ローカル環境で Python コードを実行する」という

- paiza ラーニングでは、ローカル環境を再現するために、PaizaCloudを活用する。
https://paiza.cloud/ja/


## py ファイルを作成してコードを書く


```python
# /home/ubuntu/test.py
print("Hello, World!")
```

ターミナルで py ファイルを実行する

```bash
python3 test.py
```

  - 実行するとき、カレントディレクトリに test.py が存在するか確認する (例では、/home/ubuntu) にいるかどうか注意
    - 現在のディレクトリを確認する: `pwd`
    - 指定のディレクトリに移動する: `cd /home/ubuntu`

  - ターミナルでの操作も学びたい方には、シェルコマンド入門編1がオススメです。
    - https://paiza.jp/works/shellcommand/primer/shell-command-primer-01


## 02:ローカル環境で入力値を受け取るコードを実行


### ローカル環境で入力値を受け取る
  - ローカル環境で input 関数を実行すると、ターミナルに入力した文字列を受け取ることができる

py ファイル:
```python
# /home/ubuntu/test.py
s = input()
print(s)
```

実行コード:
```bash
python3 test.py
```

  - 実行すると、入力待ちの状態になるため、なにかターミナルに入力する
    - input 関数に引数を渡すと、入力待ちの状態になったとき、その値が表示される

py ファイル:
```python
# /home/ubuntu/test.py

s = input("ENTER YOUR NAME: ")
print(s)
```

実行コード:
```bash
python3 test.py
```




## 03:モジュールをインポート (import)


### import 文
- `import 文`を使うと、モジュールをインポートすることができる。
- 「モジュールをインポートする」とは、他の py ファイルをコードのなかに取り込んで、その py ファイルに書かれているコードを利用できるようにすることを指す。
- import 文は import インポートしたいモジュールの名前 のように使う。

py ファイル:
```python
# /home/ubuntu/test.py

import testmod
testmod.hello()
```

- モジュール名: 取り込みたいモジュールの名前から、 .py を除いたもの。
- インポートの際は、import 文で指定したモジュールから、module クラスのインスタンスが生成される。
- インスタンスが代入される変数の名前は、特に指定しない限り、モジュールの名前とおなじ。
- py ファイルに定義されている関数は、インポートの際に module クラスのインスタンスの属性になる。
- そのため、testmod モジュールの hello メソッドを呼び出す際は testmod.hello と書く。

実行コード:
```bash
python3 test.py
```


##  from 節

  - from 節を使うと、モジュールに定義されている`特定の関数などを指定してインポート`することができる

py ファイル:
```python
# /home/ubuntu/test.py
from testmod import hello
hello()
```

- from モジュール名 import インポートしたい関数などの名前のように使う
- testmod モジュールから hello 関数をインポートしている

実行コード:
```bash
python3 test.py
```

## 05:インポートしたオブジェクトが代入される変数の名前を指定 (as)

### as 節

as 節を使うとインポートしたオブジェクトが代入される変数名を指定することができる

py ファイル:
```python
import testmod as tm

tm.hello()
```

  - `import モジュール名 as 変数名` のように使う
  - testmod モジュールをインポートして、変数 tm に代入している

実行コード:
```bash
python3 test.py
```



### from 節を使った場合も as 節を使うことができる

py ファイル:
```python
# /home/ubuntu/test.py
from testmod import hello as hl
hl()
```

- testmod モジュールの hello 関数をインポートして、変数 h1 に代入している


実行コード:
```bash
python3 test.py
```



## 06:モジュール内の変数やクラスを利用


  - インポートしたモジュールに含まれる変数やクラスを利用することもできる

testmod.pyの中身:
```python

PI = 3.14

class Circle:
    def init_(self, x, y, r):
        self. x = x
        self.y = y
        self.r = r
```


py ファイル:
```python
# /home/ubuntu/test.py
import testmod

print(testmod.PI)
c = testmod.Circle(0, 0, 5)
print(c.x, c.y, c.r)
```

```bash
python3 test.py
```


- from 節を使って、次のようにも書ける

py ファイル:
```python
# /home/ubuntu/test.py
from testmod import PI, Circle

print(PI)
c = Circle(0, 0, 5)
print(c.x, c.y, c.r)
```

```bash
python3 test.py
```


## 07:複数のモジュールを一括で管理

### パッケージ

  - パッケージとは、複数のモジュールがまとめられたディレクトリのこと
  - パッケージにまとめられたモジュールは、次のようにインポートできる

./mypackage/my_module1の中身:

```python

def hello1():
    print("Hello 1")

```

./mypackage/my_module2の中身:

```python

def hello2():
    print("Hello 2")

```

py ファイル:
```python
# /home/ubuntu/test.py

from my_package import my_module1, my_module2

my_module1.hello1()
my_module2.hello2()
```

  - カンマ区切りで複数のモジュールをインポートできる
  - ただし、import a, b のようにインポートすることは推奨されていない

実行コード:

```bash
python3 test.py
```


  - パッケージのなかのモジュールに含まれる関数を指定するには次のように書く
```python
# /home/ubuntu/test.py

from my_package.my_module1 import hello1
from my_package.my_module2 import hello2

hello1()
hello2()
```

- ピリオドで区切って、モジュールまでのパスを入力する
- パッケージをそのままインポートしようとした場合エラーになる

py ファイル:
```python
# /home/ubuntu/test.py

import my_package

my_package.my_module1.hello1()
```

- my_module1 が my_package の属性ではないため、エラーが発生する



実行コード:
```bash
python3 test.py
```

## 08:モジュールの名前を確認 (__name__)

### 変数 __name__

- 変数 __name__ はあらかじめ用意されている変数
- 変数 __name__ には、モジュールの名前が代入される

py ファイル 1:
```python
# /home/ubuntu/testmod.py
def get_mod_name():
    return __name__
```


py ファイル 2:
```python
# /home/ubuntu/test.py

import testmod

print(testmod.get_mod_name())
```

実行コード:
```bash
python3 test.py
```

  - また、そのモジュールが直接実行されている場合、変数 `__name__` には、文字列 `__main__` が代入される

py ファイル:
```python
# /home/ubuntu/test.py

print(__name__)
```

実行コード:
```bash
python3 test.py
```

### `__mro__` を使ったときに出力された `__main__` について

クラスの継承関係を確認するコード:
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def add_age(self, year):
        self.age += year

class Programmer(Person):
    def __init__(self, name, age, language):
        super().__init__(name, age)
        self.language = language
        self.languages = {language}

class StudentProgrammer(Programmer):
    pass

print(StudentProgrammer.__mro__)
```

- `クラス名.__mro__` が示す値のなかには、`__main__.StudentProgrammer` のように、`__main__` に続けてクラス名が書かれるクラスがあった
- `__main__` は直接実行されているモジュールに付けられる特別な名前
- つまり、`__main__.クラス名` は、クラス名 クラスが、直接実行されているモジュールの属性であることを示している



## !!!!! 09:モジュールの処理を制御 (if __name__ == "__main__")

  - モジュールをインポートすると、モジュールのコードが実行される
  - モジュールをインポートすると、そのモジュールに書かれている処理が実行される

py ファイル:
```python
# /home/ubuntu/test.py
import testmod
```

- 実行すると、「testmod が実行されました。」と出力される
- testmod.py の 5 行目の処理によって出力された

testmod.pyの中身:
```python

def func():
    print("func 関数が呼び出されました。")


print("testmod が実行されました。")


```

### !!! if __name__ == "__main__"

インポート時に実行されると困る処理は、条件式が `__name__ == "__main__"` の if 文のなかにいれる

py ファイル:
```python
# /home/ubuntu/testmod.py

def func():
    print("func 関数が呼び出されました。")

if __name__ == "__main__":
    print("testmod が実行されました。")
```
                  
  -  変数 __name__ の値は、モジュールの名前
  - `__name__ == "__main__"` が満たされるときは、そのモジュールが直接実行されているとき
  - つまり、`このモジュールはインポートされても、print("testmod が実行されました。") は実行されない`


実行コード:
```bash
python3 test.py
```

## 10:モジュールの利点

  - 異なるモジュールどうしで同じ変数名を使える
  - コードの再利用ができる


## 11:標準ライブラリ

### 標準ライブラリ
- 標準ライブラリは、あらかじめ用意されているモジュール群
- どこに配置されたモジュールからでもインポートすることができる
- 標準ライブラリには、
  - random モジュール
  - math モジュール
  - sys モジュール etc.


### リンク
- randomモジュール
  - https://docs.python.org/ja/3/library/random.html
- mathモジュール
  - https://docs.python.org/ja/3/library/math.html
- sysモジュール
  - https://docs.python.org/ja/3/library/sys.html


## 12:random モジュール

### random モジュール

- random モジュールは、疑似乱数に関するモジュール
- たとえば、次のコードで指定した範囲からランダムで整数を得ることができる

```python
import random

n = random.randint(1, 5)
print(n)
```

  - random モジュールの randint 関数を使うと、第 1 引数以上、第 2 引数以下の整数を得ることができる
  - つまり、上記コードでは、変数 n に 1 から 5 までの整数のなかからランダムに選ばれた整数が代入される


## 13:math モジュール

  - math モジュールは、数学におけるさまざまな演算に関するモジュール
  - たとえば、次のコードで指定した数値の平方根を得ることができる

```python
import math

x = math.sqrt(2)
print(x)
```

  - math モジュールの sqrt 関数を使うと、引数の数値の平方根を得ることができる



## 14:sys モジュール

- sys モジュールは、実行システムに関するモジュール
- たとえば、次のコードで実行を強制終了することができる

```python
import sys

sys.exit()
print("paiza")

```

- sys モジュールの exit 関数を使うと、コードの実行を強制終了することができる


<br>

---

<br>

# Lesson 24: 例外処理を理解しよう


## 01:例外・例外処理とはなにか

### 例外とはなにか

- コードを実行すると、エラーが発生し、実行が終了する場合がある。このようなとき「例外が発生した」「例外が送出された」という。

```python
a = float("abc")
```

> [!CAUTION]
> 上記コードを実行すると、`ValueError` という例外が発生する<br>
> 今回は、文字列 abc を浮動小数点数に変換できなかったために発生した

### 例外処理とはなにか
  - 例外処理とは、コード実行時に発生する例外に対しておこなう処理のこと
  - 例外処理を用意すると、例外によって実行が途中で終了しないようにすることができる



## 02:try 文の書き方 (try - except)

try 文の書き方:
```python
try:
    例外が発生しうる処理
except 予期される例外名:
    例外が発生したときにおこなう処理
```



## 03:はじめての try 文

### try 文の書き順

- try と書く

```python 
try
```

- コロンを書いて改行する
```python
try:
```

- インデントに気を付けて、例外が発生しうる処理を書く
```python
try:
    a = float(input())
```

- 改行して、except と書く
```python
try:
    a = float(input())
except
```

- 半角スペースを空けて、この except 節で受ける例外の名前を書く
```python
try:
    a = float(input())
except ValueError
```

- コロンを書いて改行する
```python
try:
    a = float(input())
except:
```

- ValueError が発生したときの処理を書く
```python
try:
    a = float(input())
except ValueError:
    print("入力値は数字でなければなりません。")
```


## 04:複数の例外を受ける except 節

- 1 つの except 節で、複数の例外を受けるようにすることができる

- コードでは、except 節の例外名を書くところに例外名のタプルを書く

```python
try:
    a = float(input())
    b = float(input())
    print(a / b)
except (ValueError, ZeroDivisionError):
    print("入力値が正しくありません。")
```

- このコードの except 節では、ValueError と ZeroDivisionError を受けることができる
- ただし、このタプルについては、かっこを省略することはできない


## 05:複数の except 節


### except 節は複数用意することができる

  - except 節を複数用意した場合、発生した例外にマッチする except 節が上から順番に探索され、最初にマッチした except 節に処理が移る

  - コードでは、普段 except 節を書くときと同じように書く

```python
try:
    a = float(input())
    b = float(input())
    print(a / b)
except ValueError:
    print("入力値は数字でなければなりません。")
except ZeroDivisionError:
    print("0 で割ることはできません。")
```

## 06:例外クラスの継承関係と except 節

### 動画内で使う try 文のコード

```python
try:
    a = float(input())
    b = float(input())
    print(a / b)
except ValueError:
    print("入力値は数字でなければなりません。")
except ZeroDivisionError:
    print("0 で割ることはできません。")
```


### except 節で受ける例外

- except 節で受ける例外には、その例外クラスの子孫にあたるクラスのものも含まれる
- そのため、except 節で受ける例外のクラスを Exception にすると、ほとんどすべての例外を受けることができる

```python
try:
    a = float(input())
    b = float(input())
    print(a / b)
except Exception:
    print("例外が発生しました。")
```


### BaseException クラスと Exception クラスの違い

- Python の BaseException クラスと Exception クラスはそれぞれ次のようなクラス
  - BaseException: すべての例外クラスに継承されるクラス
  - Exception: BaseException クラスのサブクラスで、ほとんどすべての例外クラスに継承されるクラス
- そして、それぞれのクラスは次のような意図で定義されている
  - BaseException: すべての例外クラスの基底クラス
  - Exception: システムの終了以外の例外クラス
      - たとえば...
      - SystemExit というクラスは Exception クラスを継承せずに、BaseException クラスを直接継承している
      - SystemExit クラスは Python の実行を終了させるときに用いられる
      - なぜ、Exception クラスを継承せずに、BaseException クラスを直接継承しているかというと、このクラスの例外が except Exception: といった except 節に誤って捕捉されないようにするため
      - 誤って捕捉されると、エラー出力がされないことがある



## 07:例外クラスのインスタンスを生成

### 例外クラスのインスタンスを生成することができる
```python
e = ValueError("test1", "test2")
print(e.args)
```

- 例外クラスのインスタンスのメンバ変数 args には、コンストラクタに渡した引数の分だけ要素をもつタプルが代入される



## 08:例外を意図的に発生させる (raise)

- PHPでいうところのthrow、GoLangでいうところのpanic


### raise 文

- raise 文を使うと、意図的に例外を発生させることができる

raise 文の書き方 1:
```python
raise 例外クラスのインスタンス
```

例:
```python
raise ValueError("0 ≦ x ≦ 10 の整数を指定してください。")
```

- 例外クラスに渡した引数の値（= 例外クラスのインスタンスのメンバ変数 args の値）は、エラーメッセージに使われる
```python
raise 文の書き方 2:
raise 例外クラス名
```

例:
```python
raise ValueError
```

- この場合、メンバ変数 args の値を設定できないため、「なぜエラーが発生したか」を詳細に伝えることができない


## 09:独自の例外クラスを定義

Exception クラスを継承してクラスを定義すると、独自の例外クラスを定義することができる:
```python
class InputValueError(Exception):
    pass

raise InputValueError("入力値は整数値でなければなりません。")
```


### ※　【初心者向け】エラーを握りつぶすことの問題と対処法

  - https://tech.anycloud.co.jp/articles/js-error-handling/   


#### なぜ例外を握りつぶしてはいけないのか
  - 問題の隠蔽: ユーザーや開発者にエラーが発生したことが伝わらないため、システムは異常な状態のまま動作し続けてしまいます。
  - デバッグの困難化: エラーの原因や場所を特定する手がかりが失われるため、バグの修正が難しくなります。
  - 異常処理の連鎖: 正常に処理が続行されることで、予期せぬ後続処理が実行され、別の問題を引き起こす可能性があります。 

#### 例外を握りつぶさないための対処法
  - 最低限の記録: 例外をキャッチした場合は、ログにエラー情報を記録します。
  - 例外の再スロー: 処理を続行できない場合は、例外を再スローして上位の処理にエラーを通知します。
  - 明確なコメント: 例外を無視する特殊なケースでは、なぜ無視する必要があるのかをコメントで明確に記録します。
  - ユーザーへの通知: エラー発生時には、ユーザーに分かりやすいメッセージを表示したり、システム管理者に通知したりします。
  - 例外処理の共通化: 共通の例外処理を行う仕組みを、上位層に設けることで、個々の開発者による不適切な処理を防ぎます。 

<br>

---

<br>



# Lesson 25: !!!!! イミュータブルとミュータブルを学習しよう

## 「オブジェクト」は抽象的で、幅広く使われる

- 例:
  - 整数の 1
  - 文字列の "paiza"
  - 関数の print
  - モジュールの random


- 「オブジェクト」は「型」をもち、「型」に応じた値をもつ
- オブジェクトの識別には id 関数によって得られる識別値が用いられる


## 02:オブジェクトのid


###  id 関数

- id 関数を使うと、オブジェクトの id を得ることができる

```python
def show_abc_id(a, b, c):
    print(f"a: {id(a)}")
    print(f"b: {id(b)}")
    print(f"c: {id(c)}")

a, b, c = 1, [0, 3, 6], (1, "apple")
show_abc_id(a, b, c)
```


### 累算代入をしたときのオブジェクトの id

- 2 種類がある
    - id を変えずに値を変えることができないオブジェクト
    - id を変えずに値を変えることができるオブジェクト 

```python
def show_abc_id(a, b, c):
    print(f"a: {id(a)}")
    print(f"b: {id(b)}")
    print(f"c: {id(c)}")

"""
a: 187874005136352
b: 95410720533376
c: 95410720987008
"""

a, b, c = 1, [0, 3, 6], (1, "apple")
show_abc_id(a, b, c)

print("=" * 3)

a += 1
b += [9, 12]
c += ("cherry", "donut")

show_abc_id(a, b, c)

"""
a: 187874005136384
b: 95410720533376
c: 95410721116048
"""

```

  - 変数 a, c が示すオブジェクトの id が変わった
  - 変数 b が示すオブジェクトの id は変わらなかった


## 03:イミュータブルなオブジェクトとはなにか

- id を変えずに値を変えることができないオブジェクトを「`イミュータブルなオブジェクト`」と言う
- つまり、イミュータブルなオブジェクトは、`その値が常に同じであるオブジェクト`

- たとえば、次のコードでは変数 a の示すオブジェクトの id が再代入前後で変わる

```python
def show_id(name, value):
    print(f"{name}: {id(value)}")

a = 1
show_id("更新前の a", a)

a += 1
show_id("更新後の a", a)
```

  - `a += 1` で、変数 a の示すオブジェクトの値を変更しようとする
  - すると、再代入前後で変数 a の示すオブジェクトの id が変わる
  - オブジェクトは、その id によって識別されるため、再代入前後で変数 a の示すオブジェクトが変わったことがわかる


## 04:ミュータブルなオブジェクトとはなにか

  - id を変えずに値を変えることができるオブジェクトを「ミュータブルなオブジェクト」と言う
  - つまり、ミュータブルなオブジェクトは、`その値が変動しうるオブジェクト`

  - たとえば、次のコードでは変数 a の示すオブジェクトの id が再代入前後で変わらない

```python
def show_id(name, value):
    print(f"{name}: {id(value)}")

a = [1, 2, 3]
show_id("更新前の a", a)

a += [4, 5, 6]
show_id("更新後の a", a)
```

- `a += [4, 5, 6]` で、変数 a の示すオブジェクトの値を変更しようとする
- 再代入前後で変数 a の示すオブジェクトの id が変わらなかったことがわかる
- オブジェクトは、その id によって識別されるため、再代入前後で変数 a の示すオブジェクトが変わらなかったと言える

- ミュータブルなオブジェクトは、同じ値をもつオブジェクトどうしでも、id が異なることがある
```python
def show_id(name, value):
    print(f"{name}: {id(value)}")

b, c = [1, 2, 3], [1, 2, 3]
show_id("リスト 1", b)
show_id("リスト 2", c)
```


## 05:idと変数と代入

- id を用いると、変数と代入を次のように考えることができる
- 代入: 変数にオブジェクトの id を教えること
- 変数: 代入時に教わった id を覚えているもの

```python
def show_id(name, value):
    print(f"{name}: {id(value)}")

a = [1, 2, 3]
b = a
show_id("最初に生成した a", a)
show_id("a が代入された b", b)
```

- ミュータブルなオブジェクトは、同じ値のオブジェクトどうしで id が異なることがある
- しかし、今回変数 b に代入されたオブジェクトの id は変数 a が示すものと同じであることがわかる
- このことから、変数への代入は、オブジェクトの id を変数に教えること、と考えることができる
- つまり、代入とは変数にオブジェクトを入れることではなく、どのオブジェクトを示すようにするかを変数に指定することと言える



## 06:イミュータブルなオブジェクトが代入された変数

- 次のコードを実行すると、1 が出力される

```python
a = 1
b = a

a += 1
print(b)
```

- 1 が出力されるのは、変数 a と b に代入されたオブジェクトがイミュータブルなオブジェクトだから
- b = a で変数 b は、この時点で変数 a が示すオブジェクトを教わる
- a += 1 で変数 a の示すオブジェクトは、値が 2 である別のオブジェクトに変更されるが、変数 b の示すオブジェクトが変更されるわけではない
- 変数 b は、変数 a を見ているわけではなく、自身に代入されたオブジェクトを見ている

- これらのことは、id を使って確認できる
```python
def show_id(name, value):
    print(f"{name}: {id(value)}")

a = 1
b = a
show_id("更新前の a", a)
show_id("b", b)

a += 1
show_id("更新後の a", a)
show_id("b", b)
print(b)


"""
更新前の a: 196623995679712
b: 196623995679712
更新後の a: 196623995679744
b: 196623995679712
1
"""


```


## 07:ミュータブルなオブジェクトが代入された変数


  - 再代入は累算代入を除いて、オブジェクトの値を変更するわけではなく、変数が示すオブジェクトを変更する行為なので、他の変数が示す値は変わらない

```python
def show_id(name, value):
    print(f"{name}: {id(value)}")

a = [1, 2, 3]
b = a
c = [1, 2, 3]
show_id("更新前の a", a)
show_id("b", b)
show_id("c", c)

a = a + [4]

show_id("更新後の a", a)
show_id("b", b)
show_id("c", c)

print(b)
print(c)

"""
更新前の a: 83004697209728
b: 83004697209728
c: 83004697670144
更新後の a: 83004697672768
b: 83004697209728
c: 83004697670144
[1, 2, 3]
[1, 2, 3]
"""


```

  - 累算代入の際は変数に代入されているオブジェクトの id を可能な限り変えずに値を変更するように演算がおこなわれる

```python
def show_id(name, value):
    print(f"{name}: {id(value)}")

a = [1, 2, 3]
b = a
c = [1, 2, 3]
show_id("更新前の a", a)
show_id("b", b)
show_id("c", c)

a += [4]

show_id("更新後の a", a)
show_id("b", b)
show_id("c", c)

print(b)
print(c)

"""
更新前の a: 100991766162304
b: 100991766162304
c: 100991766622720
更新後の a: 100991766162304
b: 100991766162304
c: 100991766622720
[1, 2, 3, 4]
"""

```


### ※　Python のミュータブルとイミュータブル：違いと意味解説

- https://beginner-engineers.com/mutable-immutable/
- https://qiita.com/Tadataka_Takahashi/items/53433acd7fcc9b2e044c



#### 1.1 不変オブジェクト（Immutable Objects）

不変オブジェクトは、一度作成されると、その内容を変更することができません。

主な不変オブジェクト：
- 整数（int）
- 浮動小数点数（float）
- 文字列（str）
- タプル（tuple）
- frozenset

例：
```python
x = 5
y = x
x += 1
print(x, y)  # 出力: 6 5
```

#### 1.2 可変オブジェクト（Mutable Objects）

可変オブジェクトは、作成後にその内容を変更することができます。

主な可変オブジェクト：
- リスト（list）
- 辞書（dict）
- セット（set）

例：
```python
x = [1, 2, 3]
y = x
x.append(4)
print(x, y)  # 出力: [1, 2, 3, 4] [1, 2, 3, 4]
```

#### 2. 不変オブジェクトのメリットとデメリット

#### 2.1 メリット

1. **スレッドセーフ**: 複数のスレッドから同時にアクセスされても、値が変更されることがないため安全です。

2. **キャッシュの最適化**: 同じ値を持つオブジェクトは同一のメモリ位置を参照できるため、メモリ使用量を節約できます。

3. **ハッシュ可能**: 辞書のキーやセットの要素として使用できます。

4. **予測可能性**: オブジェクトの状態が変わらないため、コードの動作が予測しやすくなります。

#### 2.2 デメリット

1. **新しいオブジェクトの作成**: 値を「変更」する際に、新しいオブジェクトを作成する必要があるため、メモリ使用量が増加する可能性があります。

2. **大量のデータ操作時の非効率性**: 大きなデータ構造を扱う際に、頻繁に新しいオブジェクトを作成する必要があるため、パフォーマンスが低下する可能性があります。

#### 3. 可変オブジェクトのメリットとデメリット

#### 3.1 メリット

1. **効率的なメモリ使用**: オブジェクトの内容を直接変更できるため、新しいオブジェクトを作成する必要がありません。

2. **大量のデータ操作に適している**: データの追加や削除が頻繁に行われる場合、効率的に処理できます。

3. **柔軟性**: オブジェクトの状態を簡単に変更できるため、動的なデータ構造の実装に適しています。

#### 3.2 デメリット

1. **スレッドセーフではない**: 複数のスレッドから同時にアクセスされると、予期せぬ結果を招く可能性があります。

2. **副作用**: 関数内でオブジェクトを変更すると、呼び出し元の環境にも影響を与える可能性があります。

3. **デバッグの難しさ**: オブジェクトの状態が予期せず変更される可能性があるため、バグの追跡が難しくなる場合があります。

#### 4. 適切な使用シーン

#### 4.1 不変オブジェクトの適切な使用シーン

1. **定数や設定値**: 変更されるべきでない値を表現する際に適しています。

    ```python
    MAX_CONNECTIONS = 100
    DATABASE_URL = "postgresql://user:pass@localhost/dbname"
    ```

2. **関数の引数**: 関数内で引数の値が変更されないことを保証したい場合に適しています。

    ```python
    def process_data(data: tuple) -> list:
        return list(data)
    ```

3. **マルチスレッド環境**: 複数のスレッドで共有されるデータを安全に扱いたい場合に適しています。

    ```python
    import threading

    shared_data = (1, 2, 3, 4, 5)

    def worker(data):
        # dataは不変なので、安全に読み取ることができる
        print(sum(data))

    threads = [threading.Thread(target=worker, args=(shared_data,)) for _ in range(5)]
    for thread in threads:
        thread.start()
    ```

4. **キャッシュのキー**: 辞書のキーやセットの要素として使用する場合に適しています。

    ```python
    cache = {}
    def expensive_operation(x, y):
        key = (x, y)  # タプルをキーとして使用
        if key not in cache:
            cache[key] = x ** y
        return cache[key]
    ```

#### 4.2 可変オブジェクトの適切な使用シーン

1. **データの収集と加工**: リストや辞書を使用してデータを収集し、加工する場合に適しています。

    ```python
    def process_logs(log_files):
        results = []
        for file in log_files:
            with open(file, 'r') as f:
                results.extend(process_log_line(line) for line in f)
        return results
    ```

2. **キャッシュやメモ化**: 計算結果を保存し再利用する場合に適しています。

    ```python
    def fibonacci(n, cache={}):
        if n in cache:
            return cache[n]
        if n <= 1:
            return n
        result = fibonacci(n-1) + fibonacci(n-2)
        cache[n] = result
        return result
    ```

3. **オブジェクト指向プログラミング**: クラスのインスタンス変数として使用する場合に適しています。

    ```python
    class ShoppingCart:
        def __init__(self):
            self.items = []

        def add_item(self, item):
            self.items.append(item)

        def remove_item(self, item):
            self.items.remove(item)

        def get_total(self):
            return sum(item.price for item in self.items)
    ```

4. **パフォーマンスが重要な場合**: 大量のデータを頻繁に更新する必要がある場合に適しています。

    ```python
    def update_large_dataset(data, updates):
        for key, value in updates.items():
            data[key] = value
        return data
    ```

#### 5. ベストプラクティス

1. **デフォルト引数に注意**: 可変オブジェクトをデフォルト引数として使用する際は注意が必要です。

    ```python
    # 悪い例
    def add_item(item, items=[]):
        items.append(item)
        return items

    # 良い例
    def add_item(item, items=None):
        if items is None:
            items = []
        items.append(item)
        return items
    ```

2. **不変性の活用**: 可能な限り不変オブジェクトを使用し、必要な場合のみ可変オブジェクトを使用しましょう。

3. **コピーの使用**: 可変オブジェクトを変更する際は、元のオブジェクトを保護するためにコピーを作成することを検討しましょう。

    ```python
    import copy

    original = [1, [2, 3], 4]
    shallow_copy = original.copy()
    deep_copy = copy.deepcopy(original)
    ```

4. **イミュータブルなデータクラスの活用**: Python 3.7以降では、`dataclasses`モジュールを使用してイミュータブルなデータクラスを簡単に作成できます。

    ```python
    from dataclasses import dataclass

    @dataclass(frozen=True)
    class Point:
        x: float
        y: float
    ```



## 08:関数の引数


### 関数の仮引数の渡され方

- 一般的に関数に引数が渡されるとき、その渡され方は次の 2 通りがある
  - 値渡し: オブジェクトがコピーされて渡されるような方法
  - 参照渡し: オブジェクトの id が渡されるような方法



- Python は参照渡し
```python
def show_id(name, value):
    print(f"{name}: {id(value)}")

a = [1, 2, 3]
print(f"関数の外: {id(a)}")
show_id("関数の中", a)

"""
関数の外: 79070197312384
関数の中: 79070197312384
"""



```

- 関数の内側と外側、どちらで id 関数を使っても得られる id が同じ


### 関数内の処理が与える影響

関数内の処理は、関数の外のミュータブルなオブジェクトに影響を与えることがある

```python
def show_id(name, value):
    print(f"{name}: {id(value)}")


def twice(li):
    for i in range(len(li)):
        li[i] *= 2

a = [1, 2, 3]
print(f"関数処理の前: {a}")
twice(a)
print(f"関数処理の後: {a}")

"""
814
813
"""


```



<br>

---

<br>



【EOF】



[←　README](../README.md)


