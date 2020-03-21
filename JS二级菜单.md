1、	ol == order list
	ul == unorder list
	li == list item
2、onmouseover触发事件，单鼠标进入1级菜单，显示二级菜单所在div
	onmouseout触发事件，单鼠标离开1级菜单，隐藏了二级菜单
	【思想】延迟关闭
		（1）当离开一级菜单，执行（延迟）【隐藏2级菜单】的操作==任务
		（2）如果鼠标在延迟时间内，刚好计入了2级菜单，则撤销操作==任务
			var myTask001;
			function showSM123(){
				keepShowSM789();
			}
			function hideSM456(){
				document.getElementById("smId123").style.display="none";
			}
			//延迟执行一个(隐藏)任务
			function lazyHide666(){
				myTask001 = window.setTimeout(hideSM456,1000);
			}
			function keepShowSM789(){
				window.clearTimeout(myTask001);
			}
			
			如何设置一个超时（延迟执行）任务
				任务1 = window.setTimeout(执行什么,多久之后执行 = 单位毫秒);
			如何撤销一个延迟执行任务
				window.clearTimeout(任务1);
3、
		鼠标进入男装		【立刻】显示2级菜单	1
		鼠标离开男装		【延迟】隐藏二级菜单	3
		鼠标进入了电子	【立刻】显示2级菜单	2
		在进入显示二级菜单之前，检查是否要隐藏二级菜单任务（无论有没有直接撤销）
		
		