# 使用 GitHub Pages 和 VuePress 搭建网站

**参考文档：**

- 参考地址：[GitHub Pages](https://pages.github.com/)
- 参考地址：[VuePress 中文网](http://caibaojian.com/vuepress/)

 **目前效果：**

![1545656821121](https://raw.githubusercontent.com/bd2star/img_commin/master/1545656821121.png)



## 1. 目录

​	

[TOC]



## 2. 前言

``` txt

一般的网站，大体由三部分组成：域名、服务器部署环境以及部署代码。
1. GitHub Pages，由 GitHub 网站服务，为众多 GitHub 用户提供了良好的服务器部署环境以及域名的好工具。		【Github Pages 官网 https://pages.github.com/】
2. VuePress，是以 Vue 为驱动的主题系统的简约静态网站生成工具 balabala……它是咱尤雨溪大神折腾出来的一个工	 具，初始目的是为了方便他使用 Markdown 语法来写文档，然后生成 HTML 代码，部署到服务器上即可。在众多网友	的修改下，它可以拿来写静态网站，也就是可以拿来发布我们编写的博文。
   【VuePress 官网 http://caibaojian.com/vuepress/】

	
```



 ## 3.基础配置

### 3.1搭建GitHub Pages

``` txt
1. 新建仓库( New repository )，在仓库名( Repository name )中输入 用户名.github.io，例如我的就是：bd2star.github.io，然后点击 Create repository 即可创建一个部署好的环境
2. clone 项目至电脑，并新增 README.md 和 index.html 修改 README.md 和 index.html内容
3. 上传到 GitHub
4. 浏览器访问 hhtp://用户名.github.io

```

![1545657554873](https://raw.githubusercontent.com/bd2star/img_commin/master/1545657554873.png)

``` shell
# 运行如下命令 clone项目 新增README.md 新增
git clone https://github.com/bd2star/bd2star.github.io.git
touch README.md
touch index.html

# 修改新建文件的内容
vim README.md
vim index.html

# 上传到GitHub上
git add .
git commit -m "Github Pages"
git push

```

> README.md

``` md
Hello Github Pages
===

&emsp;这是我的 GitHub Pages 初始目录
```

> index.html

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Hello Github Pages</title>
    <style>
        .container {
            margin-top: 300px;
            text-align: center;
        }
    </style>
</head>
<body>
    <h1 class="container">Hello Github Pages</h1>
</body>
</html>
```

> 上传完github后可直接浏览器访问  返回如下(即index.html文件的内容)

![1545658142208](https://raw.githubusercontent.com/bd2star/img_commin/master/1545658142208.png)



如上，完成 GitHub Pages 的搭建，现在我们已经拥有了一个免费部署静态页面的平台了。那么，下面我们将讲解如何通过 Markdown + VuePress 来编写博客。

### 3.2搭建VuePress

``` txt
1.安装 VuePress
在你需要的存放的目录中,通过终端命令行安装VuePress
2.创建目录及部署代码 (根路径下创建 docs 文件夹，并在 docs 文件夹下创建 README.md 文件)
3. 修改package.json文件内容 以及docs/README.md文件内容
4. 终端执行命令 npm run dev
5. 可执行 npm run build 对代码进行压缩打包(会生成.vuepress文件夹 里面存放结构样式行为等) 
```

> 步骤一

![1545658648307](https://raw.githubusercontent.com/bd2star/img_commin/master/1545658648307.png)

> 步骤二

![1545659212036](https://raw.githubusercontent.com/bd2star/img_commin/master/1545659212036.png)

> 步骤三  package.json

``` json
{
  "scripts": {
    "dev": "vuepress dev docs",
    "build": "vuepress build docs"
  },
  "devDependencies": {
    "vuepress": "^0.14.8"
  }
}
```

> 注:

- `npm run dev` 即可开始实时编辑模式
- `npm run build` 即可对代码进行压缩打包，打包后的文件夹在 `.vuepress/dist` 上。



``` shell
# 安装VuePress命令
npm i vuepress -D

```

> 步骤三 README.md

``` md
Hello VuePress
===
```



最后在终端执行命令 `npm run dev`，并打开 `http://localhost:8080`，得到初步配置界面如下：

![1545659097065](https://raw.githubusercontent.com/bd2star/img_commin/master/1545659097065.png)

![1545659188046](https://raw.githubusercontent.com/bd2star/img_commin/master/1545659188046.png)

可执行 npm run build  代码进行压缩打包 会生成.vuepress目录

执行后目录如下:

![1545659418040](https://raw.githubusercontent.com/bd2star/img_commin/master/1545659418040.png)

#### 3.2.1目录讲解

1. 新增如下文件夹及文件 此时目录结构如下

![1545659627332](https://raw.githubusercontent.com/bd2star/img_commin/master/1545659627332.png)

``` txt
- docs                   - VuePress 存放目录
 - .vuepress             - VuePress 配置目录
  - public               - 共用文件存储目录
   - img                 - 共用图片目录
    - banner.png         - 图片-首页 banner
    - logo.ico           - 图片-网站右上角小图标
  - config.js            - VuePress 的 js 配置文件
 - listOne               - 侧边栏项目组1
  - pageOne.md           - 项目组1页面1
  - README.md            - 项目组1默认页面
 - listTwo               - 侧边栏项目组2
  - pageThree.md         - 项目组2页面3
  - pageTwo.md           - 项目组2页面2
  - README.md            - 项目组2默认页面
 - README.md             - 网站默认首页
+ node_modules           - node 依赖包
- package.json           - webpack 配置文件

```

其中，`.vuepress` 存放 VuePress 的配置目录，`public` 中存放共有的文件，`config.js` 为 VuePress 的配置文件，`listOne`、`listTwo` 是侧边栏组，对页面进行个分类。

#### 3.2.2 导航栏

在这里，我们开始进行顶部导航栏的配置。
 首先，我们填写下 `config.js` 中的配置代码

> config.js

``` js
module.exports = {
    // 左上角标题
    title: 'bd2star 的文档库',
    // 描述
    description: 'To be or not to be,that\'s a question.',
    // 头部部署，右上角小图标
    head: [
        // ico 配置
        ['link', {
            rel: 'icon',
            href: '/img/logo.ico'
        }]
    ],
    // 主题部署
    themeConfig: {
        /**
         * 右侧导航条
         * text - 显示字段
         * link - 链接：注意前后带 / 符号
         */
        nav: [
            {
                text: '主页',
                link: '/'
            },
            {
                text: 'API',
                link: '/api/'
            },
            /**
             * 多级菜单
             * 开头 text 为一级标题
             * 数组内 text 为二级标题
             * link 为链接，注意带 /
             */
            {
                text: '博文',
                items: [
                    {
                        text: 'Git相关知识点',
                        link: 'https://blog.csdn.net/zbx931197485/article/details/84838255'
                    },
                    {
                        text: 'Vue处理五星评分',
                        link: 'https://blog.csdn.net/zbx931197485/article/details/83146546'
                    }
                ]
            },
            {
                text: '关于',
                link: '/about/'
            },
            // 链接到网站
            {
                text: 'Github',
                link: 'https://www.github.com/bd2star'
            }
        ]
    }
}

```

然后，启动 `npm run dev`，打开 `http://localhost:8080`，你可以看到导航栏部署完毕了。

![1545659862084](https://raw.githubusercontent.com/bd2star/img_commin/master/1545659862084.png)



#### 3.2.3 侧边栏

VuePress 中的侧边栏配置，一共有三种方式：简单配置，按组配置，分页配置，有兴趣的小伙伴可以去：[地址](http://caibaojian.com/vuepress/default-theme-config/#%E4%BE%A7%E8%BE%B9%E6%A0%8F-sidebar) 直接查看，这里我们单纯讲下我们部署我们的文档库用到的分页配置。

新增为文件夹及文件  此时目录结构如下:

![1545660020889](https://raw.githubusercontent.com/bd2star/img_commin/master/1545660020889.png)

然后，继续修改下 `config.js` 添加分组侧边栏：

> config.js

``` js
module.exports = {
    // 左上角标题
    title: 'bd2star 的文档库',
    // 描述
    description: 'To be or not to be,that\'s a question.',
    // 头部部署，右上角小图标
    head: [
       // 略 上面文件中有
    ],
    // 主题部署
    themeConfig: {
        /**
         * 右侧导航条
         * text - 显示字段
         * link - 链接：注意前后带 / 符号
         */
        nav: [
            // 略 上面文件中有
        ],
        sidebar: {
            // 侧边栏在 /index/ 目录上
            '/index/': [
                ['', 'README'],
                ['indexTwo', '导航第二页']
            ],
            // 侧边栏在 /about/ 目录上
            '/about/': [
                ['', 'README'],
                ['GithubPages', 'GithubPages'],
                ['VuePress', 'VuePress']
            ]
        }
    }
}

```

最后，我们运行 `npm run dev`，查看 `http://localhost:8080` 所示如下：

![1545660243287](https://raw.githubusercontent.com/bd2star/img_commin/master/1545660243287.png)

![1545660259166](https://raw.githubusercontent.com/bd2star/img_commin/master/1545660259166.png)

可以看出，我们已经成功配置了分页形式的侧边栏。

#### 3.2.4 默认首页设置

VuePress 为我们设置了一套默认的首页，我们直接拿来用，看看它长什么样子吧！

 首先，我们找一张 banner.png 图，放到 `public/img/banner.png` 上。
 然后，我们修改下 `docs/README.md` 文件：

> docs/README.md

``` md
---
home: true
heroImage: ./img/banner.jpg
actionText: 皮皮虾 我们走 →
actionLink: /index/
features:
- title: 装逼
  details: 在这里，你可以看到 bd2star 在这里无限装逼，所以你可以尽情打脸。就算你懂，没关系，打了脸再说~
- title: 搞笑
  details: 在这里，你可以获得各种学习欢乐，轻松进击编程的奥妙。点滴进步，成就不一样的你。
- title: 深沉
  details: 在这里，你可以收获一个匠心精神作者的情怀，感受在这个烦躁的社会,如何安身立命。
footer: bd2star 的文档库 | Copyright © 2018 不疯魔不成活
---

```

OK，由于我们重新修改了首页（即 docs/README.md），所以我们重新重启下，`Ctrl+C` -> `y` -> `npm run dev`，重新打开 `http://localhost:8080`：

![1545660393168](https://raw.githubusercontent.com/bd2star/img_commin/master/1545660393168.png)

``` txt
ps：可在md文件中配置如下 指定侧边栏是否强制仅包含当前页、目录深度(0-2即h2、h3)、以及开启关闭上一个或下一个
具体配置参考 

---
# 自动生成仅包含当前页面的标题链接的侧边栏
# sidebar: auto  
# 默认深度是 1，它提取 h2 标题。将其设置为 0 将禁用标题链接，最大值为2，同时提取 h2 和 h3 标题
sidebarDepth: 2  
# 上一页/下一页链接
prev: false 
next: ./全域微信端
---
```



这样 基础配置就已完成！！！

### VuePress进阶篇(待更新)

