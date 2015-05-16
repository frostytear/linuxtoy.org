Title: Linux 硬件迁移小测试
Date: 2012-11-29 18:04
Author: lovenemesis
Category: Tips
Tags: Fedora
Slug: small-test-of-linux-system-hadrware-migration

趁着电商混战之时购入了新主机？作为 Linux
用户，在将满载数据的老硬盘接上后也要向 Win
用户一样进行繁复的驱动重装甚至系统重装过程么？本人进行的两次小测试可以告诉你答案。

**测试目标**

将老主机上装有操作系统的硬盘直接连上新主机，检查新主机是否可以正常使用。

**测试用机信息**

为了简化，仅列出重要区别部分。

主机A

-   CPU：奔腾D 双核 T2390
-   芯片组：Intel PM965+ICH8M
-   显卡：Radeon HD 2400XT
-   BIOS/UEFI：BIOS

主机B

-   CPU：羿龙三核 P820
-   芯片组：AMD M880G
-   显卡：Radeon HD 5470M
-   BIOS/UEFI：BIOS

主机C

-   CPU：APU A10-5800K
-   芯片组：AMD A85X
-   显卡：核显 Radeon 7660D
-   BIOS/UEFI：UEFI

使用安装有 Fedora 17 64
位版本并安装了至撰文时所有更新的两块硬盘进行测试：

-   硬盘A分区表是 MBR，原安装在主机A 上。
-   硬盘B分区表是 GPT，原安装在主机B 上。

**迁移测试一：将硬盘A 从主机A 迁移到主机B**

从配置比较中可以看出这是一个**从 Intel 平台向 AMD
平台的迁移**，处理器和主板芯片组都有巨大的变化，实际上内存也由 DDR2
变化为 DDR3 了。

过程很简单，将主机B 上原先的硬盘B
拆除后插上硬盘A，之后启动主机B。顺利引导进入，**无需任何额外配置**，即插即用。基于
KMS 的 Radeon 驱动 Gallium3D 顺利启用并打开硬件加速。

**迁移测试二：将硬盘B 从主机B 迁移到主机C**

从配置比较中可以看出这是一个**从 BIOS 向 UEFI
的迁移**。在迁移之前，有两点比较担心，一是使用 GPT 分区表的硬盘B
上有一个 1M 大小的 BIOS 兼容分区，该分区在 UEFI 应该是多余的；二是 UEFI
的 Secure Boot 是否需要在 GRUB2 处做额外配置。

不过结果证明之前的两个担忧是多余的，在 UEFI 关闭 Secure Boot 之后，硬盘B
顺利的在主机C 上启动起来，冗余的 BIOS 兼容分区并没有对 GRUB2
的引导带来任何困扰，底层变为 UEFI 也无需额外设置。只是 Gallium3D Radeon
并未识别出来 Radeon 7660D 的核显，GNOME 3.4.X 运行在 llvmpipe 下。

**结果分析**

其实结果并不出人意料，**Linux
下硬件迁移并不需要重装驱动或者系统**。大致来说原因有以下几点：

-   作为鼓励分发的开源免费操作系统，**Linux 没有如 Win 一样的 DRM
    防盗版机制**，也就不会像 Win7 那样在多个组件变更后要求重新激活。
-   **一般二进制 Linux 发行版搭载了通用的 x86
    内核和适用于各种硬件的平台的用户态组件**，进行硬件迁移一般不会导致找不到驱动内核模块或者用户态组件的问题。
-   **KMS(Kernel Mode-Setting) 技术摆脱了固定 X.org
    配置文件的限制**，即使显卡型号变化也可以正确处理。

（更新）在迁移之后**有需要变更的地方**：

-   如果之前使用了品牌不同（如在 NVIDIA 和 AMD
    之间迁移）的**闭源显卡驱动**，则必然要更改；同品牌的闭源驱动按照硬件型号需要的版本有时也存在不同（如
    stable 和 legacy）。故建议在迁移前临时卸载闭源驱动转用 KMS
    的开源驱动。
-   由于 CPU/主板/显卡的变化，**温度测试工具** `lm-sensors`
    很有可能需要重新初始化，在新主机上运行 `sensors-detect` 即可。
-   由于**有线及无线网络信息**是保存在设备相关的配置文件中的，在硬件更换了之后是必须要重新配置的。

欢迎诸位童鞋在评论中分享自己迁移成功或失败的经验和教训～