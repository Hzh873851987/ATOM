# 当无法拖拽文件到 Viewport时，检查 MAYA快捷方式属性-兼容性-管理员身份运行(`关闭`)
---
# Alembic格式
  * ## [Alembic](https://download.autodesk.com/global/docs/maya2012/zh_cn/index.html?url=files/GUID-A1751075-FD99-40B7-88CC-C6502B66056-5.htm,topicNumber=d28e6148) 格式概述
  > 可以将 Maya 场景文件作为 Alembic 缓存文件进行保存和加载。Alembic 文件格式是一种开源格式，专为交换复杂 3D 几何数据而开发。</br>Alembic 文件是具有较强可移植性且与应用程序无关的文件，因此可由多种内容创建应用程序进行共享、处理和播放。</br>在 Maya 中，Alembic 缓存提供了许多性能改进，包括快速加载大型场景、快速播放复杂角色动画，以及实时播放包含拓扑更改的几何数据。</br>可以将复杂的场景和动画导出为 Alembic 文件，然后将其重新导入到 Maya 中，以提高播放性能并减少内存使用。</br>通过此工作流，可以轻松地将复杂场景数据传递到制作流程的各个区域，如动画与模拟之间的区域或动画与照明之间的区域，而不会因为完全可编辑的场景产生较大的开销。</br>例如，可以将从 nParticle 效果创建的多边形网格导出为 Alembic 文件，然后在 Maya 中仅作为多边形对象播放模拟。</br>可以使用“Alembic 导入”（Alembic Import）和“Alembic 导出”（Alembic Export）窗口配置用于加载和保存 Alembic 文件的设置。</br>可以从位于 Maya 主菜单栏上的“Alembic”菜单访问“Alembic 导入”（Alembic Import）和“Alembic 导出”（Alembic Export）窗口。</br>也可以使用 MEL 命令导入和导出 Alembic 文件。

  * ## 导入和导出 Alembic
  > 若要将 Maya 场景作为 Alembic 文件进行导入和导出，则必须加载 AbcImport.mll 和 AbcExport.mll 插件。</br>
  打开“插件管理器”（Plug-in Manager）（“窗口 > 设置/首选项 > 插件管理器”（Windows > Settings/Preferences > Plug-in Manager）），以确保这些插件已加载到 Maya 中。

  * ## 导出[高级选项](https://knowledge.autodesk.com/zh-hans/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2022/CHS/Maya-Basics/files/GUID-854D22F6-7547-465C-8A13-E21A8A6D9714-htm.html)（部分）
    * ### UV Write
      * 启用该选项以将 UV 数据从多边形网格和细分对象写入到 Alembic 文件中。`仅包含当前的 UV 贴图。`
    * ### Write Visibility
      * 启用该选项以将对象的可见性状态存储在 Alembic 文件中。`否则，所有对象都视为可见。`
    * ### World Space
      * 启用该选项以将节点层次中的顶部节点存储为世界空间。默认情况下，这些节点存储为局部空间。
    * ### Filter Euler Rotations
      * 启用该选项以使用 Euler 过滤器过滤 X、Y 和 Z 旋转数据。Euler 过滤有助于解决旋转中的违规情况，`尤其是 X、Y 和 Z 旋转超过 360 度时。`

# Maya有时会打不开一些窗口 Panel，可能是因为多个显示器在使用时切换过显示器主次排列造成。
# 尽量在主显示器窗口使用或者关闭窗口 Panel
---
# 绑定Rigging
  * ## 绑定类似于父子关系，呈一种约束关系
  * ## IK（反向动力学）
    * IK 不是骨骼，而是控制柄，`由ik和极向量来控制骨骼`
    * IK是靠末端的位移来控制父级的变化！但是因为是随机的所以需要用极向量来确定方向。
    * `也就是通过定位骨骼链中较低的骨骼，使较高的骨骼旋转，从而设置关节的姿势`
  * ## FK（正向动力学）
    * FK是靠父级的旋转来控制子集的变化！但是要`注意旋转的合理性`!比如人的腿只能是向后弯曲而不能左右弯曲
    * FK是带有`层级关系`的运动，是根据父关节的旋转来计算得出每个子关节的位置。

  ## 可以这样理解，你试着抬起你的左脚，IK是你的脚发力，带着你的腿运动，FK是你的腿发力，带着你的脚运动
