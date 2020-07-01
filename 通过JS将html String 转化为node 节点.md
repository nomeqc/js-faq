# 通过JS将html String 转化为node 节点
```JavaScript
function parseElement(htmlString){
	return new DOMParser().parseFromString(htmlString, 'text/html').body.childNodes[0];
}
```
