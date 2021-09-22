## ***createElementは使わない？***
createElementは使わずJSXを使って書くのが当たり前。

## ***JSX？***
JavaScriptXMLを表す。  
コード内にXMLのようなマークアップ（タグを使って文書に構造を持たせる）を記述できるようにJSを拡張した言語のこと。  
createElement()の呼び出しをネストすることで構造を作ることができたが、大変見づらいのでJSXを使ってcreateElementの記述を再現していく。

## ***JSXを使ってReact要素を記述***
以下のようにHTMLに見えるが実際はReact要素を表すJSX
```ts
//このように書くことでReact要素オブジェクトtypeを記述する
<h1> 
//props.childrenはJSXタグで囲まれた値で決まる
<h1>child</h1>
```

## ***コンポーネントをJSXで表す***
```ts
// createElement
React.createElement(test,{id="test"}) 
// JSX
<test id="test"/>
```

## ***JSX内にJSを記述する***
{}でJSを囲むことで利用することが出来る。JSX内のJSをJavaScript式という。

## ***JS内にJSXを記述する***
普通に記述できる。

### tips: jsxはjsに変換される
jsxは結局のところcreateElementのシンタックスシュガーなので、最終的にはjsに変換される。変換（コンパイル）ツールとしてBabelが存在する。

## ***propsをスプレッド構文で渡す***
注意点としてすべて渡すので必要のない要素まで渡す可能性がある。
※typescriptで制御等すればOK?
```ts
<test {...arr}>
```

## ***webpack***
モジュールバンドラ。
普通Reactの開発では機能をモジュールごとにわけ管理する。
したがって、モジュールバンドラを利用することで複雑なモジュールの組み合わせがコンパクトな構造になりブラウザでのロードが高速になる。

## ***モジュールバンドラ***
異なる複数のファイル(HTMLやcss、JSX、ES.nextなど)を単一のファイルに結合するためのツール。
統合することをモジュール化という。

## ***プロジェクトの作成***
1. npm init -yでpackage.jsonを作る
2. reactとreact-domをnpm install
3. コード製造
4. webpackのインストール（ビルド環境の構築）
5. babelのインストール
6. babelのプリセットインストール
JSXやES.nextをブラウザが理解出来るコードにコンパイルすることができる
7. webpackの設定
デフォルトの設定が効くが、カスタマイズするならプロジェクトのルートディレクトリに「webpack.config.js」を作成。

## ***dependencies***
CRAしたときに自動で作成されるreact-scriptsにはBabel・ESLint・webpackなどのあらかじめ設定済みのツールが含まれている。