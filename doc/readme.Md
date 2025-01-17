<h1 align='center'>Chartero</h1>
<p align='center'>
    <a href="https://app.codacy.com/gh/volatile-static/Chartero/dashboard?utm_source=gh&utm_medium=referral&utm_content=&utm_campaign=Badge_grade">
        <img src="https://app.codacy.com/project/badge/Grade/e9a03b20fb90462180218819b41eb34d" alt='代码质量' />
    </a>
    <a href='../src/'>
        <img src='https://img.shields.io/github/languages/code-size/volatile-static/Chartero?logo=vuedotjs' alt='代码量' />
    </a>
    <a href='https://github.com/volatile-static/Chartero/releases/latest/download/chartero.xpi'>
        <img src='https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.github.com%2Frepos%2Fvolatile-static%2FChartero%2Freleases%2Flatest&query=%24.assets%5B0%5D.size&suffix=%20字节&label=插件大小&logo=Zotero&logoColor=%23CC2936' alt='插件' />
    </a>
    <a href='https://gitee.com/const_volatile/chartero/releases'>
        <img src="https://img.shields.io/github/downloads/volatile-static/Chartero/total?logo=github" alt='下载' />
    </a>
    <a href='https://gitee.com/const_volatile/chartero/releases/latest'>
        <img src="https://img.shields.io/github/downloads/volatile-static/Chartero/latest/total" alt='最新版' />
    </a> 
</p>
<p align='center'>
    <a href='../README.md'>English</a> | <kbd>简体中文</kbd>
</p>

## 简介

