# 完美使用windows桌面。V1版本介绍
本人通常使用，一般会划分四个虚拟桌面，分别应用于：
- 系统学习，会来云笔记，chrome。
- 娱乐聊天，会开，tim，微信，网易云
- 当前任务，会开idea进行，各种代码任务
- 天马星空，这个处理那些无关紧要的随意事物。

遇到问题，桌面间切换效率太低。很尴尬，很难受，不能忍。windows虚拟桌面，只支持简单的上一个和下一个，不支持跨越式跳转。故而几经思索琢磨组合了这一套东西。个人认为很完美，欢迎指导，一起进步。

## 设计：
### 逻辑设计上：
采用vim-like的键位方式，使得对按键记录成本不高。jkli也符合，上下左右，四个方位的定义，对应着这四个桌面。

快捷键ctrl+win+[jkli]来切换到指定的虚拟桌面。分别按键位的顺序对应到1234虚拟桌面。完美把四个方位的平面映射，变成了线性映射。

鼠标手势控制，通过鼠标右键，按下，上下左右滑动，来快速的切换对应到平面上的四个方向虚拟桌面。

### 实现上：

快捷键= ahk + vim-like key

鼠标控制= strokens-plus + ahk + vim-like key

## 安装：
1. cd /xxxxx/你的软件安装目录。git clone https://github.com/fanlushuai/windows-desktop-switcher.git
2. 安装[ahk](https://www.autohotkey.com/)
3. 安装[strokens Plus](https://www.strokesplus.com/downloads/)
4. 配置ahk脚本开机启动
- Press Win + R, enter shell:startup, then click OK
- Create a shortcut to the desktop_switcher.ahk file here
5. 启动strokens Plus导入本项目的strokens plus配置文件。strokens-plus-config.spactions

## 使用：
快捷键：
- ~~ctrl + win + [j k l i] 切换到 左下右上 虚拟桌面，同时对应 1234 虚拟桌面~~
ctrl+win+[jkli] 对于单手操作是不友好的。所以换成 capslock+[sdfe]。（但是也是支持的^#[jkli]。鼠标手势基于这个）

不使用capslock+[asdw]的原因是，照顾固定的快捷键。使其能通过首字母方便记忆。还有就是使得左手食指位于F键位上。上面是有凸起的。方便定位。

capslock+[sdfe]、capslock+shift+[sdfe]逻辑主要应用在移动窗口和切换虚拟桌面。
因为ahk的缘故，对三个组合键，支持的莫名其妙。使用中发现没法让这两种类似的组合键和平相处。
重新整理思路发现，没有合适的快捷键来替换。
后来从操作便携性角度分析，发现其实移动窗口对单手有需求，但是切换桌面，对单手并没有那么大需求，因为单手往往处于另一只手在鼠标上，那么其实我们鼠标手势已经映射了桌面切换。
这样，键盘操作上，我们还是采用^#[jkli]切换桌面，采用caps+[sdfe]来移动窗口，变通思维解决了ahk的问题。还算完美。

鼠标手势：
- ← ↓ → ↑ 对应到切换到  左下右上 虚拟桌面

同时支持快捷键固定：
- capslock + t = OnTogglePinOnTopPress()  一直让应用窗口保持在最前。
- capslock + a = OnTogglePinAppPress()    让应用固定显示在任务栏上。解决的问题：windows的默认情况，下一个桌面的任务栏不能显示其他桌面的打开应用的情况。比如上个桌面打开了chrome，其他桌面无法获知。
- capslock + w = OnTogglePinWindowPress()  让应用的窗口，随着桌面的切换，总是保持状态。

> 注意，固定的功能带有windows的通知。通过ahk的traytip触发的windows10的 toast通知，包含弹出式的和侧边栏的。
  其中需要注意的是。windows10 focus assist模式（专注模式）下，能导致弹出式失效。如果发现没有弹出框。记得关闭。

快捷键传输此应用到指定虚拟桌面：
- ~~shift + CapsLock + s = MoveCurrentWindowToDesktop(1)~~
- ~~shift + CapsLock + d = MoveCurrentWindowToDesktop(2)~~
- ~~shift + CapsLock + f = MoveCurrentWindowToDesktop(3)~~
- ~~shift + CapsLock + e = MoveCurrentWindowToDesktop(4)~~
- caps + s = MoveCurrentWindowToDesktop(1)
- caps + d = MoveCurrentWindowToDesktop(1)
- caps + f = MoveCurrentWindowToDesktop(1)
- caps + e = MoveCurrentWindowToDesktop(1)

背景跟随桌面切换：

当所有桌面没有打开内容的时候，通过快速切换，有时候，不知道自己到底处于哪个桌面。于是采用这种不同桌面可以定义背景的形式，来标记。同时也有一定的美观作用。
默认功能关闭。
可以通过
1. desktop_switcher.ahk:16  AutoAssociateBackgroundWithDesktop 变成true
2. 配置BackgroundPicPaths,数组的每一位代表了桌面的对应壁纸。
