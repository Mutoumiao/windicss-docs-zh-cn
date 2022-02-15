# Shortcuts

当你在类似的工具集上工作时，重复是很常见的。我们提供了这个 "快捷方式" 的功能，允许你给实用程序的组合命名，你可以在你的应用程序中到处重复使用，而不需要重复自己.

只需在你的配置中添加`shortcuts`字段:

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

<InlinePlayground 
  :input="'btn btn-green'" 
  :config="{ shortcuts: {
    btn: 'py-2 px-4 font-semibold rounded-lg shadow-md',
    'btn-green': 'text-white bg-green-500 hover:bg-green-700',
  }}"
  :showCSS="true"
  :showMode="false"
  :showTabs="true"
  :showConfig="true"
  :enableConfig="true"
/>

CSS-in-JS语法也支持复杂的实用程序:

```js windi.config.js
export default {
  theme: {
    /* ... */
  },
  shortcuts: {
    'btn': {
      'color': 'white',
      '@apply': 'py-2 px-4 font-semibold rounded-lg',
      '&:hover': {
        '@apply': 'bg-green-700',
        'color': 'black',
      },
    },
    'btn-green': 'text-white bg-green-500 hover:bg-green-700',
  },
}
```

<InlinePlayground 
  :input="'btn btn-green'" 
  :config="{ shortcuts: {
    btn: {
      color: 'white',
      '@apply': 'py-2 px-4 font-semibold rounded-lg',
      '&:hover': {
        '@apply': 'bg-green-700',
        color: 'black',
      },
    },
    'btn-green': 'text-white bg-green-500 hover:bg-green-700',
  }}"
  :showCSS="false"
  :showMode="false"
  :showTabs="true"
  :showConfig="true"
  :enableConfig="true"
/>

该配置添加的实用程序也可以直接包装成变体，如`sm:btn`。这个功能的目的类似于`@apply`指令，它将把所有的实用工具合并成一个样式.
