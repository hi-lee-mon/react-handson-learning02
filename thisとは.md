## this
関数を呼び出すオブジェクトへのリンクと考える。
以下のthisはtestオブジェクトの～という意味。
```ts
const test = {
  type: "function"
  getType = () => return this.type;
}
```