1\. 在需要自启动的项目中安装 node-windows 模块 npm install node-windows --save

2\. 在项目根目录创建nw.js文件


**代码文本：**
```js
let Service = require('node-windows').Service;

let svc = new Service({
	name: 'cors-anywhere', //服务名称
	description: '代理请求以支持跨域;下载文件支持指定文件名', //描述
	script: './server.js', //nodejs项目要启动的文件路径
	wait: '1', //程序崩溃后重启的时间间隔
	grow: '0.25', //重启等待时间成长值，比如第一次1秒，第二次就是1.25秒
	maxRestarts: '40' //60秒内最大重启次数
});

svc.on('install', ()=>{
	svc.start();
	console.log('install complete.');
});

//监听卸载事件
svc.on('uninstall', () => {
	console.log('Uninstall complete.');
	console.log('The service exists', svc.exists);
});

//防止程序运行2次

svc.on('alreadyinstalled', () => {
	console.log('This service is already installed.');
})

//如果存在就卸载
if (svc.exists) return svc.uninstall();
//不存在就安装
svc.install();
```

3\. 运行nw.js文件 命令：node nw.js 这个时候如果安装了安全管家等软件会阻止，直接允许就可以了。运行成功后在电脑的服务中就能看到这个服务，现在就可以像普通的windows-server服务一样操作。

![](https://static.dingtalk.com/media/lALPJxuMOLHVEOnNASLNAi4_558_290.png)

运行node nw.js命令后,会在启动的node文件对应的目录下生成 daemon文件夹

![](https://static.dingtalk.com/media/lALPJxRxO2gZuCbMxs0CMA_560_198.png)

普通日志,错误日志,配置信息都有。

4\. 现在就可以连接nodejs项目，Nodejs项目开机自启动基本已完成。再次运行 node nw.js命令会卸载掉我们安装的服务。

- (nodejs项目windows下开机自启动)[https://blog.csdn.net/github_39294367/article/details/76285852]
