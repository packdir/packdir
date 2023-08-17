# React 小书

[React 小书](https://www.bookstack.cn/read/react-naive-book/1adbb75f21a39690.md)

是什么样的问题导致了我们需要前端页面进行组件化，前端页面的组件化需要解决什么样的问题。后续课程我们再来看看 React.js 是怎么解决这些问题的。

## 第一个例子


在给 LikeButton 类添加了构造函数，这个构造函数会给每一个 LikeButton 的实例添加一个对象 state，state 里面保存了每个按钮自己是否点赞的状态。还改写了原来的事件绑定函数：原来只打印 click，现在点击的按钮的时候会调用 changeLikeText 方法，这个方法会根据 this.state 的状态改变点赞按钮的文本。

```html
    <div class='wrapper'>
        <div class='like-btn'>
        </div>
    </div>

    <script>
        const createDOMFromString = (domString) => {
            const div = document.createElement('div')
            div.innerHTML = domString
            return div
        }

        class LikeButton {
            constructor () {
              this.state = { isLiked: false }
            }

            changeLikeText () {
              const likeText = this.el.querySelector('.like-text')
              this.state.isLiked = !this.state.isLiked
              likeText.innerHTML = this.state.isLiked ? '取消' : '点赞'
            }

            render () {
              this.el = createDOMFromString(`
                <button class='like-button'>
                  <span class='like-text'>点赞</span>
                  <span>👍</span>
                </button>
              `)
              this.el.addEventListener('click', this.changeLikeText.bind(this), false)
              return this.el
            }
        }

        // 实例化之后插入就可以用。
        const btn = new LikeButton()
        const wrapper = document.querySelector('.wrapper .like-btn')
        wrapper.appendChild(btn.render())
    </script>
```

## 前端组件化（三）：抽象出公共组件类

组件类：

```js
  // 这个是一个组件父类，所有的组件都可以继承这个父类来构建。
  class Component {
    setState (state) {
      const oldEl = this.el
      this.state = state
      this.el = this._renderDOM()
      if (this.onStateChange) this.onStateChange(oldEl, this.el)
    }

    // 私有方法 _renderDOM 会调用 this.render 来构建 DOM 元素并且监听 onClick 事件，
    // 所以，组件子类继承的时候只需要实现一个返回 HTML 字符串的 render 方法就可以了。
    _renderDOM () {
      this.el = createDOMFromString(this.render())
      if (this.onClick) {
        this.el.addEventListener('click', this.onClick.bind(this), false)
      }
      return this.el
    }
  }

  // 把组件的 DOM 元素插入页面，并且在 setState 的时候更新页面。
  const mount = (component, wrapper) => {
    wrapper.appendChild(component._renderDOM())
    component.onStateChange = (oldEl, newEl) => {
      wrapper.insertBefore(newEl, oldEl)
      wrapper.removeChild(oldEl)
    }
  }
```


## 6. 使用 JSX 描述 UI 信息

JSX 写法：

```js
class Header extends Component {
  render () {
    return (
      <div>
        <h1 className='title'>React 小书</h1>
      </div>
    )
  }
}
```

经过编译之后，生成符合 JavaScript 语法的结果，用JS对象来表示 HTML 结构：

```js
class Header extends Component {
  render () {
    return (
     React.createElement(
        "div",
        null,
        React.createElement(
          "h1",
          { className: 'title' },
          "React 小书"
        )
      )
    )
  }
}
```