---
# 摄像机
  * ## 开启FOV (Filed Of View)显示
      > Attribute Editer
      >> Frustum Display Controls
      >>> Display Frustum

  * ## [Gimbal Lock万向节死锁](https://www.zhihu.com/question/47736315/answer/236284413)</br>比如xyz旋转轴向：</br>以MAYA为例，z轴为最外层。</br>当物体沿Y轴旋转达到90°时，会造成X轴与Z轴重合从而丢失通滚的自由度，即 Gimbal Lock。</br>此时如果需要进行通滚的动作则需要同时运动三个轴向来给予Z轴自由度，这便会使得物体产生奇怪的运动轨迹。</br>死锁问题可以通过**四元数**来解决，或者使用不同的 Rotate Order来尽量避免。

  * ## 摄像机无法进行冻结变换操作，因为它不是一个Poloy。</br>可以使用打组的方式进行一个绑定。
  > cam_rotate 负责摄像机的旋转`(注意设置需要的 Rotate Order(即万向节的嵌套关系) 避免 Gimbal Lock万向锁)`</br>
  一般摄像机只会做俯仰和偏航以及水平移动，所以旋转方向通常使用 zxy轴向
  >> cam_move 负责摄像机的水平移动
  >>> cam(摄像机本身) 需要的话可以加一些旋转`(同样注意 Rotate Order)`

---
# 使用 FBX格式导入动画可以覆盖相同名称的节点从而直接替换动画
## `注意：如果有名称空间(NameSpace)，也需要相同`
---
# [Mixamo 导入动画速度过快问题](https://knowledge.autodesk.com/zh-hans/support/maya/learn-explore/caas/sfdcarticles/sfdcarticles/CHS/Animations-moving-super-fast.html)
---
# 编辑动画骨骼曲线时注意是否选中需要的子级
## `全选可以使用 select菜单下的 Hierarchy`
---
# 关于动画层的使用
  * ## 可以为`(尤其是动作捕捉数据这类关键帧比较多的动画时)`需要单独调试动画的物体创建动画层(Create Anim Layer From Selected)，并在新层中的第一帧插入关键帧，之后便可以调整这些物体的位置、旋转而不影响动画的播放。
---
# 关于 Playback的设置
  ## 做`动画`时设置成real time，默认是1秒播放24帧，这是为了方便动画师K动画能有个正确的时间参考。

  ## `动力学解算`是逐帧计算的，为了准确，因此需要设置成play every frame，否则可能会出错。

  ## 做`特效`的话，在正式渲染之前，一般会先拍屏预览，maya中就是playblast，这样便于观察速度和节奏。
---
# [动画的烘焙](https://knowledge.autodesk.com/zh-hans/support/maya/troubleshooting/caas/CloudHelp/cloudhelp/2020/CHS/Maya-Animation/files/GUID-A11424B4-8384-4832-B18D-01264E1A19D1-htm.html)
  > #### 切换至 Animation工具栏
  >> #### Key
  >>> #### Bake Simulation

  ## 如果不进行烘焙则每一次的动画播放都会重新进行解算。

  ## 通过烘焙动画的方式，可以将动画曲线烘焙到控制器等任何具有通道属性的节点上。
  * 例如：当混合两端动画的时候，将第一段编辑完之后的动画烘焙到角色的控制器上之后就可以导入新的骨骼动画继续编辑第二段动画，此时第一段动画的曲线已经保留在角色控制器上而不会收到影响，且可以在之后继续编辑控制器动画曲线对第一段动画进行调整。


  ## 烘焙后的骨骼节点可以删除
---
# Locator 的使用
  ## Locator可以和骨骼绑定作为其父级约束，用于控制其移动旋转的变换。在 Locator上编辑动画后将动画烘焙至骨骼上便可获得一个干净的骨骼动画曲线。
---
# Graph Editor曲线编辑器
  * ## 延长动画
    ---
  * ## [Euler Filter(欧拉角度过滤器)](https://knowledge.autodesk.com/zh-hans/support/maya/getting-started/caas/CloudHelp/cloudhelp/2020/CHS/Maya-Animation/files/GUID-9E69ABB3-E94B-4D67-9935-40F77FD2E9E0-htm.html#WS17956D7ADBC6E73647E34F8F117AE307467-7FF5)
    * ## 烘焙动画之后应该在 Graph Editor(曲线编辑器)中检查是否有因万向节死锁或其他原因引起的曲线波动。
      ## 表现为动画中奇怪的旋转，或编辑器中不规律的曲线。
      ## `可以用以下方法自动修复`
      > Graph Editor
      >> 选中所有的曲线(或者有问题的通道)
      >>> Curves
      >>>> Euler Filter
---
# 缩放关键帧后应当使用 `Snap来对齐关键帧到整数帧`，否则小数部分将不会渲染造成动画衔接不够顺畅
---
# 混合动捕数据时，我们可以在 Graph Edito中编辑特定控制柄(教程中使用的时 FK，所以只使用一个胯骨的控制柄来控制整体的移动)曲线来调整动画的衔接(`符合运动规律`，比如人跑步，胯骨的位移在 Y轴上呈现上下平滑的波浪曲线)。
#### `参考教程21集00:17:25`
---
# `实际项目中 动画一般从第 1000帧开始，当需要增长动画时向前调整就不会进入负数帧。`
---
# 在 Nucleus的通道中打开 use plane即可启用地面碰撞模拟
