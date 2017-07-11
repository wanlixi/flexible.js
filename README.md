# flexible.js
移动端适配问题
```
// designWidth: 设计稿的宽度  maxWidth: 最大宽度
module.exports = function(designWidth, maxWidth) {
	var doc = document, win = window, docEl = doc.documentElement, remStyle = document.createElement("style"), tid;
	function refreshRem() {
		var width = docEl.getBoundingClientRect().width;
		maxWidth = maxWidth || 540;
		width > maxWidth && (width = maxWidth);
		var rem = width * 100 / designWidth;
		remStyle.innerHTML = 'html{font-size:' + rem + 'px;}';
	}
	if (docEl.firstElementChild) {
		docEl.firstElementChild.appendChild(remStyle);
	} else {
		var wrap = doc.createElement("div");
		wrap.appendChild(remStyle);
		doc.write(wrap.innerHTML);
		wrap = null;
	}
	//要等 wiewport 设置好后才能执行 refreshRem，不然 refreshRem 会执行2次；
	refreshRem();
	win.addEventListener("resize", function() {
		clearTimeout(tid); //防止执行两次
		tid = setTimeout(refreshRem, 300);
	}, false);

	win.addEventListener("pageshow", function(e) {
		if (e.persisted) { // 浏览器后退的时候重新计算
			clearTimeout(tid);
			tid = setTimeout(refreshRem, 300);
		}
	}, false);

	if (doc.readyState === "complete") {
		doc.body.style.fontSize = "16px";
	} else {
		doc.addEventListener("DOMContentLoaded", function(e) {
			doc.body.style.fontSize = "16px";
		}, false);
	}
};
``` 
## 已经发布在 npm 上 可以使用 npm i --save flexible.js 下载
### 具体使用：全局注入
lib.js
```
假设设计稿宽度是 375
require('flexible')(750, 640)
```
在vscode编辑器里面设置：
### ctrl + ，###
搜索 rem ，然后找到"cssrem.rootFontSize" 将其改为48（也可以根据需要设置）
