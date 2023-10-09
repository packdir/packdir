# slug in routing

为了使用 url 参数，创建下面的文件夹结构：

src/routes/blog/[slug]
  |_ +page.js
  |_ +page.svelte


src/routes/blog/[slug]/+page.js 内容为：

```
export const load = ({ params }) => {
    return {
        slug: params.slug
    }
}
```

然后在 +page.svelte 文件中使用：

```
<script>
    /** @type {import('./$types').PageData} */
    export let data;
</script>

<h1>{data.slug}</h1>
```


参考官方文档：[routing](https://kit.svelte.dev/docs/routing#page)

