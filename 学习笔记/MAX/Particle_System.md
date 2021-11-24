# ~~暂时只编写教程所用到的部分~~

# [Particle(粒子系统)](https://knowledge.autodesk.com/support/3ds-max/learn-explore/caas/CloudHelp/cloudhelp/2020/ENU/3DSMax-Simulation-Effects/files/GUID-63C04CEF-F150-4983-BDC2-034ACF0BCBBB-htm.html)
  > ## Graph Editor
  >> ## Particle View (节点图)
  >> ## (NUM 6)

---
## 粒子系统分为 [Particle Flow(事件驱动)](https://help.autodesk.com/view/3DSMAX/2020/ENU/?guid=GUID-F4FD836C-5967-4DF4-9E2B-66A16292173D)和 non-event-driven systems(非事件驱动)
  > ### 事件驱动的粒子系统每个节点都会为粒子分配各种属性和行为并重新计算。(适用于更灵活且复杂的粒子模拟，如火焰、碎片等)
  > ### 在非事件驱动系统中，粒子通常在整个动画过程中表现出`一致`的属性。(适用于简单动画，如飘落的雪花)

  ---
  ### Particle Flow(分为 [Flow(工作流)](https://help.autodesk.com/view/3DSMAX/2020/ENU/?guid=GUID-D335CC59-E27E-4803-8D6F-D7F3955EFF64)、[Operators(操作符)](https://help.autodesk.com/view/3DSMAX/2020/ENU/?guid=GUID-03530ACE-C9F8-4E29-B6CD-7B7BA09F986F)、[Painting Particle(绘制粒子)](https://help.autodesk.com/view/3DSMAX/2020/ENU/?guid=GUID-6D6180D2-D25A-458F-A911-39B9000E50DC)和[Tests(测量)](https://help.autodesk.com/view/3DSMAX/2020/ENU/?guid=GUID-D7007897-7972-4FAB-9A36-92166657E44D)几种 Actions)
  ---
  * ### Flow
    #### 作为整个工作流的起点，否则将无法显示(无论是 Viewport中还是渲染画面)
    * Empty Flow 仅包含一个带有 Render Operator的 [PF Source](https://help.autodesk.com/view/3DSMAX/2020/ENU/?guid=GUID-89DA4474-E8F4-496F-9339-305D8C8E241E)

  * ### Operator
    * Display

  * ## Birth
    ### The Birth operator must always come at the beginning of a particle stream (放在开头)

    * ### Subframe Sampling(子帧采样)
      #### 启用将计算小数帧(即贯穿每一帧)，但不会显示。</br>关闭则将四舍五入到最接近的整数帧。

    * ### Amount(数量)
      #### Birth Event下粒子数量(Amount)的实际数量为：</br>Amount / (Emit Stop - Emit Start + 1)

    * ### Rate(速率)
      #### 从帧开始到帧结束，每秒发射此数量的粒子。
      ### 如果您指定的出生率值不是系统每秒帧数（在“时间配置”对话框中设置）的整数倍，则粒子流将使用插值来确定何时发射粒子。
      #### e.g.</br>如果您使用系统默认的每秒 30 帧的速率，并将出生率设置为 4，关闭子帧采样，系统会以 7 或 8 帧的间隔发射每个粒子，如果开启，则以 7.5 帧的间隔发射每个粒子。

  * ## Spawn
