### メモ<hr>
ECMAという団体がJavascriptの言語仕様を決めている。機能提案は0から4までの5段階のステージをへて仕様に取り込まれる。

jsは関数にしかスコープがないため、ifやfor文でvarをうっかり使うと想定しない動きになる。
変数はvarを使わないほうが良い。なぜならvarは再代入・再定義可能でスコープを持たないため、想定しない結果を作る。

関数式と関数には違いがある。関数は巻き上げと言うのが起こるため、関数を宣言する前に呼び出しても呼び出すことが出来る。これは、関数がコードの先頭で宣言されているのと同じ状態になっているから。これを巻き上げという。

関数式の場合は、関数式を宣言したあとでないと呼び出すことができない。

関数の引数にはデフォルトの値を設定することができ、オブジェクトを引数にしていすることもできる。
```ts
const default = {
  name: "Yamada Taro",
  age: ""
}

const testFunction = (profile = default) => {
  const {name, age} = profile;
  console.log(name, age);
}
```

アロー関数は引数が1つならカッコが省略できる。また、戻り値が単一の式（;で終わるもの）ならreturnも省略可能。fucntionと書かなくて良いので短くなる。
```ts
const testFunction = profile = `私は${profile.name}です。年齢は${profile.age}です。`;
```

インラインとは直列・一列に並んだという意味。または、埋め込むという意味でも利用される。

babelはjavascriptのコンパイラ。最新JS構文を古い構文にコンパイラして、最新構文に対応していないブラウザでも動かせるようにする。
babelのコンパイルの様子を確認できるサイト（https://babeljs.io/rep）

デストラクチャリング = 分割代入
ネストしてデストラクチャリングすることも可能
```ts
const obj = {
  profile:{
    name:"taro"
  }
}
const {profile:{name}} = obj;
console.log(name); // => taro
```

配列もデストラクチャリングできる。
```ts
const [first] = ["たまねぎ", "人参"]
console.log(first) // =>たまねぎ

const [ , second] = ["たまねぎ", "人参"]
console.log(second) // =>人参

```

オブジェクトリテラルには関数を埋め込むこともできる
```ts
{} <= これがオブジェクトリテラル

// 関数
const funcObj = {
  foo: "value",
  test: function(){
    console.log("test start");
  },
  foga:"value",
}

// ES2015関数
const funcObj = {
  foo: "value",
  function(){
    console.log("test start");
  },
  foga:"value",
}


// アロー関数
const funcObj = {
  foo: "value",
  test: () => {
    console.log("test start");
  },
  foga:"value",
}
```
