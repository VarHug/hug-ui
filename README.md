# hug-ui

some personal components
version: 开发版0.1

## 组件说明
<h3>card-flip(旋转卡片)</h3>
<h4>Props</h4>
<table>
  <thead>
    <tr>
      <td>参数</td>
      <td>说明</td>
      <td>类型</td>
      <td>可选值</td>
      <td>默认值</td>
    <tr>
  </thead>
  <tbody>
    <tr>
      <td>width</td>
      <td>卡片容器的宽度</td>
      <td>Number/String</td>
      <td>-</td>
      <td>0</td>
    <tr>
    <tr>
      <td>height</td>
      <td>卡片容器的高度</td>
      <td>Number/String</td>
      <td>-</td>
      <td>0</td>
    <tr>
    <tr>
      <td>speed</td>
      <td>卡片旋转的速度</td>
      <td>Number/String</td>
      <td>-</td>
      <td>1</td>
    <tr>
    <tr>
      <td>axis</td>
      <td>卡片旋转的轴</td>
      <td>String</td>
      <td>centerX/centerY/top/right/bottom/left</td>
      <td>centerX</td>
    <tr>
  </tbody>
</table>
<p>请确保内容区域宽度/高度(width/height)<font color="red">小于等于</font>卡片容器的宽度/高度(widht/height)<p>

<h4>Slot</h4>
<table>
  <thead>
    <tr>
      <td>名字</td>
      <td>说明</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>front</td>
      <td>卡片区域正面的内容</td>
    </tr>
    <tr>
      <td>back</td>
      <td>卡片区域反面的内容</td>
    </tr>
  </tbody>
</table>

<h3>carousel(3D旋转木马走马灯)</h3>
<h4>Props</h4>
<table>
  <thead>
    <tr>
      <td>参数</td>
      <td>说明</td>
      <td>类型</td>
      <td>可选值</td>
      <td>默认值</td>
      <td>示例</td>
    <tr>
  </thead>
  <tbody>
    <tr>
      <td>width</td>
      <td>图片要设置的宽度</td>
      <td>Number/String</td>
      <td>-</td>
      <td>-</td>
      <td>-</td>
    </tr>
    <tr>
      <td>height</td>
      <td>图片要设置的高度</td>
      <td>Number/String</td>
      <td>-</td>
      <td>-</td>
      <td>-</td>
    </tr>
    <tr>
      <td>height</td>
      <td>传入carousel的数据，数组的长度决定了走马灯图片的总数，建议传入6-9张。每个数组的元素为一个对象。</td>
      <td>Array</td>
      <td>-</td>
      <td>-</td>
      <td>[{link:'',image:path}]</td>
    </tr>
  </tbody>
</table>
<p>图片要设置的宽度与高度<font color="red">并不等于</font>元素在浏览器中实际的宽度与高度<p>


## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
