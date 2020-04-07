<p align="center"><img src="http://oduvanstudio.com/vdr.gif" alt="logo"></p>
<h1 align="center">Vue-drag-resize</h1>

[![Latest Version on NPM](https://img.shields.io/npm/v/vue-drag-resize.svg?style=flat-square)](https://npmjs.com/package/vue-drag-resize)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)
[![npm](https://img.shields.io/npm/dt/vue-drag-resize.svg?style=flat-square)](https://www.npmjs.com/package/vue-drag-resize)

> Vue Component for draggable and resizable elements.

## 目录

* [特性](#特性)
* [安装和基本用法](#安装和基本用法)
  * [属性](#属性)
  * [事件](#事件)
* [贡献](#贡献)
* [许可](#许可)

### Demo

[Demo](http://kirillmurashov.com/vue-drag-resize)

### 特性

* 轻巧，无依赖
* 所有道具都是反应性的
* 支持触摸事件
* 结合使用可拖动，可调整大小或同时使用
* 定义棒以调整大小
* 为可调整大小的组件保存长宽比
* 限制大小和移动到父元素
* 限制拖动到垂直或水平轴

## 安装和基本用法

```bash
$ npm i -s vue-drag-resize
```


注册组件：

```js
import Vue from 'vue'
import VueDragResize from 'vue-drag-resize'

Vue.component('vue-drag-resize', VueDragResize)
```

使用组件：

```vue
<template>
    <div id="app">
        <VueDragResize :isActive="true" :w="200" :h="200" v-on:resizing="resize" v-on:dragging="resize">
            <h3>Hello World!</h3>
            <p>{{ top }} х {{ left }} </p>
            <p>{{ width }} х {{ height }}</p>
        </VueDragResize>
    </div>
</template>

<script>
    import VueDragResize from 'vue-drag-resize';

    export default {
        name: 'app',

        components: {
            VueDragResize
        },

        data() {
            return {
                width: 0,
                height: 0,
                top: 0,
                left: 0
            }
        },

        methods: {
            resize(newRect) {
                this.width = newRect.width;
                this.height = newRect.height;
                this.top = newRect.top;
                this.left = newRect.left;
            }
        }
    }
</script>
```

### 属性

#### isActive
Type: `Boolean`<br>
Required: `false`<br>
Default: `false`

确定组件是否应处于活动状态.

```html
<vue-drag-resize :isActive="true">
```

#### preventActiveBehavior
Type: `Boolean`<br>
Required: `false`<br>
Default: `false`

通过单击组件并在组件区域之外单击来禁用组件的行为（isActive：true / false）。如果启用了prop，则组件仅针对指定的对象.

```html
<vue-drag-resize :preventActiveBehavior="true">
```

#### parentW
Type: `Number`<br>
Required: `false`<br>
Default: `0`

定义父元素的初始宽度。如果未指定，则会自动计算。使用此参数，可以设置组件的边界区域，并且在实时调整大小时也会使用它.

```html
<vue-drag-resize :parentW="2000">
```

#### parentH
Type: `Number`<br>
Required: `false`<br>
Default: `0`

定义父元素的初始高度。如果未指定，则会自动计算。使用此参数，可以设置组件的边界区域，并且在实时调整大小时也会使用它.

```html
<vue-drag-resize :parentH="2000">
```

#### parentScaleX
Type: `Number`<br>
Required: `false`<br>
Default: `1`

定义初始水平比例尺或父元素。父级转换中的值相同：scale（）CSS定义。拖动/调整大小和操纵杆的大小将使用此值进行计算.

```html
<vue-drag-resize :parentScaleX="0.5">
```

#### parentScaleY
Type: `Number`<br>
Required: `false`<br>
Default: `1`

定义初始垂直比例或父元素。父级转换中的值相同：scale（）CSS定义。拖动/调整大小和操纵杆的大小将使用此值进行计算.

```html
<vue-drag-resize :parentScaleY="0.5">
```

#### isDraggable
Type: `Boolean`<br>
Required: `false`<br>
Default: `true`

确定组件是否应拖动.

```html
<vue-drag-resize :isDraggable="false">
```

#### isResizable
Type: `Boolean`<br>
Required: `false`<br>
Default: `true`

确定组件是否应调整大小.

```html
<vue-drag-resize :isResizable="false">
```

#### parentLimitation
Type: `Boolean`<br>
Required: `false`<br>
Default: `false`

Limits the scope of the component's change to its parent size.

```html
<vue-drag-resize :parentLimitation="true">
```

#### snapToGrid
Type: `Boolean`<br>
Required: `false`<br>
Default: `false`

Determines whether the component should move and resize in predefined steps.

```html
<vue-drag-resize :snapToGrid="true">
```

#### gridX
Type: `Number`<br>
Required: `false`<br>
Default: `50`

Define the grid step size for the horizontal axis. Both sides of the component (left and right) will snap to this step.

```html
<vue-drag-resize :snapToGrid="true" :gridX="20">
```

#### gridY
Type: `Number`<br>
Required: `false`<br>
Default: `50`

Define the grid step size for the vertical axis. Both sides of the component (top and bottom) will snap to this step.

```html
<vue-drag-resize :snapToGrid="true" :gridY="20">
```

#### aspectRatio
Type: `Boolean`<br>
Required: `false`<br>
Default: `false`

Determines whether the component should retain its proportions.

```html
<vue-drag-resize :aspectRatio="false">
```

#### w
Type: `Number`<br>
Required: `false`<br>
Default: `200`

Define the initial width of the component.

```html
<vue-drag-resize :w="200">
```

#### h
Type: `Number`<br>
Required: `false`<br>
Default: `200`

Define the initial height of the component.

```html
<vue-drag-resize :h="200">
```

#### minw
Type: `Number`<br>
Required: `false`<br>
Default: `50`

Define the minimal width of the component.

```html
<vue-drag-resize :minw="50">
```

#### minh
Type: `Number`<br>
Required: `false`<br>
Default: `50`

Define the minimal height of the component.

```html
<vue-drag-resize :minh="50">
```

#### x
Type: `Number`<br>
Required: `false`<br>
Default: `0`

Define the initial x position of the component.

```html
<vue-drag-resize :x="0">
```

#### y
Type: `Number`<br>
Required: `false`<br>
Default: `0`

Define the initial y position of the component.

```html
<vue-drag-resize :y="0">
```

#### z
Type: `Number|String`<br>
Required: `false`<br>
Default: `auto`

Define the zIndex of the component.

```html
<vue-drag-resize :z="999">
```

#### sticks
Type: `Array`<br>
Required: `false`<br>
Default: `['tl', 'tm', 'tr', 'mr', 'br', 'bm', 'bl', 'ml']`

Define the array of handles to restrict the element resizing:
* `tl` - Top left
* `tm` - Top middle
* `tr` - Top right
* `mr` - Middle right
* `br` - Bottom right
* `bm` - Bottom middle
* `bl` - Bottom left
* `ml` - Middle left

```html
<vue-drag-resize :sticks="['tm','bm','ml','mr']">
```

#### axis
Type: `String`<br>
Required: `false`<br>
Default: `both`

Define the axis on which the element is draggable. Available values are `x`, `y`, `both` or `none`.

```html
<vue-drag-resize axis="x">
```

#### dragHandle
Type: `String`<br>
Required: `false`

Defines the selector that should be used to drag the component.

```html
<vue-drag-resize dragHandle=".drag">
```

#### dragCancel
Type: `String`<br>
Required: `false`

Defines a selector that should be used to prevent drag initialization.

```html
<vue-drag-resize dragCancel=".drag">
```





---

### 事件

#### clicked

Required: `false`<br>
Parameters: `Original event handler`

Called whenever the component gets clicked.

```html
<vue-drag-resize @clicked="onActivated">
```

#### activated

Required: `false`<br>
Parameters: `-`

Called whenever the component gets clicked, in order to show handles.

```html
<vue-drag-resize @activated="onActivated">
```

#### deactivated

Required: `false`<br>
Parameters: `-`

Called whenever the user clicks anywhere outside the component, in order to deactivate it.

```html
<vue-drag-resize @deactivated="onDeactivated">
```

#### resizing

Required: `false`<br>
Parameters: `object`
```javascript
{
    left: Number, //the X position of the component
    top: Number, //the Y position of the component
    width: Number, //the width of the component
    height: Number //the height of the component
}
```

Called whenever the component gets resized.

```html
<vue-drag-resize @resizing="onResizing">
```

#### resizestop

Required: `false`<br>
Parameters: `object`
```javascript
{
    left: Number, //the X position of the component
    top: Number, //the Y position of the component
    width: Number, //the width of the component
    height: Number //the height of the component
}
```

Called whenever the component stops getting resized.

```html
<vue-drag-resize @resizestop="onResizstop">
```

#### dragging

Required: `false`<br>
Parameters: `object`
```javascript
{
    left: Number, //the X position of the component
    top: Number, //the Y position of the component
    width: Number, //the width of the component
    height: Number //the height of the component
}
```

Called whenever the component gets dragged.

```html
<vue-drag-resize @dragging="onDragging">
```

#### dragstop

Required: `false`<br>
Parameters: `object`
```javascript
{
    left: Number, //the X position of the component
    top: Number, //the Y position of the component
    width: Number, //the width of the component
    height: Number //the height of the component
}
```


Called whenever the component stops getting dragged.

```html
<vue-drag-resize @dragstop="onDragstop">
```

## 贡献

Any contribution to the code or any part of the documentation and any idea and/or suggestion are very welcome.

``` bash
# serve with hot reload at localhost:8081
npm run start

# distribution build
npm run build

```

## 许可

[MIT license](LICENSE)
