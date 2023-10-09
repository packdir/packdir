
[The use directive](https://learn.svelte.dev/tutorial/actions)，也称为 Actions。

Actions 是元素级别的函数。它们的功能包括：

- 作为第三方库的接口
- 懒加载图片
- tooltips
- 增加定制化事件句柄


## 另一个介绍与举例

其工作方式：

You take any native component (like an input, a button, or a div) and assign it a function that is executed on the DOM node of the component when the component is mounted.

下面是一个原始的input：

    <input type="text" class="ui-input" placeholder="Name" title="Name">

现在要给它加一个功能：获得焦点时，自动全选内容。

第一步，写一个处理函数：

```
/** Selects the text inside a text node when the node is focused */

export function selectTextOnFocus(node) {
  
  const handleFocus = event => {
    node && typeof node.select === 'function' && node.select()
  }
  
  node.addEventListener('focus', handleFocus)
  
  return {
    destroy() {
      node.removeEventListener('focus', handleFocus)
    }
  }
}
```

第二步，给input指定该函数：

    <input type="text" class="ui-input" placeholder="Name" title="Name use:selectTextOnFocus>



## React

相比下面的 React 的做法：

Let’s say you want some of your input fields to automatically select all text on focus. Especially when coming from a framework like React, it might feel very tempting to start creating a component wrapper around the input (i.e. <input> becomes <Input/>) and add your custom event handlers in there.

