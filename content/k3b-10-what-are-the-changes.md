Title: K3b 1.0 改变了什么？
Date: 2007-03-18 13:40
Author: toy
Category: Apps
Slug: k3b-10-what-are-the-changes

昨天我们报道了 [K3b 1.0
正式版发布](http://linuxtoy.org/archives/k3b-10-released.html)的消息。对于我们来说，K3b
从 0.12.17 跳跃到
1.0，不单单是一次数字的改变，在其背后，有许多值得注意的更新内容。

以下是 nihui 朋友发来的 K3b 1.0 更新清单，它将有助于我们详细了解在 K3b
1.0 中到底改变了什么？

> 好啦，总结 K3b 1.0 对于 k3b 0.12.17
> 的更新情况不是一项简单的工作。一方面，因为我不得不承认我在为 K3b
> 工作的时候没有保留下详细的更新日志；另一方面，由于许多更改发生在暗处，而不是直接面向用户的。创造
> K3b 1.0
> 是为了获得更好的稳定性和可靠性。我更想去完善已有的特性，而不是引进新的特性。因此，新特性的列表清单可能不是你们想象当中那么长。然而，小小的更改、一点点的改进、修复的问题就会罗列出非常长的清单，而我不会详细地展示出来（主要是因为我没有这样的一张列表）。
>
> 这就是啦，不完全而且是随意排列的 K3b 1.0 更新日志：
>
> *K3b 现在包含了一个 VideoDVD kio 从设备。如果 libdvdcss
> 安装了的话，它能够通过 videodvd:/ 协议在 Konqueror 当中用 on-the-fly
> 解密一个 VideoDVD 复制文件。（注意在某些国家会不被允许使用
> libdvdcss。）
>
> *新的 Device
> 设备菜单包含了一个设备所有可能的动作（像弹出、卸载……）。这包括了指定快捷方式到这些类型的动作的可能。
>
> *如果外部程序的用户参数已经被指定了，现在 K3b
> 就会发出警告。引进这个功能是因为有一些由默认用户参数所引起的错误报告。
>
> *在数据处理方案中，新的选项以使不缓冲 inodes。这意味着在一张 CD/DVD
> 上的同一个文件可能会有多个实际复制版本。现在这个是新的默认值。
>
> *K3b 现在会适当地在使用媒体之前取消挂载它们。
>
> *新的 Audio Track 音轨资源编辑对话框可以在开头和结尾处剪辑音轨。
>
> *为复制光盘扇区的数据和音乐分离“重新读取”和“忽略读取错误”，并且对造成过多读取的音频扇区设定了新的默认值：重试
> 5 次，之后跳过不能读取的扇区。
>
> *新的媒体管理器，能使 K3b
> 一直知道哪种设备包含了哪种媒体。这使得媒体装卸更加平滑，而且用户现在可以选择媒体而不是设备。
>
> 其他的一些优点包括：
>
> -   当查询媒体信息时不再需要等待（包括音频 CD）。
> -   漂亮的默认图像和文件名。
> -   CD 复制：启用/禁用基于来源媒体的选项。
> -   自动选择新插入的媒体作为烧录的媒体。
>
> *DCOP 呼叫 directBurn()
> 函数现在将返回一个布尔值显示进程是否能够启动。
>
> *新的 DCOP 用 media:/ 地址支持呼叫 cddaRip()、videocdrip() 和
> videodvdrip() 函数。
>
> *K3b 现在可以处理从命令行发出的 media:/ 地址来指定设备。
>
> *更好的 Lame 设置对话框。对于初学者更加容易，有更好的默认值。
>
> *更加美观的 Ogg Vorbis 编码设置对话框。
>
> *K3b 现在能在磁盘信息面板中显示出 DVD 媒体的标识符。
>
> *K3b 现在能显示一个对于当前工作大致估计的剩余时间。
>
> *对刻录项目的新的自动媒体大小模式。这意味着 K3b
> 使用插入媒体的大小来作为刻录项目的最大大小。
>
> *当保存一个基于卷标识符（数据刻录项目）或者 CD 标签（音频
> CD）的刻录项目的时候提出一个对于文件名的建议。
>
> *音频编码插件现在可以在万一发生错误时提供用户反馈（非常简单化的反馈）。
>
> *在使用外部程序的音频编码插件中新的设置“交换字节顺序”和“写入波形数据头”。这能使诸如
> mppenc 这样的程序来编码 Musepack 文件。事实上，mppenc
> 只要安装了就会连同 flac 一起被设定为默认程序。
>
> *新的 DCOP 界面：提供 DCOP 对于当前工作信号的
> K3bJobInterface。它也许，例如，能够给一个 Karamba 模块提供信息。
>
> *新的 K3b 刻录项目的 KFile 插件。眼下它只能显示刻录项目的类型（数据
> DVD 或者音频 CD 或者……）但是可以扩展为显示任意的信息。
>
> *K3b 现在选择基于刻录项目名或 CD/DVD 的卷标识/cd
> 标签的默认的映像名称。
>
> *K3b 刻录项目 DCOP 界面现在对 url 参数使用 Qstring 类代替 KURL。
>
> *在音频刻录项目中保存/载入音频 cd 轨道资源。
>
> *显示一个美化过的卷标识。比如：THE\_TRANSPORTER -> The Transporter
>
> *在开始创建一个刻录项目映像之前检查映像目录是否已存在
>
> *对于一个进程暂时隐藏 OSD。
>
> *完全重写了视频 DVD 抓取和译码支持：
>
> -   简单的视频 DVD 标题的 on-the-fly 译码
> -   音频 CD 抓取界面更相似
> -   在抓取窗口中预览图像
> -   自动剪裁
> -   用自动纵横比处理简单调整大小
>
> *文件系统预先调整所有的数据刻录项目包含所有的高级选项。
>
> *完全重写了数据刻录项目的验证：
>
> -   K3b
>     现在将比较写入的映像而不是单个的文件。这可能会使信息量减少，但最终能知道它可以工作。
> -   视频 DVD 刻录项目的验证。
>
> *小部分的 GUI 更改：
>
> -   更改了操作对话框中的会话布局。
> -   简化了数据刻录项目的烧录对话框布局（更多的高级设置被隐藏了）。
> -   改善了主题支持（半透明主题）。
>
> *用 growisofs >= 7.0 对 DVD 烧录显示设备缓冲区状态
>
> *支持用 libcdio 代替 libcdparanoia 抓取音频 CD
>
> *支持 Cdrkit、Debian cd 刻录工具的分支指令。

(Thanks nihui!)
