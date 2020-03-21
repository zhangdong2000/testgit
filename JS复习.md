<div>标签是默认垂直分布的；若是水平分布，可以使用float:left/right使得水平分布，div使用float属性后，
	会变成内容。若改变的话，则使用一个大的div标签包裹float属性的div
div重叠：position：absolute（绝对的），relative（绝对的）
1、JS:JavaScript 脚本语言（样式、数据的动态的）
		基于对像，面向原型的语言
		【解释】 基于对象：js语言中有类和对象的概念，不允许用户自己定义类
		js预先定义好了一些类，这些类是可以使用的。
		【**】js预先定义好的这些类的总和，就叫原型。
2、【**】开发应用：IE,谷歌，火狐
3、JS处理谁？
	处理页面的(HTML页面、JSP页面)
	（1）整个HTML页面（JSP页面）=== document（文档）
	（2）在HTML页面上存在的代码 === 标签和文本 === element（元素）/node（节点）/tag（标签）
		element === node === tag
4、JS 在页面上的书写位置：
	书写在<head>标签中
	<head>
		<script>
		function 函数名(){
			内容
		}
		</script>
	</head>
5、JS 用什么方式区分页面元素
	（1）id（identityCard）唯一标识
			可以再document（文档中）根据id（唯一标识）来获取一个元素（==节点，标签）
	 (2)元素（节点/标签）=document.getElementById("具体的id")
		元素（节点/标签）。style（样式）。属性（width，height、。。。）="要改变到的值"
	 (3)display(显示)属性：
		 block 显示
		 none 不显示
	（4）触发事件：
			【1】onclick  当点击的时候
			【2】ondbclick  当双击的时候
			【3】onmouseover 当鼠标进入范围的时候
			【4】onmouseout 当鼠标离开范围的时候
			【5】onmousedown 当鼠标按下是触发此事件
			【6】onmouseup 当鼠标按下后松开鼠标时触发此事件
			【7】onmousemove 当鼠标移动时触发此事件
			【8】onkeydown 当键盘上额的某个键被按下并且释放时触发此事件
			【9】onkeydown 当键盘上某个键被按下时触发此事件
			【10】onkeyup 当键盘上某个按键被按放时触发此事件
			
6、JS 是弱类型的语言（不需要指定变量的类型）
	myElement.style.width="300px";
	【**】要改变的内容要用双引号括起来
	【**】这个元素.样式.背景色="想要改变的值"
	