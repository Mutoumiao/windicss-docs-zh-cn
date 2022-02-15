# Dark Mode

WindiCSS有开箱即用的黑暗模式支持。

通过给实用程序加上`dark:`的前缀，它们将只在黑暗模式启用时适用。在下面的例子中，`Preview`文本在浅色模式下是红色的，在深色模式下是绿色的。试着玩一下吧。

<ToggleDark />

<InlinePlayground :input="'text-red-400 dark:text-green-400'" :showCSS="true" :showPreview="true"/>

我们有两种启用黑暗模式的模式，[class mode](#class-mode)和[media query mode](#media-query-mode) 。默认情况下，`class`模式被启用。

## Class mode

class模式让你更好地控制黑暗模式的启用时间。

```js windi.config.js
export default {
  darkMode: 'class',
  // ...
}
```

它检测父元素的`class="dark"`，通常你可以在`html`元素上应用它，使其在全局上发挥作用。

```html
<html>
<body>
  <!-- Dark mode disabled -->
</body>
</html>

<html class="dark">
<body>
  <!-- Dark mode enabled -->
</body>
</html>
```

你可以使用下面的片段来使颜色方案与用户的系统偏好相匹配，或者编写你自己的逻辑来管理它。

```js
if (window.matchMedia('(prefers-color-scheme: dark)').matches)
  document.documentElement.classList.add('dark')
else
  document.documentElement.classList.add('light')
```

<InlinePlayground 
  :input="'text-white dark:text-white'" 
  :config="{ darkMode: 'class' }"
  :showCSS="true"
  :showPreview="false"
  :showMode="false"
  :showTabs="false"
  :showConfig="true"
  :enableConfig="true"
/>

## Media query mode 

在媒体查询模式下，它使用浏览器内置的`@media (prefers-color-scheme: dark)`查询，总是与用户的系统偏好相匹配。

```js windi.config.js
export default {
  darkMode: 'media',
  // ...
}
```

<InlinePlayground 
  :input="'text-white dark:text-white'" 
  :config="{ darkMode: 'media' }"
  :showCSS="true"
  :showPreview="false"
  :showMode="false"
  :showTabs="false"
  :showConfig="true"
  :enableConfig="true"
/>

