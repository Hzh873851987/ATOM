# [关于 NUKE Version 12+无法启动的问题](https://support.foundry.com/hc/en-us/articles/360017022219-Q100588-Hiero-encountered-a-fatal-error-and-crashes-when-launching-Nuke-on-Windows-)
  > `Hiero encountered a fatal error and crashes when launching Nuke on Windows.`

  ~~this has been resolved within the Nuke 13.0+ releases.~~

---

# Nuke导入的模型需要 UV

---

# 教程中的插件地址：
  ## [RainMaker](http://www.nukepedia.com/gizmos/particles/rainmaker)
  ### ~节点中 Reformat无法使用 scale属性，版本1.1~

  ## [expoglow](http://www.nukepedia.com/gizmos/filter/expoglow)

  ## [fxT_chromaticAberration](http://www.nukepedia.com/gizmos/filter/chromaticabberation)

---

# [Bounding Box(BBox 边界框)](https://learn.foundry.com/nuke/content/comp_environment/reformatting_elements/adjusting_bbox.html)
  ## 边界框定义了 Nuke 认为具有有效图像数据的帧区域。边界框越大，Nuke 处理和渲染图像所需的时间就越长。

---

# 分离(组合)光源通道
  ## 当光源复杂或需要后期调整时，可以选择使用`shuffle`节点将所有的光源通道单独分开成`漫反射`、`高光`等`(教程中 Vray在分灯光渲染时只能分离漫反射和高光)`，再通过`Merge 加法`节点进行加法合并。

  ### `注意：Shuffle节点分离出的通道带有 Alpha，直接合并会造成多次相加，需要对每个通道添加 Remove节点来去除 Alpha通道，在最后所有合并做完再单独赋予 Alpha，就可以保证所有像素的边缘能够保留`

  ### `再注意：在用 Shuffle分割前，就 .exr格式而言，导入 Nuke之后图像像素与 Alpha已经做过乘法运算，为了保证最大细节，应当先使用 Unpremult预除使图像回到未处理时的效果`

  ## 最后组合通道时，将 Gi全局光照作为底层和光源通道 Merger`(组合顺序可以参考材质球)`

---

# (3dsmax 导出摄像机到 NUke的正确方式)[https://zhuanlan.zhihu.com/p/51561583]

---

# 部分节点介绍
  ## Erode(侵蚀)和 Dilate(膨胀)
