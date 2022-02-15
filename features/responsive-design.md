# Responsive Design

Doing [Responsive Design](https://en.wikipedia.org/wiki/Responsive_web_design) in Windi CSS is effortless. By simply adding variant prefixes like `md:` or `lg:` to the utility you want to use, the corresponding media query will be generated automatically. Try it yourself using the playground below:

在WindiCSS中做[响应式设计](https://en.wikipedia.org/wiki/Responsive_web_design)是毫不费力的。只需在你要使用的工具上添加变量前缀，如`md:`或`lg:`，相应的媒体查询就会自动生成。自己用下面的playground试试吧。

<InlinePlayground :input="'p-1 lg:p-2'" :showCSS="true" :showPreview="false"/>

当你想把一个断点变体应用于多个工具时，在WindiCSS中，你可以通过使用[Variant Groups](/features/variant-groups.html)功能来实现，而不需要重复操作。

<InlinePlayground :input="'p-1 lg:(p-2 m-2 text-red-400)'" :showCSS="true" :showPreview="false"/>

## Custom Range

默认情况下，WindiCSS的断点被设计为移动优先。

这意味着非前缀的工具（如`p-1`）对所有的屏幕尺寸都有效，而前缀的工具（如`md:p-2`）只在**指定的断点及以上的地方生效。

我们还提供了通过添加`<`和`@`前缀对查询范围进行更多控制的能力。

```bash
lg  => greater or equal than this breakpoint
<lg => smaller than this breakpoint
@lg => exactly this breakpoint range
```

<InlinePlayground :input="'lg:p-1\n<lg:p-2\n@lg:p-3'" :showCSS="true" :showPreview="false"/>

## Breakpoints

|  | Default | `<` prefixed | `@` prefixed |
| :------ | :--- | :--- | :--- |
| sm | (min-width: 640px) | (max-width: 639.9px) | (min-width: 640px) and <br>(max-width: 767.9px) |
| md | (min-width: 768px) | (max-width: 767.9px) | (min-width: 768px) and <br>(max-width: 1023.9px) |
| lg | (min-width: 1024px) | (max-width: 1023.9px) | (min-width: 1024px) and <br>(max-width: 1279.9px) |
| xl | (min-width: 1280px) | (max-width: 1279.9px) | (min-width: 1280px) and <br>(max-width: 1535.9px) |
| 2xl | (min-width: 1536px) | (max-width: 1535.9px) | (min-width: 1536px) |

## Customization

你可以在你的`windi.config.js`中自定义你的中断点。

```ts windi.config.js
import { defineConfig } from 'windicss/helpers'

export default defineConfig({
  theme: {
    screens: {
      tablet: '640px',
      laptop: '1024px',
      desktop: '1280px',
    },
  },
})
```
