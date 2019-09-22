## オブジェクト指向プログラミング
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

---
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

---
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

---
## インスタンス(2)

```java
SampleClass instance1 = new SampleClass();
SampleClass instance2 = instance1;  // 同じインスタンスを参照
instance1.field = "a";
instance2.field = "b";

instance1.method(); // "b"が表示される
instance2.method(); // "b"が表示される
```