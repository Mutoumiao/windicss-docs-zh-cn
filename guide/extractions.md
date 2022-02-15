# Extractions

Windi CSS依靠对你的源文件的**静态扫描和提取**来找到你的实用程序的使用，并按需生成相应的CSS。与[Tailwind's Purge limitation](https://tailwindcss.com/docs/optimizing-for-production#writing-purgeable-html)类似，你需要使用实用程序的静态全名，以便Windi CSS能够正确地检测它们。比如说,

字符串串联不能被静态提取:

```html
<div class="text-${ active ? 'green' : 'orange' }-400"></div>
```

使用实用程序的全名，而不是:

```html
<div class="${ active ? 'text-green-400' : 'text-orange-400' }"></div>
```

## 安全名单

有时你不得不使用动态连接法:

```html
<div class="p-${size}"></div>
```

为此，你将需要在`windi.config.js`的`safelist`选项中指定可能的组合。.

```ts windi.config.js
import { defineConfig } from 'windicss/helpers'

export default defineConfig({
  safelist: 'p-1 p-2 p-3 p-4',
})
```

或者更灵活一些:

```ts windi.config.js
import { defineConfig } from 'windicss/helpers'

function range(size, startAt = 1) {
  return Array.from(Array(size).keys()).map(i => i + startAt)
}

export default defineConfig({
  safelist: [
    range(3).map(i => `p-${i}`), // p-1 to p-3
    range(10).map(i => `mt-${i}`), // mt-1 to mt-10
  ],
})
```

## 扫描

当dev-server/build过程开始时，Windi CSS将扫描你的源代码并提取实用程序。

默认情况下，它将扫描`src/`下的文件，扩展名为`vue, html, mdx, pug, jsx, tsx`。

If you want to enable/disable scanning for other file-types or locations, you can configure it using `include` and `exclude` options:

如果你想 启用/禁用 对其他文件类型或位置的扫描，你可以使用 `include`和 `exclude` 选项进行配置。

```ts windi.config.js
import { defineConfig } from 'windicss/helpers'

export default defineConfig({
  extract: {
    // accepts globs and file paths relative to project root
    include: [
      'index.html',
      'src/**/*.{vue,html,jsx,tsx}',
    ],
    exclude: [
      'node_modules/**/*',
      '.git/**/*',
    ],
  },
})
```

### Preflight

预检（样式重设）也是在扫描时按需启用的。

你可以在配置中完全禁用它。

```ts windi.config.js
import { defineConfig } from 'windicss/helpers'

export default defineConfig({
  preflight: false,
})
```

或者通过安全列表明确地启用它。

```ts windi.config.js
import { defineConfig } from 'windicss/helpers'

export default defineConfig({
  preflight: {
    safelist: 'h1 h2 h3 p img',
  },
})
```

