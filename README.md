Typescript Webpack Alias to Local Dir as Package Demo
================================================

There are 2 dirs in this project, `app` will use `~common` as local package.

Develop `~common`:

```
cd ~common
npm install
```

Develop `app`:

```
cd app
npm install
npm run demo
```

在其它的demo中，我已经验证了使用`npm install ../~common`或者`npm link ../~common`这些方式，
与webpack和ts-loader配合使用时有些问题，虽然可以勉强解决，但是很不完美。

在这个demo中，不再把`~common`加入到`app`的dependencies中，而是利用typescript和webpack的alias功能，
直接引用的同时，让import的url看起来不那么长。

1. `tsconfig.json`中
    ```
    "baseUrl": ".",
      "paths": {
        "~common": [
          "../~common"
        ]
    }
    ```
    
2. `webpack.config.ts`中：
   ```
   alias: {
     "~common": "../~common"
   }
   ```
   
3. 代码中引用：`import {hello} from '~common/hello'`