# xStyle

一个轻量级的 SCSS 工具库，提供丰富的 mixin 和 function 接口，帮助开发者快速构建美观的界面。

## 安装

```cmd
pnpm add ilx1-x-style -D

# 或

npm i ilx1-x-style --save-dev
```

## 配置

在 `vite.config.ts` 中配置：

```ts
css: {
    preprocessorOptions: {
      scss: {
        additionalData: '@use "ilx1-x-style/base/global.scss" as global;',
        api: 'modern', // 使用新的JS API
        silenceDeprecations: ['legacy-js-api'], // 可选：静默此特定警告
      },
    },
  },
```

## 接口文档

### Global Mixins (global.scss)

#### custom-scrollbar
自定义滚动条样式（全浏览器兼容）
- **参数**:
  - `$show`: Boolean - 是否显示滚动条，默认 true
  - `$width`: Length - 滚动条宽度，默认 10px
  - `$track-color`: Color - 轨道颜色，默认 rgba(51, 51, 51, 0.3)
  - `$thumb-color`: Color - 滑块颜色，默认 rgba(51, 51, 51, 0.5)
  - `$thumb-hover-color`: Color - 滑块 hover 颜色，默认 rgba(173, 173, 173, 0.8)
  - `$border-radius`: Length - 圆角，默认 12px

#### comm-box
通用容器样式
- **参数**: 无

#### wh
宽高设置
- **参数**:
  - `$width`: Length - 宽度，默认 100%
  - `$height`: Length - 高度，默认 auto
  - `$max-width`: Length - 最大宽度，默认 none
  - `$max-height`: Length - 最大高度，默认 none
  - `$min-width`: Length - 最小宽度，默认 none
  - `$min-height`: Length - 最小高度，默认 none

#### full-wh
100% 宽高设置
- **参数**: 无

#### grid-config
Grid 布局配置
- **参数**:
  - `$col`: List/Value - 列配置，默认 auto
  - `$rows`: List/Value - 行配置，默认 auto
  - `$gap`: Length - 间距，默认 0px
  - `$place-content`: Value - 内容对齐方式，默认 normal
  - `$place-items`: Value - 项目对齐方式，默认 normal

#### flex-config
Flex 布局配置
- **参数**:
  - `$isrow`: Number - 是否为列布局（0: 行, 1: 列），默认 0
  - `$layout`: Value - 主轴对齐方式，默认 space-between
  - `$gap`: Length - 间距，默认 0px
  - `$wrap`: Value - 是否换行，默认 nowrap

#### font-config
字体配置
- **参数**:
  - `$size`: Length - 字体大小，默认 $font-size-base
  - `$color`: Color - 字体颜色，默认 $color-base
  - `$weight`: Number - 字体粗细，默认 $font-weight-regular
  - `$line-height`: Number - 行高，默认 1.5
  - `$align`: Value - 文本对齐方式，默认 left

#### text-truncate
文本截断（单行/多行）
- **参数**:
  - `$lines`: Number - 行数，默认 1（单行）

#### pos-ab
绝对定位
- **参数**:
  - `$data1`: Length - 第一个定位值，默认 0px
  - `$data2`: Length - 第二个定位值，默认 0px
  - `$reverse`: Number - 定位方向（0: top/left, 1: top/right, 2: bottom/right, 3: bottom/left），默认 0
  - `$pos`: Value - 定位类型，默认 absolute

#### fixed-center
固定中心定位
- **参数**: 无

#### ab-center
绝对中心定位
- **参数**: 无

#### flex-center
Flex 中心定位
- **参数**: 无

#### style-common
通用样式配置
- **参数**:
  - `$radius`: Length - 圆角，默认 12px
  - `$bg`: Color - 背景色，默认 null
  - `$border`: Value - 边框，默认 null
  - `$bs`: Value - 阴影，默认 null

#### app-common
应用通用样式重置
- **参数**: 无

### Effect Functions (effect.scss)

#### angle-inner-curve
角内凹曲线
- **参数**:
  - `$radius`: Length - 主曲线半径，默认 10px
  - `$cropRadius`: Length - 裁剪区域半径，默认 10px
  - `$pos`: Number/List - 需应用效果的角落编号，默认 0（0-3，可传入列表）
- **返回值**: List - 渐变背景列表

#### plane-inner-curve
平面内凹曲线
- **参数**:
  - `$radius`: Length - 主曲线半径，默认 20px
  - `$cropRadius`: Length - 裁剪区域半径，默认 40px
  - `$position`: Percentage - 曲线在边缘的位置（0%-100%），默认 50%
  - `$depth`: Angle - 立体深度角度（0-90度），默认 30deg
  - `$corners`: Number/List - 需应用效果的角落编号（0-3，可传入列表），默认 0
- **返回值**: List - 渐变背景列表

## 使用示例

```scss
// 导入
@use "ilx1-x-style/base/global.scss" as global;
@use "ilx1-x-style/base/effect.scss" as effect;

// 使用 mixin
.container {
  @include global.flex-center();
  @include global.custom-scrollbar();
  @include global.style-common(
    $radius: 16px,
    $bg: #f5f5f5,
    $border: 1px solid #e0e0e0
  );
}

// 使用 function
.custom-shape {
  background: effect.plane-inner-curve(
    $radius: 30px,
    $cropRadius: 60px,
    $position: 70%,
    $depth: 45deg,
    $corners: (0, 2)
  );
}