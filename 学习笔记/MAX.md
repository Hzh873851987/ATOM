# Vray
  * ## ~~[Vray NEXT 不包含 RT模式，请使用V-Ray IPR或Viewport IPR作为渲染选项](https://forums.chaosgroup.com/forum/v-ray-rt-forums/v-ray-rt-general/1055905-vray-rt-not-in-next)~~
    * [解决](https://docs.chaosgroup.com/display/VMAX/V-Ray+Next%2C+Update+3)

  * RT模式的凹凸贴图有可能与ADV模式渲染出来的凹凸贴图可能存在不同，往往在RT渲染调试后需要在ADV模式中重新检查

  * ViewPort左上角 VrayToolbar 茶壶
  * 或者 x开启搜索 输入 IPR

  * ## VRay的面光(Plane)默认是散射光源，阴影会比较虚。</br>可以通过：
    > Rectangle/disc light
    >> Directional(方向性)
    ## 来聚拢光源从而增强阴影。

  * > General
    >> Multiplier(光照强度)
    ## 也会影响阴影虚实

  * > Options
    >> Affect diffuse(影响漫反射)</br>
    >> Affect Specular(影响高光)

  * ## 分通道渲染(`重要`)
    > 在后期调整时将通道重新整合，方便调整而不需要重新渲染</br>`教程中 Vray版本为 3.4，可以将每一盏灯光分为漫反射、高光和反射`
    ### 一般分为 GI层、光照层、高光层、反射层、折射层、自发光等

  # Particle(粒子系统)
    ##### (教程中用于模拟雨滴在玻璃上的滑动效果以替代更消耗资源的流体模拟，```最终只需要一张渲染后的Alpha通道图```)
    >Graph Editor
    >> Particle View(NUM 6)

    * ## Birth
      ## The Birth operator must always come at the beginning of a particle stream

      * ### Subframe Sampling(子帧采样)
        #### 启用将计算小数帧(即贯穿每一帧)，但不会显示。</br>关闭则将四舍五入到最接近的整数帧。

      * ### Amount(数量)
        #### Birth Event下粒子数量(Amount)的实际数量为：</br>Amount / (Emit Stop - Emit Start + 1)

      * ### Rate(速率)
        #### 从帧开始到帧结束，每秒发射此数量的粒子。
        ### 如果您指定的出生率值不是系统每秒帧数（在“时间配置”对话框中设置）的整数倍，则粒子流将使用插值来确定何时发射粒子。
        #### e.g.</br>如果您使用系统默认的每秒 30 帧的速率，并将出生率设置为 4，关闭子帧采样，系统会以 7 或 8 帧的间隔发射每个粒子，如果开启，则以 7.5 帧的间隔发射每个粒子。

    * ## Spawn
