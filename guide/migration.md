[auto]: /features/value-auto-infer
[design]: /posts/story

# 从Tailwind CSS迁移

## Packages 

你的一些依赖性不再需要了。你可以从你的`package.json`中删除它们，如果它们只是Tailwind CSS需要的话。

```diff package.json
- "tailwindcss": "*",
- "postcss": "*",
- "autoprefixer": "*",
+ "windicss": "*"
```

## Base Styles

你现在可以从你的CSS文件中删除Tailwind的CSS导入。

```diff
- @import 'tailwindcss/base';
- @import 'tailwindcss/components';
- @import 'tailwindcss/utilities';
```

(可选）根据你所使用的集成工具，你可能需要明确导入`virtual:windi.css`条目。请查看工具的文档以了解更多细节。

```js main.js
import 'virtual:windi.css'
```

## Configurations

由于所有的变体都是[自动启用][auto]，所以不再需要`variant`和`purge`字段。

`colors`和`plugins`需要从`windicss`导入。

我们与`windi.config.js`和`tailwind.config.js`都兼容。

```diff windi.config.js
-const colors = require('tailwindcss/colors')
+const colors = require('windicss/colors')
-const typography = require('@tailwindcss/typography')
+const typography = require('windicss/plugin/typography')

export default {
- purge: {
-   content: [
-     './**/*.html',
-   ],
-   options: {
-     safelist: ['prose', 'prose-sm', 'm-auto'],
-   },
- },
- variants: {
-   extend: {
-     cursor: ['disabled'],
-   }
- },
+ extract: {
+   include: ['./**/*.html'],
+ },
+ safelist: ['prose', 'prose-sm', 'm-auto'],
  darkMode: 'class',
  plugins: [typography],
  theme: {
    extend: {
      colors: {
        teal: colors.teal,
      },
    }
  },
}
```

## Cleanup (optional)

如果你不使用它们的其他功能，以下文件可以被删除。

```diff
- postcss.config.js
```
