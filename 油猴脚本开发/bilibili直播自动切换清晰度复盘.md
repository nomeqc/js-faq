# bilibili直播自动切换清晰度复盘

## 1. 如何获得`video`元素刚开始播放的回调
```js
document.querySelector('video').addEventListener("timeupdate", () => {
    console.log('start playing.');
}, { once: true })
```

## 2. `addEventListener` 只执行一次回调
通过添加once选项，例如：
```js
document.querySelector('video').addEventListener("timeupdate", () => {
    console.log('start playing.');
}, { once: true })
```

## 3. 模拟鼠标动作
```js
const eve = new Event('mousemove');
const livePlayer = document.querySelector('#live-player');
livePlayer && livePlayer.dispatchEvent(eve);

const mouseEnter = new Event('mouseenter');
const qualityBtn = document.querySelector("div.quality-wrap");
qualityBtn && qualityBtn.dispatchEvent(mouseEnter)
```
