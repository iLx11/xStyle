下载

```cmd
pnpm add ilx1-x-style -D

#or

npm i ilx1-x-style --save-dev
```



`vite.config.ts` 中配置

```ts
css: {
    preprocessorOptions: {
      scss: {
        additionalData: '@use "ilx1-x-style/base/global.scss" as global;',
        api: 'modern', // 添加这一行以使用新的JS API
        silenceDeprecations: ['legacy-js-api'], // 可选：静默此特定警告
      },
    },
  },
```

