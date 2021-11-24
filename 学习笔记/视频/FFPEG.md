# FFMPEG学习笔记
* ## [官网](https://ffmpeg.org/)
* ## [Windows Build](https://www.gyan.dev/ffmpeg/builds/)
* ## [手册](https://trac.ffmpeg.org/)

* ## 环境变量
  * ### PATH
    > defines the list of :-separated paths where the system looks for binaries.
    For example if you install your package in /usr/local/, you should update the PATH so that it will contain /usr/local/bin.
    This can be done for example through the command export PATH=/usr/local/bin:$PATH.

    **系统查找二进制文件的分隔路径列表。例如，如果您安装包/usr/local/，你应该更新PATH，使其包含/usr/local/bin。例如，这可以通过命令来完成export PATH=/usr/local/bin:$PATH。**

  * ### LD_LIBRARY_PATH
    > contains the :-separated paths where the system looks for libraries.
    For example if you install your package in /usr/local/, you should update the LD_LIBRARY_PATH so that it will contain /usr/local/lib.
    This can be done for example through the command export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH.
    This variable is sometimes deprecated in favor of the use of ldconfig.

    **系统在其中查找库的分隔路径。例如，如果您安装包/usr/local/，你应该更新LD_LIBRARY_PATH，使其包含/usr/local/lib。例如，这可以通过命令来完成export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH。有时不推荐使用此变量以支持使用ldconfig.**

  * ### CFLAGS
    > contains flags used by the C compiler, and usually includes preprocessing directives like -IPREFIX/include or compilation flags.
    Custom CFLAGS are usually prefixed to the source package compiler flags by the source package build system.
    Alternatively many build systems allow to specify the configure option -extra-cflags.

    **包含 C 编译器使用的标志，通常包括预处理指令，如-IPREFIX/include或 编译标志。自定义 CFLAGS 通常由源包构建系统作为源包编译器标志的前缀。或者，许多构建系统允许指定配置选项-extra-cflags。**

  * ### LDFLAGS
    > these are directives used by the linker, and usually include linking directives like -LPREFIX/lib needed to find libraries installed in custom paths.
    Custom LDFLAGS are usually prefixed to the source package linker flags by the source package build system.
    Alternatively, many build systems allow to specify the configure option -extra-ldflags.

    **这些是链接器使用的指令，通常包括链接指令，例如-LPREFIX/lib查找安装在自定义路径中的库所需的链接指令。自定义 LDFLAGS 通常由源包构建系统作为源包链接器标志的前缀。或者，许多构建系统允许指定配置选项-extra-ldflags。**

  * ### PKG_CONFIG_PATH
    > contains the :-separated paths used by pkg-config to detect the pkg-config files used by many build systems to detect the custom CFLAGS/LDFLAGS used by a specific library.

    **用于pkg-config检测许多构建系统使用的 pkg-config 文件的-separated 路径，以检测特定库使用的自定义 CFLAGS/LDFLAGS。**
