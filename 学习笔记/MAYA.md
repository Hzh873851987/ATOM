# Alembic格式
  * ## [Alembic](https://download.autodesk.com/global/docs/maya2012/zh_cn/index.html?url=files/GUID-A1751075-FD99-40B7-88CC-C6502B66056-5.htm,topicNumber=d28e6148) 格式概述
  > 可以将 Maya 场景文件作为 Alembic 缓存文件进行保存和加载。Alembic 文件格式是一种开源格式，专为交换复杂 3D 几何数据而开发。</br>
  Alembic 文件是具有较强可移植性且与应用程序无关的文件，因此可由多种内容创建应用程序进行共享、处理和播放。</br>
  在 Maya 中，Alembic 缓存提供了许多性能改进，包括快速加载大型场景、快速播放复杂角色动画，以及实时播放包含拓扑更改的几何数据。</br>
  可以将复杂的场景和动画导出为 Alembic 文件，然后将其重新导入到 Maya 中，以提高播放性能并减少内存使用。</br>
  通过此工作流，可以轻松地将复杂场景数据传递到制作流程的各个区域，如动画与模拟之间的区域或动画与照明之间的区域，而不会因为完全可编辑的场景产生较大的开销。</br>
  例如，可以将从 nParticle 效果创建的多边形网格导出为 Alembic 文件，然后在 Maya 中仅作为多边形对象播放模拟。</br>
  可以使用“Alembic 导入”（Alembic Import）和“Alembic 导出”（Alembic Export）窗口配置用于加载和保存 Alembic 文件的设置。</br>
  可以从位于 Maya 主菜单栏上的“Alembic”菜单访问“Alembic 导入”（Alembic Import）和“Alembic 导出”（Alembic Export）窗口。</br>
  也可以使用 MEL 命令导入和导出 Alembic 文件。

  * ## 导入和导出 Alembic
  > 若要将 Maya 场景作为 Alembic 文件进行导入和导出，则必须加载 AbcImport.mll 和 AbcExport.mll 插件。</br>
  打开“插件管理器”（Plug-in Manager）（“窗口 > 设置/首选项 > 插件管理器”（Windows > Settings/Preferences > Plug-in Manager）），以确保这些插件已加载到 Maya 中。

# 绑定Rigging
  * ## 绑定类似于父子关系，呈一种约束关系
  * ## IK（反向动力学）
    * IK 不是骨骼，而是控制柄，由ik和极向量来控制骨骼
    * IK是靠末端的位移来控制父级的变化！但是因为是随机的所以需要用极向量来确定方向
  * ## FK（正向动力学）
    * 更像是骨骼一段一段
    * FK是靠父级的旋转来控制子集的变化！但是要注意旋转的合理性!比如人的腿只能是向后弯曲而不能左右弯曲

  ## 可以这样理解，你试着抬起你的左脚，IK是你的脚发力，带着你的腿运动，FK是你的腿发力，带着你的脚运动
