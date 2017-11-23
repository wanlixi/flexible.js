# flexible.js
移动端适配问题
<h1>可以在各种全家桶项目的入口文件中引入:</h1>
<br />
<h3>首先安装flexible.js</h3>
<br />
<code>npm i -S flexible.js</code>
<br />
or
<br />

<h3>如果npm安装比较慢的话，使用淘宝镜像cnpm安装</h3>
<br />
<h4>先在命令行工具里面输入：</h4>
<br />
<code>npm install -g cnpm –registry=https://registry.npm.taobao.org</code>
<br /><br />
<h4>成功之后输入：</h4>
<br /><br />
<code>cnpm i -S flexible.js</code>
<br /><br />
<h4>找到目录</h4>
<br /><br />
<code>
src/main.js
</code>
<br /><br />
<code>
import flexible form 'flexible.js'
<br /><br />
flexible();

</code>
<br /><br />
or
<br /><br />
<code>
</code>
<br />
<small>注意因为移动端的设计稿通常是按照iphone6的尺寸，即750   * 1334，所以我在封装的时候内部设默认置的第一个参数即设计稿尺寸为750，第二个参数为最大宽度，默认设置的是640，	即没有兼容到ipad等大屏幕设备，你们在开发中可以结合实际的情况自己传入对应的参数即可！</small>
<br />
<h2>
	如果您使用的sublime编辑器，可以下载插件remunit，如果您使用的是vscode编辑器，可以下载插件cssrem，两个都需要配置：50基数，即：
	<br />
  <code>font-size：1rem；/*50px*/</code>
</h2>
