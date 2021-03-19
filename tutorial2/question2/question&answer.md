## 問題

以下の HTML に表される DOM を出力する React コードを書いてください。（JSX を使用します。）

```html
<section id="react" class="box">
  <h1 class="title">React</h1>
  <dl class="definition">
    <dt class="definition-title">Initial release</dt>
    <dd class="definition-content">2013/5</dd>
    <dt class="definition-title">Github stars</dt>
    <dd class="definition-content">147,940</dd>
  </dl>
</section>
<section id="vue" class="box">
  <h1 class="title">Vue.js</h1>
  <dl class="definition">
    <dt class="definition-title">Initial release</dt>
    <dd class="definition-content">2014/2</dd>
    <dt class="definition-title">Github stars</dt>
    <dd class="definition-content">163,165</dd>
  </dl>
</section>
<section id="angular" class="box">
  <h1 class="title">Angular</h1>
  <dl class="definition">
    <dt class="definition-title">Initial release</dt>
    <dd class="definition-content">2016/9</dd>
    <dt class="definition-title">Github stars</dt>
    <dd class="definition-content">60,571</dd>
  </dl>
</section>
```

## ヒント

1. Section, DefinitionList の2つのコンポーネントを作成してください。
2. Section は、id, title, 子要素の3つの props を取ります。title で渡された文字列は、`<h1>` 要素に描画されます。
3. DefinitionList は、props として items を取ります。items は以下の形式の配列で、title が `<dt>` 要素に、content が `<dd>` 要素に描画されます。
```js
[
  { title: '...', content: '...' },
  { title: '...', content: '...' }
]
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
    function Section({ id, title, children }) {
      return (
        <section id={id} className='box'>
          <h1 class="title">{title}</h1>
          {children}
        </section>
      )
    }
    function DefinitionList({ items }) {
      return (
        <dl className="definition">
          { items.map(item => (
              <React.Fragment key={item.title}>
                <dt class="definition-title">{item.title}</dt>
                <dd class="definition-content">{item.content}</dd>
              </React.Fragment>
            ))
          }
        </dl>
      )
    }
    const app = (
      <>
        <Section id="react" title="React">
          <DefinitionList
            items={[
              { title: 'Initial release', content: '2013/5' },
              { title: 'Github stars', content: '147,940' }
            ]}
          />
        </Section>
        <Section id="vue" title="Vue.js">
          <DefinitionList
            items={[
              { title: 'Initial release', content: '2014/2' },
              { title: 'Github stars', content: '163,165' }
            ]}
          />
        </Section>
        <Section id="angular" title="Angular">
          <DefinitionList
            items={[
              { title: 'Initial release', content: '2016/9' },
              { title: 'Github stars', content: '60,571' }
            ]}
          />
        </Section>
      </>
    );
    const root = document.getElementById('root');
    ReactDOM.render(app, root);
  </script>
</body>
```

