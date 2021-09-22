## Reactとは
ReactはオープンソースのUIライブラリ。

## Node.jsとは
Node.jsはオープンソースソフトウェアのjavascript実行環境。

## npmとは
Node.jsのパッケージ管理システム。

## package.json
npmコマンドでインストールされたnpmパッケージの依存関係を記述したファイル。  
srcファイルとpackage.jsonを共有することで、プロジェクトのクローンができる。

## yarn
後発のNode.jsのパッケージ管理システム。  
現状、npmがアップデートされて便利になったためyarnとの違いはなくなってきている。

TODO: 何が違うのか調査が必要  

### メモ<hr/>
ReactはオープンソースのUIライブラリ。
最新のReactのバージョンは公式のblogで確認できる。(https://ja.reactjs.org/blog/2021/06/08/the-plan-for-react-18.html)

Node.jsはオープンソースソフトウェアのjavascript実行環境。
npmはNode.jsのパッケージ管理システム。jsのオープンソースプロジェクトはnpmパッケージとして公開されており、npmコマンドでローカルにインストールして利用することができる。
npmコマンドでnpmパッケージをインストールすると、package.jsonが作成される。
package.jsonにはプロジェクトの依存関係が記述される。
プロジェクトをクローンしたいときは、ソースコードとpackage.jsonを受け取りnpm installを実行すればpackage.jsonに記述されている依存パッケージがインストールされる。
自身の環境でプロジェクトを始まるなら、空フォルダで npm init -y とすることでpackage.jsonが生成される。
パッケージのインストールは npm install パッケージ名
アンインストールは npm remove パッケージ名

Yarnは後発のパッケージ管理システム。
yarn add パッケージ名でインストール
yarn remove パッケージ名でアンインストールできる。
