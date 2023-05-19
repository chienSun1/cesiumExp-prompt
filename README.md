## Cesium气泡窗插件
[在线api文档说明](http://mapgl.com/3dapi/Prompt.html)
[在线体验地址](http://mapgl.com/shareCode/#/PopupTooltip?downUrl=)
[更多案例地址](http://mapgl.com/shareCode/)
***
实现原理：
Cesium和我们平时常见的leaflet、ol以及arcgis api是不一样的，其没有内置的气泡窗，那么就得靠我们手写气泡窗来实现了。
本插件样式是参考了leaflet来写的。
气泡窗目前分两种：
    1、固定位置气泡窗，即气泡窗的位置固定在地图的某一个点上，不会随鼠标移动。
    2、可移动气泡窗，通过给定像素坐标和三维世界坐标来进行气泡窗坐标的设置。
主要的点就是做了：像素坐标和三维世界坐标的相互转换。

***
两种调用方法：
1、固定位置气泡窗：
```
prompt1 = new Prompt(viewer, {
    type: 2,
    content: "我是定点提示框",
    position: [117, 32, 100], // 支持多种形式传参 cartesian3 || array || object
    close: function () {
      alert("easy3d--三维可视化类库！");
      return false
    } // 点击关闭按钮的回调函数
  });
```

2、鼠标移动气泡窗：
```
  movePrompt = new Prompt(viewer, {
    type: 1,
    content: "我是移动提示框"
  })
    // 设定鼠标位置
   movePrompt.update({
      x: evt.clientX,
      y: evt.clientY
    })
```
