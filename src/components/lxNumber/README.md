## 数字动画

### 使用方法
```
import {lxNumber} from 'lxNumber'
components: {lxNumber}
```

### 参数
### data {Number}  数字
### speed {Number} 数字动画播放速度 默认 700
### fontStyle {Object}  字体样式  默认 {color:'#ffcd36', fontSize:'20px'}

### 组件引用
`<lxNumber :data='number' :speed='speeds' :fontStyle='fontStyle'></lxDialog>`

## 赋值
 ```
 setTimeout(()=> {
 this.num = 1234
}, 1200)
 ```
