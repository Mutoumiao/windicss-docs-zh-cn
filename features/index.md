[windi css]: https://github.com/windicss/windicss
[tailwind css]: https://tailwindcss.com/docs
[svelte]: /guide/svelte.html#additional-features-in-svelte-⚡%EF%B8%8F

# Features

[Windi CSS] 与 [Tailwind CSS] v2完全兼容。在此基础上，我们还有许多额外的功能，进一步提升你的工作流程，并开辟更多的可能性。

## Value Auto-infer

在你的类中使用任意的值并生成相应的样式.

```html
<!-- sizes and positions -->
<div class="p-5px mt-[0.3px]"></div>

<!-- colors -->
<button class="bg-hex-b2a8bb"></button>
<button class="bg-[hsl(211.7,81.9%,69.6%)]"></button>

<!-- grid template -->
<div class="grid-cols-[auto,1fr,30px]"></div>
```

<LearnMore to="/features/value-auto-infer" />

## Variant Groups

通过用圆括号分组，将实用程序应用于同一变体。.

```html
<div class="bg-white dark:hover:(bg-gray-800 font-medium text-white)"/>
```

```html
<div class="bg-white dark:hover:bg-gray-800 dark:hover:font-medium dark:hover:text-white"/>
```

<LearnMore to="/features/variant-groups" />

## 响应式设计

扩展的响应式断点控制.

```html
<div class="p-1 md:p-2 <lg:p-3"></div>
```

<LearnMore to="/features/responsive-design" />

## Important Prefix

在任何实用类前加上`!`，将其设置为`!important`。

```html
<div class="text-red-400 !text-green-300">Green</div>
```

<LearnMore to="/features/important-prefix" />

## 快捷方式

快速组合实用程序以创建可重复使用的组件.

```js windi.config.js
export default {
  theme: {
    /* ... */
  },
  shortcuts: {
    'btn': 'py-2 px-4 font-semibold rounded-lg shadow-md',
    'btn-green': 'text-white bg-green-500 hover:bg-green-700',
  },
}
```

```html
<div class="btn hover:btn-green"></div>
```

<LearnMore to="/features/shortcuts" />

## Dark Mode

```html
<div class="text-black dark:text-white"></div>
```

<LearnMore to="/features/dark-mode" />

## RTL

```html
<div class="text-green-400 rtl:(text-red-400 text-right)"></div>
```

<LearnMore to="/features/rtl" />

## Directives

完全支持类似于Tailwind的`@apply`、`@screen`指令。

```css
.btn {
  @apply font-bold py-2 px-4 rounded;
}
.btn-blue {
  @apply bg-blue-500 hover:bg-blue-700 text-white;
  padding-top: 1rem;
}
```

<LearnMore to="/features/directives" />

## Visual Analyzer

We provided a visual analyzer for you to have an overview of your utility usage and design system.

<LearnMore to="/features/analyzer" />
