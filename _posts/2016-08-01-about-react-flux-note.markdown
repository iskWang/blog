---
layout: post
title: "About react flux note"
---

這是自己的 ~~Twitter 風格~~ 整理筆記，希望可以幫助一些跟我一樣常常鬼打牆的朋友 Orz

## Why
**One-way data flow**: 就像在 React 的世界裡，只有當下的 **State** 異動才會更動元件 ui。

**flux**: 如果有很多的元件需要處理 State......

## What
![Flux 流程圖](https://facebook.github.io/react/img/blog/flux-diagram.png)

#### Action
一種 Helper 決定 state 處理前 + 處理後的流程

Ex. ajax + parseJSON 行為

#### Dispatcher
Store 之間的支配器，透過 `waitFor` 可以處理不同 store 之間的非同步行為~~，但通常我只有用到一行~~

#### Store
有點像是 MVC 當中的 Model，可以在這裡決定 State 回傳的形式

## 參考
[AndyYou's Blog - [Reactjs] Reactjs 大解密](https://facebook.github.io/react/docs/component-specs.html): 解釋 State 的 life cycle 以及 DOM 是如何在 React 運作

[AndyYou's Blog - Flux 筆記](http://andyyou.logdown.com/posts/241839-flux-notes): Flux 三大元件

[React/Flux in Action 實戰經驗分享](https://speakerdeck.com/coodoo/flux-in-action-shi-zhan-jing-yan-fen-xiang)

[簡單聊一下 One-way data flow、Two-way data binding 與前端框架](http://blog.turn.tw/?p=2948&utm_campaign=CodeTengu&utm_medium=web&utm_source=CodeTengu_33)

[React：引领未来的用户界面开发框架](http://www.phei.com.cn/module/goods/wssd_content.jsp?bookid=42662)

[Yahoo: To-Do flux example](https://github.com/yahoo/fluxible/tree/master/examples/todo)