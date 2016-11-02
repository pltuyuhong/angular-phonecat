> 该应用 fork 自angular的官方项目angular-phonecat，只是对 `README.md` 做了中文翻译，其他内容保持不变。

# AngularJS 手机商城入门应用

## 简述

该应用将会指引开发者如何通过 AngularJS 来搭建一个网页应用

每一个提交都包含了一小结课程，便于独立分来学习

你可以在这里找到全部的的教程 https://docs.angularjs.org/tutorial.

## 准备条件

### Git

- 工欲善其事必先利其器，查看这里学习如何配置 Git [here][git-setup].
- 你可以在这里下载并且学习 Git 的相关的文档 [here][git-home].

- 下载 [Node.js][node-download]
- 安装依赖包 `npm install`

## 该应用做了什么？

- 该应用程序的结构目录是基于[angular-seed][angular-seed]上开发的。
- 这是一个纯前端的工程，完全没有后端服务的支撑，数据部分我们将使用本地的 JSON 文件来代替。
- 学习 _Development_ 章节来了解如何运行和开发一个 Angular 应用。


## 提交历史既是教程大纲

你可以通过以下命令来签出提交记录，你可以通过以下命令对教程做无顺序阅读。

```
git checkout step-?
```

你可以通过以下命令看到任何两个章节之间的变化，这些变化会直观的体现在代码上。

```
git diff step-?..step-?
```

### 章节0 引导

- 添加了 'angular.js' 脚本
- 添加了 'ngApp' 标签到用来引导应用
- 使用表达式添加了一个简单的网页模板

### 章节1 静态数据

- 添加了一个样式文件 ('app/app.css')
- 添加了一个静态的列表来装载两个手机的数据


### 章节2 Angular 模板（动态模板）

- 将上一步骤的静态列表转换为动态列表，方式：
  - 创建一个 `PhoneListController` 控制器
  - 从 HTML 中解析数据并且传递到控制器里，该数据将持久化到内存中
  - 使用 `ngRepeat` 标签将静态的列表转换为动态的
 - 为`PhoneListController`控制器添加了一个单元测试，该单元测试说明了如何使用 Karma 编写和运行测试
  
### 章节3 组件化

- 介绍组件化
- 将控制器和模板封装为可复用的、独立的 `phoneList` 组件
- 使用 `phoneList` 组件重构应用并且做测试

### 章节4 工程目录结构
  
- 重构工程目录，使应用在未来持续可维护、可扩展
  - 将每一个实体都放在独立文件中
  - 按功能区域而不是功能来组织代码
  - 将代码拆分为其他模块可依赖的模块
  - 在 `.html` 文件中使用外部模板（而不是内联 HTML 字符串）
  
### 章节5 列表搜索

- 添加一个搜索框演示以下内容：
  - 数据绑定是如何根据输入的过条件工作的
  - 如何使用 `filter` 过滤器
  - `ngRepeat` 是如何自动过滤列表中的数据的
- 添加一个端到端的测试用例：
  - 如何编写一个端到端的测试
  - 验证搜索框与过滤器能够彼此协调工作

### 章节6 双向绑定

- 为手机模型添加 `age` 字段
- 为手机列表添加一个用于控制列表排序的下拉框
- 在控制器中覆盖默认的排序方式
- 添加一个端对端的单元测试用以测试本章节的功能

### 章节7 网络资源 & 依赖注入
   
- 更改数据的获取方式，将从内存中获取的方式改为从网络获取（即便如此，数据将会保存在静态文件 `phone.json` 中模拟后台数据）
  - 使用 `$http` 服务来加载 JSON 数据
- 演示了 `服务` 和 `依赖注入`
  - 控制器中可用的的 `$http` 是被注入进来的
  - 介绍了动态注入的注解方法：`.$inject` 和内联数组

### 章节8 模板跳转 & 图片显示

- 添加了一个手机图片和手机详情页的连接
- 添加了一个端到端的测试用来验证详情页的连接
- 调整了 CSS 

### 章节9

- 介绍了 `$route` 服务，允许将深层次的连接地图绑定到相关的页面：
  - 添加了一个 `ngRoute` 依赖模块
  - 配置路由器
  - 在 `index.html` 中使用了 `ngView` 组件
- 创建了一个列表的路由(`/phones`)
  - 将 `/phones` 映射到了现成的 `phoneList` 组件
- 创建了一个手机详情的路由（`/phones/:phoneId`）
  - 将 `/phones/:phoneId` 映射到了一个新的 `phoneDetail` 组件
  - 创建了一个 `phoneDetail` 组件,用来显示当前选中的手机
  - 通过 `$routeParams` 在控制器中传递 `phoneId` 参数
  
### 章节10 更多的模板

- 实现获取所选手机的数据并呈现到视图
  - 在 `PhoneDetailController` 中使用 `$http` 在 JSON 文件中获取手机的详细信息
  - 创建一个用于显示手机详情的视图
- 创建了一个 CSS 样式使手机详情页显得美观

### 章节11 自定义过滤器

