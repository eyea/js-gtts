# js-gtts
内置基础网络请求和提供渲染原生和自定义音频样式的组件

为了能让本工具能运行在 __javascript__ 的所有环境中以及使用 __node__ 的后端服务中正常使用，规范采用 __UMD__
前后端跨平台的解决方案

### 实现
1. 先判断是否支持Node.js模块格式（exports是否存在），存在则使用Node.js模块格式
2. 再判断是否支持AMD（define是否存在），存在则使用AMD方式加载模块
3. 前两个都不存在，则将模块公开到全局（window或global）

### 使用
作为TTS的中间件，支持接口自定义和请求数据的发送和响应数据的接收。

1. js
  - 文件引入
  - 调用 __GTTS.post__ 入参为当前的页面地址 __url__ 和 要语音的文本内容 __content__
  - 回调成功后 __GTTS.insertVoiceFileById('can', rd.returnObject, type)__ 
    - (rd === res.data, can为插入的元素id节点)
    - type指的是音频相对于容器的位置仅支持标准DOM接口, 比如 __insertBefore__ 等


### 约定
- 请求
  - 仅对入参非空进行校验
  - 不做超时处理
  - 异常捕获请用户自行操作
- 音频dom插入
  - 使用浏览器原生的 __audio__ 标签 仅保留 播放/暂停 时间显示 播放进度
    - mac chrome: Version 74.0.3729.169
    - mac Safari: Version 13.1.2 (15609.3.5.1.3)
    - mac Microsoft Edge Version 84.0.522.63 (Official build)
    - mac Firefox 81.0.2  会保留音量操作
  - 对同一个插入的节点仅渲染一次，目前不做容器和音频文件的缓存；如果想更新，请刷新页面，重新获取

#### 入参
1. config
  - __headers__
2. data
  - 当前页面地址 curUrl
  - 文本 content
3. 


### 相关参考
1. [umdjs/umd](https://github.com/umdjs/umd)


