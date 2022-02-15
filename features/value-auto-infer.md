# Value Auto-infer

由于Windi CSS只会生成你所使用的CSS工具，它使你能够在你的类中使用任意的值，并根据适当的语义生成相应的样式。

```html
<!-- sizes and positions -->
<div class="p-5px mt-[0.3px]"></div>

<!-- colors -->
<button class="bg-hex-b2a8bb"></button>
<button class="bg-[#b2a8bb]"></button>
<button class="bg-[hsl(211.7,81.9%,69.6%)]"></button>

<!-- grid template -->
<div class="grid-cols-[auto,1fr,30px]"></div>
```

当你想退出你的设计系统并对一些特定的组件进行一些细粒度的控制时，这很有用。支持直接的`p-5px`和显式转义的`p-[5px]`。

我们还提供了[可视化分析器](/features/analyzer)，让你对项目中所有的实用程序的使用情况有一个概览，并能轻松发现设计系统中不需要的值转义。

## Numbers

```less
p-{float} -> padding: {float/4}rem;
```

<InlinePlayground :input="'p-2.5\np-3.2'" :showCSS="true" :showPreview="false"/>

## Sizes

```less
// {size} should be end with rem|em|px|vh|vw|ch|ex
p-{size} -> padding: {size};
```

<InlinePlayground :input="'p-3px\np-4rem'" :showCSS="true" :showPreview="false"/>


## Fractions

```less
w-{fraction} -> width: {fraction -> percent};
```

<InlinePlayground :input="'w-9/12'" :showCSS="true" :showPreview="false"/>


## Colors

```css
text-{color} -> color: rgba(...);

border-hex-{hex} -> border-color: rgba(...);
```

<InlinePlayground 
  :input="'text-cyan-400\nborder-hex-6dd1c7'" 
  :showCSS="true" 
  :showPreview="false"
  fixed="border border-2 px-4 py-2 rounded"
/>

## Variables

你甚至可以传递变量名称，这在与CSS变量结合时非常有用.

```css
bg-${variableName}
```

<InlinePlayground 
  :input="'bg-$test-variable'" 
  :showCSS="true" 
  :showPreview="false"
/>

## Grid Templates

```css
grid-cols-[auto,1fr,30px]
```

<InlinePlayground 
  :input="'grid-cols-[auto,1fr,30px]'" 
  :showCSS="true" 
  :showPreview="false"
/>
