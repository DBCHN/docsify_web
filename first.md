# 开始

这是一个垃圾项目

# 封面

- docsify 默认会加载 `_coverpage.md ` 文件作为封面。
- 可以通过`homepage: 'HOME.md'` 配置项来指定封面。
  
        <!-- index.html -->
        window.$docsify = {
        //指定主页文件,默认为README.md
        homepage: 'HOME.md',
   }

- 封面也可以通过 `coverpage` 配置项来配置。
    

## 忽略副标题 <!-- {docsify-ignore}-->
* 当设置了 `subMaxLevel` 时，默认情况下每个标题都会自动添加到目录中。如果你想忽略特定的标题，可以给它添加`<!-- {docsify-ignore} -->`，则该标题不会出现在侧边栏的目录中。

* 要忽略特定页面上的所有标题，你可以在页面的第一个标题上使用 `<!-- {docsify-ignore-all} --> `。

* 在使用时， `<!-- {docsify-ignore} --> `和 `<!-- {docsify-ignore-all} --> `都不会在页面上呈现。

# 配置项
## loadSidebar
- 类型：`boolean|String`
- 默认值：`true`
    加载自定义侧边栏，参考多页文档。设置为 `true` 后会加载 `_sidebar.md `文件，也可以自定义加载的文件名。

        <!-- index.htm -->
        window.$docsify = {
        // 加载 _sidebar.md
        loadSidebar: true,

        // 加载 summary.md
        loadSidebar: 'summary.md',
        };

## loadNacbar
- 类型：`Number`
- 默认值: `false`
    默认情况下会抓取文档中所有标题渲染成目录，可配置最大支持渲染的标题层级。

        <!-- index.htm -->
        window.$docsify = {
        // 加载 _navbar.md
        loadNavbar: true,

        // 加载 nav.md
        loadNavbar: 'nav.md',
        };


# 封面

>通过设置 `coverpage`参数，可以开启渲染封面的功能。具体用法见配置项[#coverpage]()。

# 必应

>点击这里 [必应](https://cn.bing.com), 然后你就可以打开 [必应搜索](https://cn.bing.com) 的初始页面
