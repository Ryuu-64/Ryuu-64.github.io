---
title: Hexo 小姿势
date: 2021-01-20 22:54:43
tags:
    - 网页
categories: 前端
---

## Hexo 小姿势

在本地启动 hexo start

(ctrl + c 停止) 

``` console
hexo s
```

创建新的博客文章 new blog
``` console
hexo n "文章名称"
```

 生成文件并部署至仓库 deploy
``` console
hexo d
```

部署的信息在 _config.yml 文件最下的 deploy

//  _config.yml 示例 (记得冒号后要有空格)

``` console
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git 
  repo: https://github.com/Ryuu-64/Ryuu-64.github.io
  branch: master
```

## hexo  小问题

当node 版本过高时会产生以下 Warning

``` javascript
(node:13888) Warning: Accessing non-existent property 'lineno' of module exports inside circular dependency
(Use `node --trace-warnings ...` to show where the warning was created)
(node:13888) Warning: Accessing non-existent property 'column' of module exports inside circular dependency
(node:13888) Warning: Accessing non-existent property 'filename' of module exports inside circular dependency
(node:13888) Warning: Accessing non-existent property 'lineno' of module exports inside circular dependency
(node:13888) Warning: Accessing non-existent property 'column' of module exports inside circular dependency
(node:13888) Warning: Accessing non-existent property 'filename' of module exports inside circular dependency
(node:10816) Warning: Accessing non-existent property 'column' of module exports inside circular dependency
(node:10816) Warning: Accessing non-existent property 'filename' of module exports inside circular dependency
(node:10816) Warning: Accessing non-existent property 'lineno' of module exports inside circular dependency
(node:10816) Warning: Accessing non-existent property 'column' of module exports inside circular dependency
(node:10816) Warning: Accessing non-existent property 'filename' of module exports inside circular dependency
(node:10816) Warning: Accessing non-existent property 'lineno' of module exports inside circular dependency
```

官方的 issues https://github.com/stylus/stylus/issues/2534

### 解决方案

不用改变node的版本

找到项目中的此文件: \node_modules\stylus\lib\nodes\index.js 在最前处添加如下代码即可

``` javascript
exports.lineno = null;
exports.column = null;
exports.filename = null;
```

### 后续问题

结果还是有问题

博客部署出错了 详情如下

``` console
FATAL Something's wrong. Maybe you can find the solution here: https://hexo.io/docs/troubleshooting.html
TypeError [ERR_INVALID_ARG_TYPE]: The "mode" argument must be integer. Received an instance of Object
    at copyFile (fs.js:1972:10)
    at tryCatcher (F:\Users\Ryuu\Documents\GitWork\MyBlog\HexoBlogLib\node_modules\bluebird\js\release\util.js:16:23)
    at ret (eval at makeNodePromisifiedEval (F:\Users\Ryuu\Documents\GitWork\MyBlog\HexoBlogLib\node_modules\bluebird\js\release\promisify.js:184:12), <anonymous>:13:39)
    at F:\Users\Ryuu\Documents\GitWork\MyBlog\HexoBlogLib\node_modules\hexo-fs\lib\fs.js:144:39
    at tryCatcher (F:\Users\Ryuu\Documents\GitWork\MyBlog\HexoBlogLib\node_modules\bluebird\js\release\util.js:16:23)
    at Promise._settlePromiseFromHandler (F:\Users\Ryuu\Documents\GitWork\MyBlog\HexoBlogLib\node_modules\bluebird\js\release\promise.js:547:31)
    at Promise._settlePromise (F:\Users\Ryuu\Documents\GitWork\MyBlog\HexoBlogLib\node_modules\bluebird\js\release\promise.js:604:18)
    at Promise._settlePromise0 (F:\Users\Ryuu\Documents\GitWork\MyBlog\HexoBlogLib\node_modules\bluebird\js\release\promise.js:649:10)
    at Promise._settlePromises (F:\Users\Ryuu\Documents\GitWork\MyBlog\HexoBlogLib\node_modules\bluebird\js\release\promise.js:729:18)
    at Promise._fulfill (F:\Users\Ryuu\Documents\GitWork\MyBlog\HexoBlogLib\node_modules\bluebird\js\release\promise.js:673:18)
    at Promise._resolveCallback (F:\Users\Ryuu\Documents\GitWork\MyBlog\HexoBlogLib\node_modules\bluebird\js\release\promise.js:466:57)
    at Promise._settlePromiseFromHandler (F:\Users\Ryuu\Documents\GitWork\MyBlog\HexoBlogLib\node_modules\bluebird\js\release\promise.js:559:17)
    at Promise._settlePromise (F:\Users\Ryuu\Documents\GitWork\MyBlog\HexoBlogLib\node_modules\bluebird\js\release\promise.js:604:18)
    at Promise._settlePromise0 (F:\Users\Ryuu\Documents\GitWork\MyBlog\HexoBlogLib\node_modules\bluebird\js\release\promise.js:649:10)
    at Promise._settlePromises (F:\Users\Ryuu\Documents\GitWork\MyBlog\HexoBlogLib\node_modules\bluebird\js\release\promise.js:729:18)
    at Promise._fulfill (F:\Users\Ryuu\Documents\GitWork\MyBlog\HexoBlogLib\node_modules\bluebird\js\release\promise.js:673:18)
```

### 最终方案

下载一个 nodejs 的 12.x 的版本

再部署就没有任何问题了

还有问题就把高版本的 nodejs 删除