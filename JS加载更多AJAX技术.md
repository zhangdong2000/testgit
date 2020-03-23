1、float属性：默认垂直分布，文字放在正中间：text-align：center;设置行高，是文字居中line-height:
	alert("内容");打印文字内容
2、需要给id是"show123"的div添加子元素（节点、标签）
	需要一次性给父div添加两个子元素，没格子元素里存储两张图片
3、如何使用JS创建页面元素（节点、标签）
	文档（表示当前的网页）
	元素（节点、标签）=document.createElement("标签名字（div）")
	function myAppend(){
		newDIV = document.createElement("div");
		newDIV.style.width="278px";
		newDIV.style.height="139px"; 
		//新建的div标签内部追加HTML代码;
		newDIV.innerHTML="<div style='float:left;width:139px;height:139px;'>"
			+"<img src="imgs/p5.jpg">"+
			"</div>"+"<div style='float:left;width:139px;height:139px;'>"
			+"<img src="imgs/p6.jpg">"+
			"</div>";
	}
	document.getElementById("").appendChild(newDIV);
4、对页面上的元素，进行HTML编写：
	元素（节点、标签）.innerHTML = "<div style='....'>....</div>";
	注意单双引号的使用
5、使用JS为当前的元素，追加子元素（节点，标签）
	父元素.appendChild(子元素);
6、【**】在JS中使用innerHTML = "书写的html代码要求标准,注意空格、空行、结束标签，结束符号等。。";
7、AJAX（异步交互技术）
	synchoornous
		asynchronous
						JavaScript and 		XML
			异步				JS		和	  可扩展的
		（1）最早的请求方式是form表单（提交数据），服务器会返回一个页面（整个页面发送给用户）
		（2）现在不需要服务器发送页面，只发回我们需要（更新）的数据即可。
8、示例：
	first.jsp  ---请求ValidServlet服务页面---->   second.jsp
	（1）first.jsp和second.jsp的区别非常小（页面大部分内容是一致的）
	（2）由于两个页面的内容非常相似，所以让服务器发送给用户第二页面浪费网络资源
9、使用ajax技术来优化
	once.jsp--- 请求AjaxServlet服务页面----once.jsp
	(1)页面整体不刷新
   （2）只有局部刷新
   <script>
		//使用js去请求servlet，而不是用jsp页面去请求servlet
		//利用XML去请求
		var req = new XMLHttpRequest();
		req.onreadystatechange = function(){
		if(req.readyState == 4){
			//服务器返回的信息（状态==4，服务器的信息已经完整发送回来）
			var returnData = req.responseText;
		}	
		//req.open(method,url,true(是否使用一步的方式交互))
		状态1：准备发送
		req.open("post","doAjax",true);
		状态2：发送(简单发送一个null);
		req.sned(null);
		};
		//添加监听程序，因为不知道什么时间发起请求
   </script>
   AjaxServlet中：
		System.out.print("这里是AjaxServlet。。。。");
		PrintWriter out = response.getWriter(); //响应获取流（流里存数据）
		out.print("return value 6666");
		out.flush();	//清空流
		out.close();
   请求的过程中有好多状态，4个步骤：
	（1）准备发送（设置各种参数）
			open
	（2）发送send
	（3）开始响应
	（4）响应完成
	监听，监听以上四个状态，（onreadystatechange）

10、异步交互的过程：
	var 请求 = new XMLHttpRequest();
	请求.onreadystatechange = function(){
		if(请求.readyState == 4){
			服务器返回的数据 = 请求.responseText;
		}
		
	}
	请求.open("post/get","请求的目标Servlet（URL）",true);
	请求.send(null);
   
   