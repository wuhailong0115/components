# 弹框组件，可拖拽

# 使用方法
import {lxDialog} from 'lxDialog'
components: {lxDialog}

# 参数
# 显示隐藏： isShow  {Boolean}
# 位置： 	left, right, top, width   {String}
# 标题： 	title  {String}

# 组件引用
<lxDialog top="10px" left="10px" v-model="isShow" :title="msg">
	<div>内容...</div>
</lxDialog>
