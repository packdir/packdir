
在 src/components 文件夹中创建文件 Counter.svelte

```svelte
<script>
  let count = 0;
</script>

<button on:click={() => count += 1}>
  Count: {count}
</button>
```

在 +page.svelte 中引入 Counter 组件

```svelte
<script>
  import Counter from '../components/Counter.svelte';
</script>
```

然后就可以使用该组件：

```svelte
<Counter />
```
