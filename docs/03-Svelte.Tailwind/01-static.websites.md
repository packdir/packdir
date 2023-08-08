
[Building your static website with Svelte, SvelteKit and TailwindCSS](https://dev.to/robertobutti/how-to-start-building-your-static-website-with-svelte-and-tailwindcss-hbk)

流程已经走通，参考上面的文章，把整个过程记录下来。


## 安装 SvelteKit

初始化项目：

    npm create svelte@latest my-app
    cd my-app
    npm install
    npm run dev -- --open

index 页面是 `src/routes/+page.svelte`，修改它，可以看到页面的变化。


## 安装 TailwindCSS

进入项目根目录，安装：

    npm install -D tailwindcss postcss autoprefixer
    npx tailwindcss init -p

将生成两个文件：

    tailwind.config.js
    postcss.config.js


### 导入 vitePreprocess（略过）

（在目前的最新版本中，这一步已经自动完成了，因此无需任何操作。）

在 svelte.config.js 文件中，导入 vitePreprocess，这样就可以将 `<style>` 处理为 PostCSS 的块。导入示例代码如下：

```
import adapter from '@sveltejs/adapter-auto';
import { vitePreprocess } from '@sveltejs/kit/vite';
/** @type {import('@sveltejs/kit').Config} */
const config = {
  kit: {
    adapter: adapter()
  },
  preprocess: vitePreprocess()
};
export default config;
```

### 配置模板路径

在 tailwind.config.js 中配置模板路径：

```
/** @type {import('tailwindcss').Config} */
export default {
  content: ['./src/**/*.{html,js,svelte,ts}'],
  theme: {
    extend: {}
  },
  plugins: []
};
```

### app.css

创建文件 `./src/app.css`，内容如下：

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### 导入css

创建文件 `./src/routes/+layout.svelte`，内容如下：

```
<script>
  import "../app.css";
</script>

<slot />
```


## 生成静态网站

Svelte 文档：[Static site generation](https://kit.svelte.dev/docs/adapter-static)

安装：

    npm i -D @sveltejs/adapter-static@latest

修改 svelte.config.js：

```
import adapter from '@sveltejs/adapter-static';

export default {
    kit: {
        adapter: adapter({
            // default options are shown. On some platforms
            // these options are set automatically — see below
            pages: 'build',
            assets: 'build',
            fallback: undefined,
            precompress: false,
            strict: true
        })
    }
};
```

创建文件 `./src/routes/+layout.js`：

```
// This can be false if you're using a fallback (i.e. SPA mode)
export const prerender = true;
```



## 编译与部署

编译：

    npm run build

使用 rsync 同步编译好的静态文件，完成部署：

    rsync -va -e "ssh -i /path/to/your.pem" build/ ubuntu@1.1.1.1:/path/to/directory

上面是使用 pem 密钥，将 build 目录的内容复制到服务器的相应路径中。


