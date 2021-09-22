## ***React***
React (リアクト) は、Facebookとコミュニティによって開発されているユーザインタフェース構築のためのJavaScriptライブラリである。  
React.jsまたはReactJSの名称でも知られている。

## ***Reactを動かすには？***
ReactとReactDOMという二つのライブラリが必要。  
* Reactは、ビューを構築するためのライブラリ。
* ReactDOMは、ビューをブラウザで描画するためのライブラリ。

## ***HTMLの描画***
HTML要素はブラウザによってDOM要素に変換され、描画される

## ***SPA（シングルページアプリケーション）***
AJAXの登場で普及した。  
画面遷移の際にドキュメント全体をロードするのではなく、一部だけロードしてページを部分的に更新するアプリケーション。  
ユーザから見れば画面遷移は起きているが、実際は同じドキュメントを見ていることになる。  
そのドキュメントの更新（DOMの書き換え）を担っているのがJavaScript
## ***DOM API***
ブラウザから提供されているAPI。  
JavaScriptでDOM APIを利用することで画面の更新（DOMの書き換え）を行う。

## ***React（ライブラリ）***
ReactライブラリはDOM APIの呼び出しを一手に引き受けてくれるため、
開発者自身がDOM APIを利用することは意識しない。  
開発者はReactに対してReact要素を渡す（returnする）だけ。  
React要素は指示書のようなもので、ReactはReact要素を受け取り画面の描画を行う。したがってReact要素とDOM要素はそっくりであるが実際は別物。
<hr/>
### ***一旦整理***
HTMLはブラウザによってDOMに変換されたあと、画面に描画される。そのDOM要素を操作するためにブラウザからDOM APIが提供されている。
SPAではJavaScriptがDOM APIを利用することで、DOMの要素を書き換え画面の一部分を更新している。

## ***React要素の作成***
React.createElement()を利用して作成する。
React要素の実態はオブジェクト。実際にReact要素をコンソールログに出力すると、オブジェクトが表示される。  
プロパティには以下がある。
```ts
React.createElement("h1", { id: "test" }, "child");

{
  type,   //要素 例) h1
  key,    //Reactが要素の識別に使う
  ref,    // ref
  props,  // props
  _owner, // 内部的な値
  _store, // 内部的な値
}
```
## ***createElement引数***
* 第1引数
HTMLタグ
* 第2引数
HTML属性  // React要素が持つpropsオブジェクトに格納される
* 第3引数
children(props)  // React要素が持つpropsオブジェクトに格納される


## ***React要素の描画***
React要素の作成ができたらReactDom.render関数にReact要素を渡す。
ReactDomのrender関数によってReact要素はDOM要素に変換され、render関数の第二引数の要素の配下に描画される。

## ***Reactで再現する子要素***
React要素のprops.childrenに子要素が当てられる。  
createElement関数の第三引数以降はすべてchldrenに当てられるため、複数の子要素を宣言することも可能。  
冗長なコードを避けるため、map関数で子要素を作るのがおススメ。

## ***React要素をmapで回す際の注意点***
React要素のchlderenに配列を設定する場合は、配列の各要素が持つReact要素のkeyを設定する必要がある。

## ***Reactのコンポーネント***
コンポーネントとはUI部品のこと。Reactではコンポーネント（画面の部品）を組み合わせUIを構築する。

## ***コンポーネントの実体は関数！？***
コンポーネントはReact要素(createElementの戻り値)を返す純粋関数。
```ts
const test = () => React.createElement('h1',null,'この文字がh1の子要素として描画されるよ。');
// 以下のようなHTMLになる
<h1>この文字がh1の子要素として描画されるよ。</h1>
```

## ***コンポーネントの呼び出し***
```ts
// 第1引数にはコンポーネントを渡す
React.createElement(test,null,null);
```

## ***コンポーネント引数props***
コンポーネントは引数を受け取ることが出来る。
引数にはcreateElementで設定したpropsオブジェクが渡る。
propsオブジェクはcreateElementの第２引数で設定することができる。


## ***コンポーネントの引数であるpropsとReact要素のprops***
全くの別物？。
```
引数のprops：コンポーネント（関数）の引数のこと

React要素のprops：React要素のid属性やReact要素の子要素に関する情報を持ったオブジェクトのこと
```

### Tips:画面の描画の仕組み
1. クライアントからサーバーへのリクエスト
2. サーバーからhtmlファイルを返す
3. クライアント側は受け取ったhtmlファイルを解析して必要な他ファイルをリクエストする
4. htmlを操作しやすくするためにDOMに変換
5. javascriptが読み込まれる(Reactが動く)
6. ReactはDOM APIを利用して画面の描画を行う

https://zenn.dev/ak/articles/c28fa3a9ba7edb
https://zenn.dev/ak/articles/61d25099295372

### Tips:ハードコーディング
動的に変化べき値をコード内に直接書いてしまっている。
```ts
// ハードコード
<button>ボタン</button>
// ハードコードでない
<button>{text}</button>
```