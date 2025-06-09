# taro-with-tdesign-miniprogram
注意：taro + 原生第三方组件库进行开发的项目，不再具有多端转换的能力。

taro + webpack + tdeisgn-miniprogram 示例


##  taro4 + vite，报错：无法找到 usingComponents 中的组件
taro4 + vite 编译到小程序阶段问题较多，未深入探索.
repo： https://github.com/NervJS/taro/issues/16226

## taro + webpack，可以正常引入 tdesign-miniprogram

### 关键改动点：

```bash
# 引入 tdesign-miniprogram UI 组件库
npm i tdesign-miniprogram
# or
yarn add  tdesign-miniprogram
```

```js
// config/index.ts 配置别名
alias: {
	"@/tdesign": path.resolve(
	__dirname,
	"../node_modules/tdesign-miniprogram/miniprogram_dist"
	),
},
```

```js
// src/pages/index/index.config.ts 页面配置文件
export default definePageConfig({
  navigationBarTitleText: "首页",
  usingComponents: {
    "t-button": "@/tdesign/button/button",
  },
});
```

```html
<!-- src/pages/index/index.tsx 页面文件 -->
<t-button theme="primary">显示日历</t-button>
```

### 效果
<img width="1240" src="https://github.com/user-attachments/assets/5c81fff6-6c98-4273-b5ef-a1e1de2c8fa8" />
