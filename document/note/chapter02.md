## ***ECMA***
ECMAという団体がJavascriptの言語仕様を決めている。  
機能提案は0から4までの5段階のステージをへて仕様に取り込まれる。

## ***javascriptのスコープについて***
JSでは関数のみスコープを作ることができ、if文やfor文はブロックを持つがスコープはない。  
let,constがスコープ（レキシカルスコープ）を作っている。  
let,constを使っておけば気にする必要はない。

## ***レキシカルスコープ***
調査・・・

## ***Javascriptの関数と関数式の違い***
関数は関数の巻き上げにより想定しない挙動を起こす可能性がある。巻き上げとは、関数の宣言がコードの先頭に移動することを言い、そのため関数を宣言する前から関数を呼び出すことができてしまう。  
関数式では巻き上げが起こらないため、関数宣言のあとに関数の呼び出しという順番を守らなければならない。  
推奨は関数式。

## ***デフォルト引数をオブジェクトにする***
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

## ***アロー関数の省略記法***
・引数がひとつ  
カッコ省略可  
・戻り値が単一の式（;で終わる）  
return省略可  
・function  
アロー関数であれば省略できる  
```ts
// 上記条件があえばインラインで書くことも可能
// 　※インラインとは直列・一列に並んだという意味。または、埋め込むという意味でも利用される。
const testFunction = profile = `私は${profile.name}です。年齢は${profile.age}です。`;
```

## ***Babel***
javascriptのコンパイラ。  
最新JS構文を古い構文にコンパイラして、最新構文に対応していないブラウザでも動かせるようにする。  
babelのコンパイルの様子を確認できるサイト（https://babeljs.io/rep）

## ***デストラクチャリング = 分割代入***
### `ネスト`
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

### `配列の分割代入`
配列もデストラクチャリングできる。
```ts
const [first] = ["たまねぎ", "人参"]
console.log(first) // =>たまねぎ

const [ , second] = ["たまねぎ", "人参"]
console.log(second) // =>人参

```

## ***オブジェクト***
オブジェクトリテラルには関数を埋め込むこともできる。  
アロー関数を持たせることもできるが、非推奨。予期せぬ挙動をするため。
```ts
// {} <= これがオブジェクトリテラル

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
  test(){
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

## ***スプレッド構文***
### `スプレッド構文によるイミュータブルなオブジェクトの実現`  
[...arr]はarrをコピーしているのと同様になる。
```ts
const arr = ["hoge", "foo", "foga"];

const reverseArr = [...arr].reverse();
console.log(arr) // => ["hoge", "foo", "foga"] となるため、arrの構造が変化していないことがわかる。
```

### `関数の引数にスプレッド構文`
関数の引数を配列として受け取ることができる。このとき、引数を任意の数受け取ることができる。
```ts
const hoge = (...arr) => {

}
```

### `オブジェクトとスプレッド構文`
オブジェクトでも可能
```ts
  const foo = {
    a: "A",
    b: "B"
  };
  const hoge = {
    c: "C"
  };
  const hoga = {
    ...foo,
    ...hoge
  };
  console.log({a:"A",b:"B",c:"C"},hoga);
```

## ***スプレッド構文と分割代入を組み合わせる***
要素数がわからない配列を操作してかつ、再定義することが出来る。
```ts
export const spread = () => {
  const arr = ["hoge", "foo", "foga"];

  const [first, ...others] = arr;
  console.log("hoge", first); 
  console.log("foo,foga", others); 
  const [, second, ...others2] = arr;
  console.log("foo", second);
  console.log("foga", others2);
};
```


## ***イミュータブルとは***
イミュータブルとは、作成後に状態を変えることのできないオブジェクトのこと。

## ***破壊的なメソッドとは***
オブジェクトの内容を書き換えるメソッドを破壊的なメソッドという。

## ***モジュール***
Javascriptのモジュールとは再利用可能なコードのこと。import して利用することが出来る。  
なお、import/exportでモジュールを利用する方法はECMAScriptモジュール(ESM)仕様の一部。  
CommonJSモジュールという先発のモジュールもあり、require/exportを使う。  



### メモ
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

スプレッド構文を利用すると、イミュータブルなオブジェクトを実現できる。
[...arr]はarrをコピーしているのと同様になる。
```ts
const arr = ["hoge", "foo", "foga"];

const reverseArr = [...arr].reverse();
console.log(arr) // => ["hoge", "foo", "foga"]
```


イミュータブルとは、作成後に状態を変えることのできないオブジェクトのこと。

オブジェクトの内容を書き換えるメソッドを破壊的なメソッドという。

スプレッド構文と分割代入を組み合わせることで要素数がわからない配列を操作してかつ再定義することが出来る。
```ts
export const spread = () => {
  const arr = ["hoge", "foo", "foga"];

  const [first, ...others] = arr;
  console.log("hoge", first); 
  console.log("foo,foga", others); 
  const [, second, ...others2] = arr;
  console.log("foo", second);
  console.log("foga", others2);
};
```

関数の引数を配列として受け取ることができる。このとき、引数を任意の数受け取ることができる。
```ts
const hoge = (...arr) => {

}
```

配列だけではなくオブジェクトでも可能
```ts
  const foo = {
    a: "A",
    b: "B"
  };
  const hoge = {
    c: "C"
  };
  const hoga = {
    ...foo,
    ...hoge
  };
  console.log({a:"A",b:"B",c:"C"},hoga);
```

Javascriptのモジュールとは再利用可能なコードのこと。import して利用することが出来る。
なお、import/exportでモジュールを利用する方法はECMAScriptモジュール(ESM)仕様の一部

他にはCommonJSモジュールがあり、require/exportを使う。