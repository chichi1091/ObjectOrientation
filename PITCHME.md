### オブジェクト指向プログラミングとデザインパターン
<br/>
<br/>
<br/>
<br/>
<p align="right">
* chiharu terashima
* 2019.xx.xx
</p>

---
### クラスの中に定義できるもの

* クラスはJavaにおける基本単位

```java
// クラス
class SampleClass {
    // フィールド
    String field;

    // コンストラクタ
    SampleClass() {
    }

    // メソッド
    void method() {
        System.out.println(field);
    }
}
```

+++
### クラスの中に定義できるもの

* クラスの中には以下が定義できる
  * コンストラクタ
  * フィールド(属性)
  * メソッド
  * ネストしたクラス(インナークラス)やインターフェース

---
### コンストラクタ

* インスタンス生成時に実行される特別な処理
* コンストラクタはメソッドに似ているがメソッドではない

+++
### デフォルトコンストラクタ

* クラスには1つ以上のコンストラクタが必要
* 省略した場合はデフォルトコンストラクタが生成される
  * 引数を持たない
  * 1つでも定義するとデフォルトコンストラクタは生成されない

---
### インスタンス(1)

* クラスをもとに生成されたオブジェクトをインスタンスという
* `new` 演算子で生成され、生成されたインスタンス毎に個別の状態を持つ

```java
SampleClass instance1 = new SampleClass();
SampleClass instance2 = new SampleClass();
instance1.field = "a";
instance2.field = "b";

instance1.method(); // "a"が表示される
instance2.method(); // "b"が表示される
```

+++
## インスタンス(2)

* 同じインスタンスを参照している場合

```java
SampleClass instance1 = new SampleClass();
SampleClass instance2 = instance1;  // 同じインスタンスを参照
instance1.field = "a";
instance2.field = "b";

instance1.method(); // "b"が表示される
instance2.method(); // "b"が表示される
```

---
### static

* `static` はインスタンスではなくクラスと結びつく
* コンストラクタを除くクラス構成要素全てに付与可能
* `static` なメンバから `static` でないメンバは参照できない

```java
Object instanceField;
static Object staticField;

void instanceMethod() {
    Object i = instanceField;  // OK
    Object s = staticField;    // OK
}

static void staticMethod() {
    Object i = instanceField;  // NG
    Object s = staticField;    // OK
}
```

---
### アクセス

* アクセス範囲を限定するために以下の4つがある

1. private
  * クラスの内部でのみアクセス可能
1. (何も記述しない)
  * 同じパッケージないのでみアクセス可能
1. protected
  * パッケージないと軽症舌クラスのみアクセス可能
1. public
  * 無制限

---
### 抽象クラス

* `abstract` が付与されたクラス
* 継承されることを前提としている
* 抽象クラスの対義語は具象クラス
* 抽象クラスはインスタンス生成できないので継承した具象クラスを生成して使用する
* 抽象メソッドは処理を持たず、継承したクラスで実装する(TemplateMethodパターン)

```java
abstract class SampleAbstractClass {
    // 抽象メソッド
    abstract void methodA();

    // 通常のメソッド
    void methodB() {
        methodA();
    }
}
```

---
### インターフェース

* 抽象メソッドと定数のみが定義できる
* フィールドは暗黙的に `public static final` が付与される
* メソッドには暗黙的に `public abstract` が付与される

```java
interface SampleInterface {
    // 定数
    String CONST = "hoge";

    // メソッド
    void method();
}
```

+++
### 匿名クラス

* 通常のインスタンス生成に続けて、実装を記述する
* 可読性が低下したりするので利用頻度は低い

```java
SampleInterface instance = new SampleInterface() {
    @Override
    public void method() {
        // ...
    }
}
```

+++
### デフォルトメソッド

* Java 8以降で、インターフェースにdefaultメソッドが作成可能に

```java
interface SampleInterface {
    default void method() {
        // ...
    }
}

class SampleClass implements SampleInterface {
    // methodメソッドを定義しなくてもよい
}
```

---
### 列挙値(enum)

* 定義値を宣言する特別なクラス
* `new` 演算子でインスタンス生成はできな

```java
enum Card {
    SPADES("スペード"),
    HEARTS("ハート"),
    DIAMONDS("ダイヤ"),
    CLUBS("クラブ");

    final String name;

    Card(String name) {
        this.name = name;
    }
}
```

---
### アノテーション

* クラス、メンバ、メソッドにメタ情報を付与する

```java
@Override
public String toString() {
    // ...
}
```