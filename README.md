<div align="center">
    <div align="right">
        简体中文 | <a href="README-EN.md">English</a>
    </div>
    <h1>shyreckdc.github.io</h1>
    <p>基于 jekyll 的响应式 Github Pages 个人博客网站</p>

[![license](https://img.shields.io/github/license/shyreckdc/shyreckdc.github.io)](https://github.com/shyreckdc/shyreckdc.github.io/blob/master/COPYING)
[![Gitter](https://img.shields.io/gitter/room/shyreckdc/shyreckdc.github.i0)](https://gitter.im/shyreckdc-github-io/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)
[![Website](https://img.shields.io/website?down_color=lightgrey%09&down_message=offline&up_color=%09aqua&up_message=online&url=https%3A%2F%2Fshyreckdc.github.io)](https://shyreckdc.github.io)
[![GitHub deployments](https://img.shields.io/github/deployments/shyreckdc/shyreckdc.github.io/github-pages)](https://github.com/shyreckdc/shyreckdc.github.io/deployments)
![GitHub top language](https://img.shields.io/github/languages/top/shyreckdc/shyreckdc.github.io)

![GitHub stars](https://img.shields.io/github/stars/shyreckdc/shyreckdc.github.io?style=flat)
![GitHub forks](https://img.shields.io/github/forks/shyreckdc/shyreckdc.github.io?style=flat)
![GitHub followers](https://img.shields.io/github/followers/shyreckdc?style=flat)
[![Github issues](https://img.shields.io/badge/issues-welcome-success)](https://github.com/shyreckdc/shyreckdc.github.io/issues)
[![Github pull request](https://img.shields.io/badge/pull%20request-welcome-success)](https://github.com/shyreckdc/shyreckdc.github.io/pulls)

[![GitHub last commit](https://img.shields.io/github/last-commit/shyreckdc/shyreckdc.github.io)](https://github.com/shyreckdc/shyreckdc.github.io/commit/master)
[![GitHub commit activity](https://img.shields.io/github/commit-activity/m/shyreckdc/shyreckdc.github.io)](https://github.com/shyreckdc/shyreckdc.github.io/graphs/commit-activity)
![GitHub repo size](https://img.shields.io/github/repo-size/shyreckdc/shyreckdc.github.io)
</div>

## 特性

- 适配移动端与桌面端展示效果 | [预览](https://shyreckdc.github.io)
- 个性化自动展示 GitHub 项目 | [预览](https://shyreckdc.github.io/projects)
- 文章按类别与标签归档展示 | [预览](https://shyreckdc.github.io/categories)
- 支持搜索框，按关键词搜索全站文章 | [预览](https://shyreckdc.github.io)
- 生动的 “关于” 页面 | [预览](https://shyreckdc.github.io/about)

## 使用

详细搭建教程：[搭建 Github Pages 个人博客网站](https://shyreckdc.github.io/2018/04/01/github-pages-blog)

jekyll 使用教程：<https://www.jekyll.com.cn/>

## 配置

配置文件是位于主目录的 `_config.yml`，关于配置的完整参数介绍和默认值等内容，请查阅官网文档：<https://www.jekyll.com.cn/docs/configuration/>

## 配置开发环境

提交推送代码后，GitHub Pages页面（即博客网站主页）更新较慢，所以推荐搭建本地开发环境，以便调试。

详细教程请见：[安装 jekyll](https://shyreckdc.github.io/2018/04/01/github-pages-blog#%E5%AE%89%E8%A3%85jekyll-)

配置好依赖后在项目主目录运行：
```cmd
bundle exec jekyll s
```

然后会提示浏览器打开 `http://127.0.0.1:4000` 预览网站，正常情况预览效果与 GitHub Pages 展示的一样，这样就可以在本地开发调试好了再推送到 GitHub。

## 用到的第三方库

- [Materialize.css](http://materializecss.com/)：一个不错的样式组件库
- [GeoPattern](http://btmills.github.io/geopattern/)：格式化生成有趣的背景图
- [particles.js](https://marcbruederlin.github.io/particles.js/)：粒子连接效果

## 参考

- https://github.com/ShawnTeoh/matjek

## License

[GPL v3](https://github.com/shyreckdc/shyreckdc.github.io/blob/master/COPYING)
