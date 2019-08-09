# 文字滚动  （上下）

# 使用方法
import {lxMessage} from 'lxMessage'
components: {lxMessage}

# 参数
# 高度： 	height 	  {String}   开启动画条件
# 滚动方向： direction {String}   'top','bottom'  默认 bottom
# 动画速度： step   	  {Number}   默认 1.2
# 动画时间： time   	  {Number}   默认 38

# 组件引用
<lxMessage height="150" >
	<div slot="message1">内容...</div>
	<div slot="message2">内容...</div>
</lxMessage>