- 实现了一个自定义的 `checkmark` 过滤器
- 将 `checkmark` 应用到 `phoneDetail` 视图
- 添加了一个单元测试用以验证 `checkmark` 过滤器是否能正常工作

### 章节12 事件处理器
  
- 为手机列表的缩略图增加点击跳转到详情页的功能
  - 介绍 `PhoneDetailController` 中的 `mainImageUrl` 属性
  - 实现了 `setImage()` 方法用来替换手机图片
  - 为缩略图注册一个 `ngClick` 的事件处理器，用来更改手机图片
  - 添加了一个端到端的测试用例用以验证该功能是否正厂工作

### 章节13 RESTful & 自定义服务

- 将 `$http` 替换为 `$resource`
- 创建一个自定义的 `Phone` 服务作为一个 RESTful 客户端
- 在单元测试中使用自定义 Jasmine 等式测试程序来忽略不相关的属性
  
### 章节14 动画
- 为应用添加动画
  - 使用 `ngRepeat` 的动画来呈现手机列表发生的变化：添加，移除或排序
  - 使用 `ngView` 的动画来呈现视图的切换
  - 以动画的方式呈现从首页跳转到手机详情页
- 展示三种不同类型的动画
  - CSS 过滤动画
  - CSS 时间轴动画
  - JavaScript 控制的动画

## Development with `angular-phonecat`

The following docs describe how you can test and develop this application further.

### Installing Dependencies

The application relies upon various Node.js tools, such as [Bower][bower], [Karma][karma] and
[Protractor][protractor]. You can install these by running:

```
npm install
```

This will also run Bower, which will download the Angular files needed for the current step of the
tutorial.

Most of the scripts described below will run this automatically but it doesn't do any harm to run
it whenever you like.

### Running the Application during Development

- Run `npm start`.
- Navigate your browser to [http://localhost:8000/](http://localhost:8000/) to see the application 
- running.

### Unit Testing

We recommend using [Jasmine][jasmine] and [Karma][karma] for your unit tests/specs, but you are free
to use whatever works for you.

- Start Karma with `npm test`.
- A browser will start and connect to the Karma server. Chrome and Firefox are the default browsers,
  others can be captured by loading the same URL or by changing the `karma.conf.js` file.
- Karma will sit and watch your application and test JavaScript files. To run or re-run tests just
  change any of your these files.

### End-to-End Testing

We recommend using [Protractor][protractor] for end-to-end (e2e) testing.

It requires a webserver that serves the application. See the
_Running the Application during Development_ section, above.

- Serve the application with: `npm start`
- In a separate terminal/command line window run the e2e tests: `npm run protractor`.
- Protractor will execute the e2e test scripts against the web application itself. The project is
  set up to run the tests on Chrome directly. If you want to run against other browsers, you must 
  modify the configuration at `e2e-tests/protractor-conf.js`.


## Application Directory Layout

```
app/                     --> all the source code of the app (along with unit tests)
  bower_components/...   --> 3rd party JS/CSS libraries, including Angular and jQuery
  core/                  --> all the source code of the core module (stuff used throughout the app)
    checkmark/...        --> files for the `checkmark` filter, including JS source code, specs
    phone/...            --> files for the `core.phone` submodule, including JS source code, specs
    core.module.js       --> the core module
  img/...                --> image files
  phone-detail/...       --> files for the `phoneDetail` module, including JS source code, HTML templates, specs
  phone-list/...         --> files for the `phoneList` module, including JS source code, HTML templates, specs
  phones/...             --> static JSON files with phone data (used to fake a backend API)
  app.animations.css     --> hooks for running CSS animations with `ngAnimate`
  app.animations.js      --> hooks for running JS animations with `ngAnimate`
  app.config.js          --> app-wide configuration of Angular services
  app.css                --> default stylesheet
  app.module.js          --> the main app module
  index.html             --> app layout file (the main HTML template file of the app)

e2e-tests/               --> config and source files for e2e tests
  protractor.conf.js     --> config file for running e2e tests with Protractor
  scenarios.js           --> e2e specs

node_modules/...         --> development tools (fetched using `npm`)

scripts/                 --> handy scripts
  private/...            --> private scripts used by the Angular Team to maintain this repo
  update-repo.sh         --> script for pulling down the latest version of this repo (!!! DELETES ALL CHANGES YOU HAVE MADE !!!)

bower.json               --> Bower specific metadata, including client-side dependencies
karma.conf.js            --> config file for running unit tests with Karma
package.json             --> Node.js specific metadata, including development tools dependencies
```


## Contact

For more information on AngularJS, please check out https://angularjs.org/.


[angular-seed]: https://github.com/angular/angular-seed
[bower]: http://bower.io/
[git-home]: https://git-scm.com
[git-setup]: https://help.github.com/articles/set-up-git/
[google-phone-gallery]: http://web.archive.org/web/20131215082038/http://www.android.com/devices/
[jasmine]: https://jasmine.github.io/
[karma]: https://karma-runner.github.io
[node-download]: https://nodejs.org/en/download/
[protractor]: http://www.protractortest.org/
