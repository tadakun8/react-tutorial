## 問題

以下の HTML に表される DOM を出力する React コードを書いてください。（JSX を使用します。）

```html
<img src="https://media.giphy.com/media/33OrjzUFwkwEg/giphy.gif" alt="" />
```

## ヒント

以下の Gif コンポーネントの中身を実装しましょう。

```js
function Gif({ id }) {
  /* Gif コンポーネントを実装する */
}

const app = <Gif id="33OrjzUFwkwEg" />;

const root = document.getElementById('root');
ReactDOM.render(app, root);
```

## 回答

```html
<body>
  <div id="root"></div>

  <script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"></script>
  <script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/classnames/2.2.6/index.min.js"></script>
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

  <script type="text/babel">
    function Gif({ id }) {
        // 回答
        const src = `https://media.giphy.com/media/${id}/giphy.gif`
        return <img src={src} alt='' />

        // 1行でも書ける
        // return <img src={`https://media.giphy.com/media/${id}/giphy.gif`} alt="" />
    }
    const app = <Gif id="33OrjzUFwkwEg" />;
    const root = document.getElementById('root');
    ReactDOM.render(app, root);
  </script>
</body>
```