_Chartero_ 这个名字是连接了 **Char**t 与 Zo**tero**，作为一个[Zotero](https://www.zotero.org/)插件，它可以帮助你更直观地了解你的文献库。

## 使用指南

-   ⚠️ 从 Zotero**6**旧版更新后请先前往首选项页面导入旧版历史数据后再使用！！！

### 旧版数据迁移

新版本记录格式采用 note 与附件一、一对应的形式。若当前电脑使用过旧版 chartero，则可在*首选项->存储*中点击“自动搜索并导入旧版数据”按钮，否则需要手动复制旧版 json 数据到文本框中再点击“导入粘贴的历史记录”按钮。**导入时会覆盖已有的新版记录。**

此外，旧版扫描周期以毫秒为单位，新版以秒为单位，**自动导入**时会自动将周期除以 1000，否则需手动修改！。

<details>
<summary>👉 <b>主要功能</b> 👈</summary>

|                     截图                      | 功能                                                                                                                                  |
| :-------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------ |
|            ![阅读记录](record.jpg)            | `Chartero`的核心功能，当你阅读文献时，记录当前页面与时间。                                                                            |
|            ![最近在读](recent.png)            | 在主菜单`文件`中，可以打开最近读过的文档。                                                                                            |
|             ![进度列](column.png)             | 在文库视图中新增一列信息显示当前条目的阅读时长。                                                                                      |
|           ![仪表盘](dashboard.jpg)            | 可视化与当前条目相关的所有信息，在阅读器的侧边栏可实时刷新。                                                                          |
|           ![分类统计](summary.jpg)            | 总结多个条目之间的关系，若选中条目数超过首选项中设置的值，则不会加载。                                                                |
|            ![小地图](minimap.gif)             | 在阅读器滚动条旁边，灰色块表示对应页面的阅读时长，彩色条表示注释。                                                                    |
|           ![文库总览](overview.jpg)           | 点击`主菜单 → 查看 → 文库总览`后弹出标签页                                                                                            |
| ![提取图片](images.png) ![加载更多](more.png) | 在阅读器左侧边栏显示当前文档中的所有图片。单击可跳转，双击可复制。若 PDF 图片过多，则每次只加载 10 页，点击最下方按钮可手动加载更多。 |

</details>

### [FAQ](https://gitee.com/const_volatile/chartero/issues?label_ids=180755057&label_text=faq&program_id=&project_id=const_volatile%2Fchartero&state=all)

## 开发指南

-   [![Using Zotero Plugin Template](https://img.shields.io/badge/Using-Zotero%20Plugin%20Template-blue?style=flat-square&logo=github)](https://github.com/windingwind/zotero-plugin-template)

-   图表采用 [![Highcharts](https://img.shields.io/github/package-json/dependency-version/volatile-static/Chartero/highcharts?logo=npm)](https://www.npmjs.com/package/highcharts) 生成
-   [Minimap](../src/bootstrap/modules/minimap/)采用内置 [![GitHub package.json dependency version (dev dep on branch)](https://img.shields.io/github/package-json/dependency-version/volatile-static/chartero/dev/%40types%2Freact?logo=npm)](https://zh-hans.react.dev/) 渲染
-   UI 组件库使用 [![T-Design](https://img.shields.io/github/package-json/dependency-version/volatile-static/Chartero/tdesign-vue-next?logo=npm)](https://tdesign.tencent.com/vue-next)
-   欲参考纯 JavaScript 版本（适用于 Zotero `6`）请[切换分支](https://gitee.com/const_volatile/chartero/tree/js_overlay/)

### 目录结构

-   [addon](../addon/)：存放插件所需的资源文件，详见[模板](https://github.com/windingwind/zotero-plugin-template)
-   [tools](../tools/)：存放开发环境所需的脚本文件等
-   src
    -   [src/bootstrap](../src/bootstrap/)：主窗口环境中运行的代码
        -   [src/bootstrap/modules](../src/bootstrap/modules/)：各个功能模块的实现细节
    -   [src/vue](../src/vue/)：使用 [Vue](https://cn.vuejs.org/) 的 `iframe` 页面
        -   [src/vue/summary](../src/vue/summary/)：分类统计（在文件夹的侧边栏）
        -   [src/vue/dashboard](../src/vue/dashboard/)：仪表盘（在普通条目的侧边栏）
        -   [src/vue/overview](../src/vue/overview/)：文库概览（单独标签页）
        -   [src/vue/utility](../src/vue/utility/)：一些辅助代码

### 全局变量

与其他插件不同，Chartero 没有在全局 Zotero 变量下定义任何对象，仅可通过侧边栏 iframe 窗口访问`window.addon`。

在*src/bootstrap*与*src/vue*中各有一个 global.d.ts 文件，定义了该目录下可访问的全局变量。
由[zotero-types](https://github.com/windingwind/zotero-types)定义的`Zotero`等变量在 Vue 中**未定义**。
`addon`是整个插件内部的“全局”变量，定义在 SandBox 中，插件外不可访问。新建 iframe 时通过`contentWindow`将其传入 Vue。

### 默认设置

[package.json](../package.json)的`config.defaultSettings`字段定义了插件使用的所有首选项及其默认值，编译时将自动替换[addon](../addon/)中相应内容，**同时在 TS 中提供类型检查**。

### 多语言

[locale](../addon/locale/)文件夹下定义了不同语言在 UI 上显示的字符串，插件启动时动态加载，**同时在 TS 中提供类型检查**。

### 开发环境

[package.json](../package.json)中定义了构建项目所需的 npm 脚本，修改[tools/zotero-cmd.json](../tools/zotero-cmd-template.json)后，在 vscode 的调试面板中选择`restart-all`即可全部编译并运行 Zotero。使用`build-dev`指令时，全局变量`__dev__`为`true`，插件进入调试模式，此时[debug.ts](../src/bootstrap/modules/debug.ts)会注册一些调试用的选项。

### 阅读记录结构

[history/data.ts](../src/bootstrap/modules/history/data.ts)定义了阅读记录的数据结构。转换成 JSON 字符串后的形式如下：

```json
{
    "pages": {
        "0": {
            "p": {
                "1693200000": 6
            }
        }
    },
    "numPages": 27
}
```

其中`pages`为页码与记录的映射，`numPages`为总页数。`p`意为 **“period”**，其键为时间戳，值为记录**周期**（单位：秒）。

### 插件间兼容性

> 一些不太优雅的实现，可能导致潜在的兼容性问题，供其他插件开发者查错时参考。

-   篡改了`Zotero.Search`对象的`search`方法，使其无法搜索到存储历史记录的笔记条目。

-   显示“所有图片”的侧边栏添加时给其他选项卡按钮添加了点击事件，可能导致冲突。

-   打开“文库总览”时`contextPane.js`会抛出异常`extraData[ids[0]] is undefined`，忽略即可。

## 友情链接

-   [🤩 Awesome Zotero Plugins](https://plugins.zotero-chinese.com/charts.html)

---

<br />
<p align='center'><img src='../addon/content/icons/icon32.png' alt='图标' /></p>
