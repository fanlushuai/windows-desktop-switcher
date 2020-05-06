# 完美使用windows桌面。
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

## 使用：
1. cd /xxxxx/你的软件安装目录。git clone https://github.com/fanlushuai/windows-desktop-switcher.git
2. 安装[ahk](https://www.autohotkey.com/)
3. 安装[strokens Plus](https://www.strokesplus.com/downloads/)
4. 配置ahk脚本开机启动
- Press Win + R, enter shell:startup, then click OK
- Create a shortcut to the desktop_switcher.ahk file here
5. 启动strokens Plus导入本项目的strokens plus配置文件。strokens-plus-config.spactions

