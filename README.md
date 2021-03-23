# 厦大 course 文件上传助手

用于在不使用 Flash 的情况下，上传文件到 course.xmu.edu.cn 的 Chrome 拓展。

- [厦大 course 文件上传助手](#厦大-course-文件上传助手)
  - [这是什么？](#这是什么)
  - [使用方法](#使用方法)
    - [在 Google Chrome 上使用](#在-google-chrome-上使用)
    - [在 Microsoft Edge 上使用](#在-microsoft-edge-上使用)
  - [原理](#原理)
  - [兼容性](#兼容性)

## 这是什么？

众所周知在 2021 年之后，Chrome/Firefox/Edge 都停止了对 Flash 的支持，而你厦这个老旧的 course 平台上传个文件还得用 Flash. 这就造成了以上浏览器的用户今年没法正常提交作业了。而学校给出的解决方案是：

![image.png](https://i.loli.net/2021/03/07/feUvjHmh5R2MydK.png)

好家伙，这个新平台到 2077 年能不能用得上我暂且不关心，但这个让我去下载搜狗浏览器的解决方案，让我想起“大连车务段人人都是高手.jpg”。

于是乎，我就整了这么一个活：

![image.png](https://i.loli.net/2021/03/07/pnqjELmPFdY1xiG.png)

这是一个 浏览器 拓展。它能将 course.xmu.edu.cn 提交作业页面中基于 Flash 上传文件方案，替换为基于 fetch() 的上传方案，使你不需要更换浏览器就能上传和提交你的作业，同时在 Windows / Linux / macOS 下都可以直接提交；效果如图：

![image.png](https://i.loli.net/2021/03/07/8LV9pwlncHQ7G4z.png)

![image.png](https://i.loli.net/2021/03/07/u67mDbfY4HglqyR.png)

![image.png](https://i.loli.net/2021/03/07/8Pn6OSCpJBtalAG.png)

## 使用方法

### 在FireFox上使用
- 首先, 请确保您使用的是这个插件的Firefox分支，且您的浏览器是Firefox的最新版本
- 使用Firefox浏览器在Release界面中下载最新的.xpi文件
- 浏览器会自动弹出安装提示，按照界面提示安装即可
- <del>对啊，FireFox好用开源还不要钱，为什么要给谷歌收割，无产阶级的劳动成果不比硅谷资本家的野心奶头乐要香？</del>

### 在Chromiumn内核浏览器上使用
因为我没办法交 5 刀的注册费，因此没有提交到Google网上应用商店。因此需要手动加载此插件：

### 在 Google Chrome 上使用

- 首先，[下载](https://github.com/kirainmoe/xmu-course-upload-helper-chrome-extension/archive/main.zip)并解压这个 Repo
  - 你会得到一个名为 xmu-course-upload-helper-chrome-extension-main 的文件夹

![image.png](https://i.loli.net/2021/03/08/WfaNovxlEt95pMQ.png)

- 打开 Chrome，地址栏中输入 `chrome://extensions` 并回车

![image.png](https://i.loli.net/2021/03/08/OgAY3lZ2zNKusCq.png)

- 打开右上角的 “开发者模式”
- 点击 “加载已解压的拓展程序”

![image.png](https://i.loli.net/2021/03/08/ljSrMQnAU3m8oF9.png)

- 打开解压好的文件夹

![image.png](https://i.loli.net/2021/03/08/oS1IfQ2MHJzjkhd.png)

- 启用插件

![image.png](https://i.loli.net/2021/03/08/RqJBemsLPOzVECu.png)

- 大功告成了。从今以后，你在 course 上交作业就不必再劳烦已经入土的 Flash 了。

### 在 Microsoft Edge 上使用

- 首先，[下载](https://github.com/kirainmoe/xmu-course-upload-helper-chrome-extension/archive/main.zip)并解压这个 Repo
  - 你会得到一个名为 xmu-course-upload-helper-chrome-extension-main 的文件夹

- 打开 Edge，在地址栏中输入 `edge://extensions` 并回车
- 打开左下角的 “开发人员模式”
- 点击右上角的 “加载已解压的拓展”

![image.png](https://i.loli.net/2021/03/08/dwhgJPUAmNCox5q.png)

- 打开解压好的文件夹
- 完成

![image.png](https://i.loli.net/2021/03/08/a1BnomAVqwvtZRy.png)



## 原理

这并不是通过什么神奇的操作实现的。这个 course 系统用的编辑器 CKEditor 使用了 Flash 来实现无刷新上传文件，这在当年也算是主流的操作。

然而，大人，时代变了。现在用 XMLHttpRequest 和 fetch API 也可以做到无刷新上传文件了。

所以这个插件的原理其实就是：

- 通过 Chrome 的插件 API，向页面里插入一个上传对话框，并替换掉原先的上传。
- 使用 fetch API 和 FormData 重写了上传逻辑。
- 把服务器返回的上传文件地址插入到 CKEditor 中。

就这么简单。

## 兼容性

理论上所有 Chromium 内核的浏览器都可以兼容。
由CharlieJ107提供的Firefox插件已经在Firefox 86.0.1（64位）版本上进行测试。

P.S：
**如果你使用国内IP搜索Firefox或者直接登陆www.mozilla.org，通常会被劫持到<del>中 国 特 色</del> Firefox的网址（www.firefox.com.cn），这个网址不是Mozilla的官方页面，其提供的Firefox浏览器也不是官方原版的Firefox浏览器，本插件不能保证在特 色浏览器上正常运行。请各位用户注意甄别，慎防上当受骗。**
