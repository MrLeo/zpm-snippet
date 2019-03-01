# [zpm-snippet](https://marketplace.visualstudio.com/items?itemName=MrLeo.zpm-snippet)

应用商店地址: [https://marketplace.visualstudio.com/items?itemName=MrLeo.zpm-snippet](https://marketplace.visualstudio.com/items?itemName=MrLeo.zpm-snippet)

> 智联 ZPFE API 项目 Visual Studio Code 代码片段

# 快捷键

## javascript


- zpfe.init

  ```javascript
  /*
   * @Company: 智联招聘
   * @Author: zhaopin.com
   * @LastEditors: Leo
   * @version: 0.0.0
   * @Date: 2019-02-20 17:17:42
   * @LastEditTime: 2019-02-20 17:18:40
   * @Description: $1
   */
  
  import qs from 'qs'
  import ZPError from '../../util/error'
  import { initHandler, errorHandler, throwIfMiss } from '../../util/'
  
  async function POST (ctx) {
    try {
      const init = await initHandler(ctx, { logged: true })
      let params = {
        loginUserId: init.loginUserId
      }
  
      let { data: res } = await init.$fetch.post(`$2?${qs.stringify(params)}`)
  
      ctx.response.body = res
      // ctx.response.set({ code: 200, data: res, message: res.message || '成功', taskId: res.taskId || ctx.request.headers.get('x-zp-request-id') })
    } catch (err) {
      errorHandler(ctx, err)
    }
  }
  
  async function GET (ctx) {
    try {
      const init = await initHandler(ctx, { logged: true })
      let params = {
        loginUserId: init.loginUserId
      }
  
      let { data: res } = await init.$fetch.get(`$2`, { params })
  
      ctx.response.body = res
      // ctx.response.set({ code: 200, data: res, message: res.message || '成功', taskId: res.taskId || ctx.request.headers.get('x-zp-request-id') })
    } catch (err) {
      errorHandler(ctx, err)
    }
  }
  
  export default { GET, POST }
  ```

- eslint

  ```javascript
  /* eslint-disable */
  ```

  ```javascript
  /* eslint-enable */
  ```

  ```javascript
   // eslint-disable-line
  ```

  ```javascript
   // eslint-disable-next-line
  ```

- cli

  ```javascript
  ctx.log.info(`[standout] $1 -> `, JSON.stringify($2))$3
  ```

- cle

  ```javascript
  ctx.log.error(`[standout] error -> $1`, simplify(err))$2
  ```

- zpthrow

  ```javascript
  throw new ZPError({ code: ${1:res.code || 500}, message: ${2:res.message || '出错了'}, taskId: ${3:res.taskId || ctx.request.headers.get('x-zp-request-id') ||''} })
  ```

- cl

  ```javascript
  console.log(`[$1]$2 -> $3`,$4)$5
  ```

  ```javascript
  console.log(`%c[$1]$2 -> $3`,'color:#1B8BFF;',$4)$5
  ```

- cg

  ```javascript
  console.groupCollapsed(`------------------> $1 <------------------`)
  console.log(`[$2]$3 -> $4`,$5)$6
  console.groupEnd()
  ```

  

# 开发

- [VS Code 插件开发文档-中文版](https://liiked.github.io/VS-Code-Extension-Doc-ZH/#/)
- [vscode 插件开发实践](https://juejin.im/post/5c63a56a6fb9a049e063d491)
- [插件市场](https://marketplace.visualstudio.com/) / [插件管理](https://marketplace.visualstudio.com/manage)

## 准备

```bash
# 插件生成器
npm install -g yo generator-code

# 打包&发布工具
npm install -g vsce

# 初始化代码
yo code
```

## 构建

```bash
# 打包
vsce package
```
