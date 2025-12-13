<!-- omit in toc -->
# 新・Java入門編 Lesson13 ～ Lesson20

<!-- omit in toc -->
# [目次]
- [新・Java入門編13: for文を学習しよう](#新java入門編13-for文を学習しよう)
  - [01: for文の使い方](#01-for文の使い方)
  - [02: for文を使ってアレイリストの中身を出力](#02-for文を使ってアレイリストの中身を出力)
  - [03: for文とforEachメソッドと拡張for文](#03-for文とforeachメソッドと拡張for文)
  - [04: for文とif文の組み合わせ](#04-for文とif文の組み合わせ)
- [新・Java入門編14: 標準入力と標準出力を学習しよう](#新java入門編14-標準入力と標準出力を学習しよう)
  - [01: 標準出力](#01-標準出力)
    - [標準出力](#標準出力)
  - [02: 標準入力](#02-標準入力)
- [新・Java入門編15: Scannerを使用した標準入力からの値の取得方法について学習しよう](#新java入門編15-scannerを使用した標準入力からの値の取得方法について学習しよう)
  - [01: nextLineを使った標準入力からの値の取得](#01-nextlineを使った標準入力からの値の取得)
    - [Scanner](#scanner)
    - [System.in](#systemin)
    - [空白文字](#空白文字)
    - [System.out](#systemout)
  - [02: nextを使った標準入力からの値の取得](#02-nextを使った標準入力からの値の取得)
  - [03: nextIntを使った標準入力からの値取得](#03-nextintを使った標準入力からの値取得)
  - [文字列連結演算子](#文字列連結演算子)
- [新・Java入門編16: 複数のデータを標準入力から取得しよう](#新java入門編16-複数のデータを標準入力から取得しよう)
  - [01: 入力されるデータの数があらかじめ決まっている場合の取得方法](#01-入力されるデータの数があらかじめ決まっている場合の取得方法)
  - [02: 入力されるデータの数があらかじめ決まっていない場合の取得方法](#02-入力されるデータの数があらかじめ決まっていない場合の取得方法)
- [新・Java入門編17: while文を学習しよう](#新java入門編17-while文を学習しよう)
  - [01: while文の使い方](#01-while文の使い方)
- [新・Java入門編18: コレクションフレームワークを理解しよう（LinkedHashSet）](#新java入門編18-コレクションフレームワークを理解しようlinkedhashset)
  - [01: コレクションフレームワークとは](#01-コレクションフレームワークとは)
    - [Listとは](#listとは)
    - [Setとは](#setとは)
    - [Mapとは](#mapとは)
  - [02: LinkedHashSet型の変数の宣言及び初期化方法](#02-linkedhashset型の変数の宣言及び初期化方法)
    - [LinkedHashSetとは](#linkedhashsetとは)
  - [03: 要素の追加（add）](#03-要素の追加add)
  - [04: 要素数の取得（size）](#04-要素数の取得size)
  - [05: 要素の有無を確認（contains）](#05-要素の有無を確認contains)
  - [06: 指定した要素の削除（remove）](#06-指定した要素の削除remove)
  - [07: 全要素の削除（clear）](#07-全要素の削除clear)
  - [08: 空かどうか（isEmpty）](#08-空かどうかisempty)
  - [09: 反復処理（forEachメソッド、拡張for文）](#09-反復処理foreachメソッド拡張for文)
- [新・Java入門編19: コレクションフレームワークを理解しよう（LinkedHashMap）](#新java入門編19-コレクションフレームワークを理解しようlinkedhashmap)
  - [01: LinkedHashMap型の変数の宣言及び初期化方法](#01-linkedhashmap型の変数の宣言及び初期化方法)
  - [02: ペアの追加（put）](#02-ペアの追加put)
  - [03: ペアの取得（get）](#03-ペアの取得get)
  - [04: ペア数の取得（size）](#04-ペア数の取得size)
  - [05: ペアの有無を確認(containsKey)](#05-ペアの有無を確認containskey)
  - [06: 指定したペアの削除（remove）](#06-指定したペアの削除remove)
  - [07: 全てのペアの削除（clear）](#07-全てのペアの削除clear)
  - [08: 空かどうか（isEmpty）](#08-空かどうかisempty-1)
  - [09: 反復処理（forEachメソッド、keySetメソッド）](#09-反復処理foreachメソッドkeysetメソッド)
- [新・Java入門編20: 複雑な制御構文について学習しよう](#新java入門編20-複雑な制御構文について学習しよう)
  - [01: 二重ループ](#01-二重ループ)
  - [02: continue文](#02-continue文)
  - [03: break文](#03-break文)
  - [04: switch](#04-switch)




<br>

---

<br>



# 新・Java入門編13: for文を学習しよう


## 01: for文の使い方

```java

public class Main {
    public static void main(String... args) {
        /* BEFORE
            System.out.println(0);
            System.out.println(1);
            System.out.println(2);
            System.out.println(3);
            System.out.println(4);
            System.out.println(5);
        */    

        // AFTER
        for(Integer i = 0; i < 6; i++) {
            System.out.println(i);
        }
    }
}

```

## 02: for文を使ってアレイリストの中身を出力

```java

import java.util.*;

public class Main {
    public static void main(String... args) {
        ArrayList<String> fruits = new ArrayList<>();
        fruits.add("apple");
        fruits.add("orange");
        fruits.add("lemon");
        fruits.add("banana");
        fruits.add("grape");

        /* BEFORE
        System.out.println(fruits.get(0));
        System.out.println(fruits.get(1));
        System.out.println(fruits.get(2));
        System.out.println(fruits.get(3));
        System.out.println(fruits.get(4));
        */

       //AFTER
       for(Integer i=0; i < fruits.size(); i++){
            System.out.println(fruits.get(i));
       }
    }
}

```



## 03: for文とforEachメソッドと拡張for文


```java

import java.util.*;
public class Main {
    public static void main(String... args) {
        ArrayList<String> fruits = new ArrayList<>();
        fruits.add("apple");
        fruits.add("orange");
        fruits.add("lemon");
        fruits.add("banana");
        fruits.add("grape");

        //for
        for(Integer i=0; i< fruits.size(); i++){
            System.out.println(fruits.get(i));
        }
        
        //forEach
        fruits.forEach(fruit -> {
            System.out.println(fruit);
        });
        
        
    }
}

```

## 04: for文とif文の組み合わせ


```java

public class Main {
    public static void main(String... args) {
        for (int i = 1; i <= 7; i++) {
            System.out.println(i + "日目");
            if (i==6 || i==7){
                System.out.println("今日はお休み");    
            }
        }
    }
} 

```


<br>

---

<br>



#  新・Java入門編14: 標準入力と標準出力を学習しよう


## 01: 標準出力

### 標準出力

-  プロセスに与えられる特別なストリーム
-  外部への出力を抽象化したようなものであり、標準出力へ書き込まれたデータは「他のプログラムの入力として利用する」「ファイルに書き込む」などの柔軟な取り扱いがなされる
-  paiza.IO 環境では、標準出力に書き込まれたデータはコード欄の下の出力欄に文字列として表示される

## 02: 標準入力

![](./images/lesson1401.png)


![](./images/lesson1402.png)


![](./images/lesson1403.png)


![](./images/lesson1404.png)



<br>

---

<br>



# 新・Java入門編15: Scannerを使用した標準入力からの値の取得方法について学習しよう


## 01: nextLineを使った標準入力からの値の取得

###  Scanner

  - https://docs.oracle.com/javase/jp/17/docs/api/java.base/java/util/Scanner.html



![](./images/lesson1501.png);



```java
import java.util.*;

public class Main {
    public static void main(String... args) {
        Scanner sc = new Scanner(System.in);
        String s1 = sc.nextLine();   //1行目
        System.out.println(s1);
        String s2 = sc.nextLine();   //2行目
        System.out.println(s2);      
    }
}

//このロジックでは標準入力が3行以上入るとエラーとなる

```

###  System.in

  - https://docs.oracle.com/javase/jp/17/docs/api/java.base/java/lang/System.html#in

### 空白文字

  - Character.isWhitespace
    - https://docs.oracle.com/javase/jp/17/docs/api/java.base/java/lang/Character.html#isWhitespace(int)


   - Unicodeの空白文字(SPACE_SEPARATOR、LINE_SEPARATOR、またはPARAGRAPH_SEPARATOR)であるが、<br>改行なしの空白('\u00A0'、'\u2007'、'\u202F')ではない。
   - '\t' (U+0009水平タブ)である。
   - '\n' (U+000A改行)である。
   - '\u000B' (U+000B垂直タブ)である。
   - '\f' (U+000Cフォーム・フィード)である。
   - '\r' (U+000D復帰)である。
   - '\u001C' (U+001Cファイル区切り文字)である。
   - '\u001D' (U+001Dグループ区切り文字)である。
   - '\u001E' (U+001Eレコード区切り文字)である。
   - '\u001F' (U+001F単位区切り文字)である。


### System.out

   -  https://docs.oracle.com/javase/jp/17/docs/api/java.base/java/lang/System.html#out


## 02: nextを使った標準入力からの値の取得

(参考) 
   - Scannerクラス next,nextLine,nextIntメソッドの使い分け
   - https://qiita.com/kitamuwork/items/e383411e5191b85d14b9
     - nextLine
       - ⇛改行をスキャンする
       - ⇛改行のみでも改行（\n）としてスキャンしている
     - next
       - ⇛改行をスキャンしない
       - ⇛文字をスキャンするまで改行は無視される
     - nextInt
       - ⇛改行をスキャンしない
       - ⇛数字をスキャンするまで改行は無視される

## 03: nextIntを使った標準入力からの値取得

## 文字列連結演算子
   - https://paiza.jp/works/java/new-primer/java-new-primer-5/80401




<br>

---

<br>


# 新・Java入門編16: 複数のデータを標準入力から取得しよう



## 01: 入力されるデータの数があらかじめ決まっている場合の取得方法


```java

import java.util.*;

public class Main {
    public static void main(String... args) {
        Scanner sc = new Scanner(System.in);
        ArrayList<String> inputList = new ArrayList<>();
        inputList.add(sc.next());
        inputList.add(sc.next());
        inputList.add(sc.next());
        System.out.println(inputList);
    }
}

```


## 02: 入力されるデータの数があらかじめ決まっていない場合の取得方法


このコードのユースケース：最初に数字を入れて、そのあとの行ごとに文字列を拾う

```java

import java.util.*;

public class Main {
    public static void main(String... args) {

        Scanner sc = new Scanner(System.in);

        ArrayList<String> inputData = new ArrayList<>();

        Integer n = sc.nextInt();

        for(Integer i=0; i < n; i++){
            inputData.add(sc.next());
        }
        System.out.println(inputData);
    }
}



```



<br>

---

<br>

# 新・Java入門編17: while文を学習しよう



## 01: while文の使い方

```java

public class Main {
    public static void main(String... args) {
    
        Integer i = 1;
        while(i < 8){
            System.out.println(i);
            i++;            
        }
        
        System.out.println("paiza");
    }
}

```


<br>

---

<br>


# 新・Java入門編18: コレクションフレームワークを理解しよう（LinkedHashSet）


## 01: コレクションフレームワークとは

- List
- Set
- Map

### Listとは

- 順序付けられた要素の集まり
- 指定した位置の要素を取り出せる
- 要素の重複を許容する

-   例)
    - ArrayList
    - LinkedList etc.


### Setとは

- 重複した要素のない集まり

  - 例)
    - HashSet
    - LinkedHashSet
    - TreeSet etc.


### Mapとは

- キーと値のペアを要素とした集まり
- 値は、キーを指定して読み書き可能

  - 例)
    - HashMap
    - LinkedHashMap
    - TreeMap etc.


## 02: LinkedHashSet型の変数の宣言及び初期化方法

### LinkedHashSetとは

- 要素として重複した値を保持しない集まりを表すクラス
- 要素が追加された順番を保持する
- ArrayList とは重複した値を保持しない点で異なる

```java
/*LinkedHashSetの呼び出し*/

import java.util.LinkedHashSet;

public class Main {
    public static void main(String... args) {
      LinkedHashSet<String> animals = new LinkedHashSet<>();
      System.out.print(animals);
    }
}
```


## 03: 要素の追加（add）

```java
import java.util.LinkedHashSet;

public class Main {
    public static void main(String... args) {
        LinkedHashSet<String> fruits = new LinkedHashSet<>();
        fruits.add("apple");
        fruits.add("lemon");
        fruits.add("apple");
        System.out.println(fruits);     // output: [apple, lemon]
    }
}

```

## 04: 要素数の取得（size）

```java
import java.util.LinkedHashSet;

public class Main {
    public static void main(String... args) {
        LinkedHashSet<String> fruits = new LinkedHashSet<>();

        fruits.add("apple");
        fruits.add("lemon");

        System.out.println(fruits);       //output : [apple, lemon]
        System.out.println(fruits.size);  //output : 2
    }
}

```

## 05: 要素の有無を確認（contains）

```java
import java.util.LinkedHashSet;

public class Main {
    public static void main(String... args) {
        LinkedHashSet<String> fruits = new LinkedHashSet<>();

        fruits.add("apple");
        fruits.add("lemon");
        System.out.println(fruits.contains("orange"));     //output: false
    }
}

```



## 06: 指定した要素の削除（remove）

```java
import java.util.LinkedHashSet;

public class Main {
    public static void main(String... args) {
        LinkedHashSet<String> fruits = new LinkedHashSet<>();

        fruits.add("apple");
        fruits.add("lemon");
        fruits.add("orange");
        
        System.out.println(fruits.contains("lemon"));     //output: true
        fruits.remove("lemon");
        System.out.println(fruits.contains("lemon"));     //output: false
    }
}


```

## 07: 全要素の削除（clear）

```java
import java.util.LinkedHashSet;

public class Main {
    public static void main(String... args) {
        LinkedHashSet<String> fruits = new LinkedHashSet<>();

        fruits.add("apple");
        fruits.add("lemon");
        fruits.add("orange");
        
        System.out.println(fruits.size());     //output: 3
        fruits.clear();
        System.out.println(fruits.size());     //output: 0
    }
}

```

## 08: 空かどうか（isEmpty）

```java
import java.util.LinkedHashSet;

public class Main {
    public static void main(String... args) {
        LinkedHashSet<String> fruits = new LinkedHashSet<>();

        fruits.add("apple");
        fruits.add("lemon");
        fruits.add("orange");
        
        System.out.println(fruits.isEmpty());   // output: false
        fruits.clear();
        System.out.println(fruits.isEmpty());   // output: true
    }
}

```

## 09: 反復処理（forEachメソッド、拡張for文）

```java
import java.util.LinkedHashSet;

public class Main {
    public static void main(String... args) {
        LinkedHashSet<String> fruits = new LinkedHashSet<>();

        fruits.add("apple");
        fruits.add("lemon");
        fruits.add("orange");
        
        fruits.forEach(fruit -> System.out.println(fruit));    // output: apple lemon orange

        for (String fruit: fruits){
            System.out.println(fruit);    // output: apple lemon orange
        }
    }
}

```

<br>

---

<br>

# 新・Java入門編19: コレクションフレームワークを理解しよう（LinkedHashMap）


## 01: LinkedHashMap型の変数の宣言及び初期化方法

```java
import java.util.LinkedHashMap;

public class Main {
    public static void main(String... args) {
        // 第1引数は【値】、第２引数は【キー】の型
        LinkedHashMap<String, Integer> users = new LinkedHashMap<>();
        System.out.println(users);
    }
}
```



## 02: ペアの追加（put）

```java
import java.util.LinkedHashMap;

public class Main {
    public static void main(String... args) {
        LinkedHashMap<String, Integer> scoreMap = new LinkedHashMap<>();
        scoreMap.put("国語",100);
        scoreMap.put("英語",90);
        scoreMap.put("数学",80);
        
        System.out.println(scoreMap);    // output: {国語=100, 英語=90, 数学=80}       
        scoreMap.put("英語",70);
        System.out.println(scoreMap);    // output: {国語=100, 英語=70, 数学=80}       
    }
}

```



## 03: ペアの取得（get）

```java
import java.util.LinkedHashMap;

public class Main {
    public static void main(String... args) {
        LinkedHashMap<String, Integer> scoreMap = new LinkedHashMap<>();

        scoreMap.put("国語", 100);
        scoreMap.put("英語", 90);
        scoreMap.put("数学", 80);
        
        System.out.println(scoreMap.get("英語"));         // output: 90
        System.out.println(scoreMap.get("理科"));         // output: null
    }
}

```


## 04: ペア数の取得（size）

```java
import java.util.LinkedHashMap;

public class Main {
    public static void main(String... args) {
        LinkedHashMap<String, Integer> scoreMap = new LinkedHashMap<>();

        scoreMap.put("国語", 100);
        scoreMap.put("英語", 90);
        scoreMap.put("数学", 80);
        
        System.out.println(scoreMap.size());     // output: 3
    }
}

```


## 05: ペアの有無を確認(containsKey)

```java
import java.util.LinkedHashMap;

public class Main {
    public static void main(String... args) {
        LinkedHashMap<String, Integer> scoreMap = new LinkedHashMap<>();

        scoreMap.put("国語", 100);
        scoreMap.put("英語", 90);
        scoreMap.put("数学", 80);
        
        System.out.println(scoreMap.containsKey("国語"));     // output: true
        System.out.println(scoreMap.containsKey("理科"));     // output: false
    }
}
```


## 06: 指定したペアの削除（remove）

```java
import java.util.LinkedHashMap;

public class Main {
    public static void main(String... args) {
        LinkedHashMap<String, Integer> scoreMap = new LinkedHashMap<>();

        scoreMap.put("国語", 100);
        scoreMap.put("英語", 90);
        scoreMap.put("数学", 80);
        
        scoreMap.remove("英語");
        System.out.println(scoreMap);     // output: {国語=100, 数学=80}
        
    }
}
```

## 07: 全てのペアの削除（clear）

```java
import java.util.LinkedHashMap;

public class Main {
    public static void main(String... args) {
        LinkedHashMap<String, Integer> scoreMap = new LinkedHashMap<>();

        scoreMap.put("国語", 100);
        scoreMap.put("英語", 90);
        scoreMap.put("数学", 80);
        
        System.out.println(scoreMap.size());    // output: 3
        scoreMap.clear();
        System.out.println(scoreMap.size());    // output: 0
    }
}
```


## 08: 空かどうか（isEmpty）

```java
import java.util.LinkedHashMap;

public class Main {
    public static void main(String... args) {
        LinkedHashMap<String, Integer> scoreMap = new LinkedHashMap<>();

        scoreMap.put("国語", 100);
        scoreMap.put("英語", 90);
        scoreMap.put("数学", 80);
    
        System.out.println(scoreMap.isEmpty());    // output: false
        scoreMap.clear();
        System.out.println(scoreMap.isEmpty());    // output: true
    }
}
```



## 09: 反復処理（forEachメソッド、keySetメソッド）

```java
import java.util.LinkedHashMap;

public class Main {
    public static void main(String... args) {
        LinkedHashMap<String, Integer> scoreMap = new LinkedHashMap<>();

        scoreMap.put("国語", 100);
        scoreMap.put("英語", 90);
        scoreMap.put("数学", 80);

        scoreMap.forEach((key, value) -> System.out.println(key + ":" + value));    // output: 国語:100 英語:90 数学:80
        for (String key: scoreMap.keySet()){
            Integer value = scoreMap.get(key);
            System.out.println(key + ":" + value);    // output: 国語:100 英語:90 数学:80
        }
    }
}

```


<br>

---

<br>


# 新・Java入門編20: 複雑な制御構文について学習しよう


## 01: 二重ループ

```java
public class Main{
    public static void main(String... args){
        
        for (Integer i=1; i < 10; i++){
            for (Integer j=1; j < 10; j++){
                System.out.print(i*j);
                System.out.print(" ");
            }
            System.out.println();
/*
output : 
    1 2 3 4 5 6 7 8 9 
    2 4 6 8 10 12 14 16 18 
    3 6 9 12 15 18 21 24 27 
    4 8 12 16 20 24 28 32 36 
    5 10 15 20 25 30 35 40 45 
    6 12 18 24 30 36 42 48 54 
    7 14 21 28 35 42 49 56 63 
    8 16 24 32 40 48 56 64 72 
    9 18 27 36 45 54 63 72 81 
*/
        }
    }
}
```



## 02: continue文
```java
public class Main{
    public static void main(String... args){
        for (Integer i = 0; i < 10; i++) {
            if (i % 2 == 1) {
                continue;                
            }
            System.out.println(i);    // output: 0 2 4 6 8
        }
    }
}
```


```java
public class Main{
    public static void main(String... args){
        for (Integer i = 1; i < 10; i++) {
            if(i == 5){
                continue;
            }
            for (Integer j = 1; j < 10; j++) {
                System.out.print(i*j);
                System.out.print(" ");
            }
            System.out.println();
        }

    }
}

/*
output:
    1 2 3 4 5 6 7 8 9 
    2 4 6 8 10 12 14 16 18 
    3 6 9 12 15 18 21 24 27 
    4 8 12 16 20 24 28 32 36 
    6 12 18 24 30 36 42 48 54 
    7 14 21 28 35 42 49 56 63 
    8 16 24 32 40 48 56 64 72 
    9 18 27 36 45 54 63 72 81 
*/
```


## 03: break文

```java
public class Main {
    public static void main(String... args) {
        for (int i = 1; i < 4; i++) {
            if(i==2){
                break;
            }
            System.out.println("外側" + i + "回目");
            for (int j = 1; j < 4; j++) {
                System.out.println("内側" + j + "回目");
            }
        }
    }
}
/*
output: 
    外側1回目
    内側1回目
    内側2回目
    内側3回目
*/

public class Main {
    public static void main(String... args) {
        for (int i = 1; i < 4; i++) {
            System.out.println("外側" + i + "回目");
            for (int j = 1; j < 4; j++) {
                if(j==2){
                    break;
                }
                System.out.println("内側" + j + "回目");
            }
        }
    }
}


/*
output: 
    外側1回目
    内側1回目
    外側2回目
    内側1回目
    外側3回目
    内側1回目
*/

```

## 04: switch

```java
public class Main {
    public static void main(String... args) {
        
        Integer month = 1;
        
        switch(month) {
            case 1:
                System.out.println("spring");
                break;
            case 2:
                System.out.println("spring");
                break;
            case 3:
                System.out.println("spring");
                break;
            case 4:
                System.out.println("summer");
                break;
            case 5:
                System.out.println("summer");
                break;
            case 6:
                System.out.println("summer");
                break;
            case 7:
                System.out.println("autumn");
                break;
            case 8:
                System.out.println("autumn");
                break;
            case 9:
                System.out.println("autumn");
                break;
            case 10:
                System.out.println("winter");
                break;
            case 11:
                System.out.println("winter");
                break;
            case 12:
                System.out.println("winter");
                break;
            default:
                System.out.println("?");
                break;
        }
    }
}


public class Main {
    public static void main(String... args) {
        
        Integer month = 1;
        
        switch(month) {
            case 1, 2, 3:
                System.out.println("spring");
                break;
            case 4, 5, 6:
                System.out.println("summer");
                break;
            case 7, 8, 9:
                System.out.println("autumn");
                break;
            case 10, 11, 12:
                System.out.println("winter");
                break;
            default:
                System.out.println("?");
                break;
        }
    }
}

public class Main {
    public static void main(String... args) {
        
        Integer month = 19;
        
        switch(month) {
            case 1, 2, 3 -> System.out.println("spring");
            case 4, 5, 6 -> System.out.println("summer");
            case 7, 8, 9 -> System.out.println("autumn");
            case 10, 11, 12 -> System.out.println("winter");
            default -> System.out.println("?");
        }
    }
}


public class Main {
    public static void main(String... args) {
        
        Integer month = 19;
        
        String season = switch(month) {
            case 1, 2, 3 -> "spring";
            case 4, 5, 6 -> "summer";
            case 7, 8, 9 -> "autumn";
            case 10, 11, 12 -> "winter";
            default -> "?";
        };
        
        System.out.println(season);
    }
}



```

<br>

---

<br>


【EOF】



[←　README](../README.md)

