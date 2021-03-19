## 問題

ランダムな猫の GIF が見られるアプリを作ってみましょう。/* ??? */ の部分を埋めて、コードを完成させてください。

```js
// GIF 共有サイト　GIPHY から持ってきた GIF ID
const gifIds = [
  '10dU7AN7xsi1I4', 'tBxyh2hbwMiqc', 'ICOgUNjpvO0PC',
  '33OrjzUFwkwEg', 'MCfhrrNN1goH6', 'rwCX06Y5XpbLG'
];

// 上記配列の要素をランダムに返す
function getGifId() {
  const max = gifIds.length;
  const index = Math.floor(Math.random() * Math.floor(max));
  return gifIds[index];
}

function Gif({ id }) {
  /* ??? 2章の練習問題1と同様 */
}

function App() {
  /* ??? GIF ID を表す state を生成する */

  const handleClick = () => {
    /* ??? ボタンが押されると GIF 画像が切り替わる */
  };

return (
    <>
      <p>
        <button onClick={handleClick}>play</button>
      </p>
      <Gif id={/* ??? */} />
    </>
  );
}

const root = document.getElementById('root');
ReactDOM.render(<App />, root);
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
    const gifIds = [
      '10dU7AN7xsi1I4', 'tBxyh2hbwMiqc', 'ICOgUNjpvO0PC',
      '33OrjzUFwkwEg', 'MCfhrrNN1goH6', 'rwCX06Y5XpbLG'
    ];

    // 上記配列の要素をランダムに返す
    function getGifId() {
      const max = gifIds.length;
      const index = Math.floor(Math.random() * Math.floor(max));
      return gifIds[index];
    }

    function Gif({ id }) {
      const src = `https://media.giphy.com/media/${id}/giphy.gif`
      return <img src={src} alt='' />
    }

    function App() {
      const [id, setId] = React.useState(getGifId())

      const handleClick = () => {
        setId(getGifId())
      };

      return (
        <>
          <p>
            <button onClick={handleClick}>play</button>
          </p>
          <Gif id={id} />
        </>
      );
    }

    const root = document.getElementById('root');
    ReactDOM.render(<App />, root);
  </script>
</body>
```

