## 简单说明

leaflet，mapbox，cesium 通用业务功能封装，框架布局以vue2.6为基础，
地图相关的基础功能已经单独抽离为Service,可单独使用

 常见的点、 线、面、弹框、数据可视化、差值渲染等 

创建、点位绘制
线、面绘制
迁徙图
 
### 其他技术选型

常用的前端地图框架（WebGIS框架）
1. Leaflet
Leaflet 是最著名的前端地图可视化库，它开源、体积小、结构清晰、简单易用。
Leaflet 是一个为建设移动设备友好的互动地图，而开发的现代的、开源的 JavaScript 库。
它是由 Vladimir Agafonkin 带领一个专业贡献者团队开发，虽然代码仅有 38 KB，但它具有开发人员开发在线地图的大部分功能。

leaflet 可以通过简单的 Api 快速构建出简单的地图，结合其他的接口（Marker、 Popup、Icon、Polyline、Polygon等）
即可快速实现点、线、面的绘制，社区中也有非常丰富的插件，可以低成本的实现诸如热力图、插值、聚合、数据可视化等功能，
需要注意一点 leaflet 只能实现 2D 地图。


2. Mapbox GL JS
Mapbox GL JS 是目前最新潮的前端地图库，它的矢量压缩、动态样式和三维性能令人印象深刻。它本身是开源的，但一般依赖于Mapbox公司提供的底图服务。

Mapbox GL JS 是一个 JavaScript 库，它使用 WebGL，以 vector tiles 和 Mapbox styles 为来源，
将它们渲染成互动式地图。它是 Mapbox GL 生态系统的一部分，其中还包括 Mapbox Mobile，
它是一个用 C++ 编写的兼容桌面和移动平台的渲染引擎。


3. ArcGIS API for JS
ArcGIS API for JS 是较为学院派的前端地图库，它是ArcGIS开发套件中的一部分，和桌面端和服务器端ArcGIS软件有较好的协作。它不开源且收费不低，在学术场景下较为常用。

4. Openlayers
Openlayers 也是常用的前端地图库，它开源，相比于Leaflet更加复杂和完备。

5. Cesium
Cesium 是三维地理可视化的常用库，在大尺度的可视化（地形、建筑、地球）中十分常用。
Cesium是国外一个基于JavaScript编写的使用WebGL的地图引擎。Cesium支持3D,2D,2.5D形式的地图展示，可以自行绘制图形，
高亮区域，并提供良好的触摸支持，且支持绝大多数的浏览器和mobile。

cesium 最重要的是可以实现三维效果，如果项目中有加载模型（类似园区模型）、场景模拟的需求时，
可以选用 cesium 的方式实现（针对预算不足，无法采购其他商用方案时）。

6. 百度地图 JS API /百度地图 API GL
百度地图 JS API 是传统的二维地图，百度地图 API GL 是三维地图，它们依赖百度地图提供的后台服务。除了地图服务外还有检索、导航、实时交通等关联服务。开发者有免费的限额。

7. 高德地图 JS API
高德地图 JS API 与百度类似。

8. Google Maps JS API
谷歌地图 JS API 在境外有更好的数据。

9. AntV L7
AntV L7 是空间数据可视化库，它可以使用高德地图等协作构建地图可视化。

10. Mapbox.js
Mapbox.js 是 Leaflet 的一个扩展插件（与 Mapbox GL JS 不同）。
 
 市面上也还有非常的多的解决方案，诸如 openlayers、百度地图、高德地图等。百度、高德提供的 sdk 也可以实现简单的 gis 效果，但不适用复杂效果的开发，笔者还是推荐对于复杂的地图效果使用专业 gis 解决方案。对于 leaflet、mapBox、cesium 从数据管理的方式做一下简单类比：


leaflet 以图层的方式管理数据，一切的数据（点、线、面）都可以看做成独立的图层，开发者只需要对相应的图层执行挂载、卸载即可；


mapbox 以资源的方式管理数据，mapbox 最常见的数据管理可以通过加载标准的 geoJson 数据，然后在后续的地图操作中可以指定相对应的资源 id；


对于普通的前端开发，cesium 推荐使用实体的方案管理地图中的数据，一切皆为实体。


在 gis 代码编写过程中需要注意代码的优化，及时的卸载各种事件的监听、数据的销毁、否则极容易造成地图的卡顿，cesium 要尤为注意。
 