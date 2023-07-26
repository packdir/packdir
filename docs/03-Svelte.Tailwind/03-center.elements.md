
# 元素居中

Tailwind 有两种方法来居中元素：

1. grid
2. flexbox

大体上来说，grid 用于页面布局，flexbox 用于细节元素。


## grid

使用下面的代码就可以将元素水平居中和垂直居中：

    <div class="grid h-screen place-items-center">
        被居中的内容
    </div>

说明：

- grid

    设置：`display: grid`

- h-screen

    Sets the 100vh (screen-height) as the height

- place-items-center

    设置：`place-items: center`


## flexbox

使用下面的代码实现元素居中：

    <div class="flex items-center justify-center h-screen">
        被居中的内容
    </div>

说明：

- flex

    设置：display: flex

- items-center

    垂直居中

- justify-center

    水平居中

