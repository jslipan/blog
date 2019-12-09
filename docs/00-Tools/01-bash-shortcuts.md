生活在 Bash shell 中，熟记以下快捷键，将极大的提高你的命令行操作效率。

### 编辑命令 ###
```cmd
Ctrl + a ：移到命令行首
Ctrl + e ：移到命令行尾
Ctrl + f ：按字符前移（右向）
Ctrl + b ：按字符后移（左向）
Alt + f ：按单词前移（右向）
Alt + b ：按单词后移（左向）
Ctrl + xx：在命令行首和光标之间移动
Ctrl + u ：从光标处删除至命令行首
Ctrl + k ：从光标处删除至命令行尾
Ctrl + w ：从光标处删除至字首
Alt + d ：从光标处删除至字尾
Ctrl + d ：删除光标处的字符
Ctrl + h ：删除光标前的字符
Ctrl + y ：粘贴至光标后
Alt + c ：从光标处更改为首字母大写的单词
Alt + u ：从光标处更改为全部大写的单词
Alt + l ：从光标处更改为全部小写的单词
Ctrl + t ：交换光标处和之前的字符
Alt + t ：交换光标处和之前的单词
Alt + Backspace：与 Ctrl + w ~~相同~~类似，分隔符有些差别 [感谢rezilla 指正]
```
### 重新执行命令 ###
```cmd
Ctrl + r：逆向搜索命令历史
Ctrl + g：从历史搜索模式退出
Ctrl + p：历史中的上一条命令
Ctrl + n：历史中的下一条命令
Alt + .：使用上一条命令的最后一个参数
```
### 控制命令 ###
```cmd
Ctrl + l：清屏
Ctrl + o：执行当前命令，并选择上一条命令
Ctrl + s：阻止屏幕输出
Ctrl + q：允许屏幕输出
Ctrl + c：终止命令
Ctrl + z：挂起命令
```
### Bang (!) 命令 ###
```cmd
!!：执行上一条命令
!blah：执行最近的以 blah 开头的命令，如 !ls
!blah:p：仅打印输出，而不执行
!$：上一条命令的最后一个参数，与 Alt + . 相同
!$:p：打印输出 !$ 的内容
!*：上一条命令的所有参数
!\*:p：打印输出 !* 的内容
^blah：删除上一条命令中的 blah
^blah^foo：将上一条命令中的 blah 替换为 foo
^blah^foo^：将上一条命令中所有的 blah 都替换为 foo
```
\_友情提示\_：

1. 以上介绍的大多数 Bash 快捷键仅当在 emacs 编辑模式时有效，若你将 Bash 配置为 vi 编辑模式，那将遵循 vi 的按键绑定。Bash 默认为 emacs 编辑模式。如果你的 Bash 不在 emacs 编辑模式，可通过 `set -o emacs` 设置。

2. `^S、^Q、^C、^Z` 是由终端设备处理的，可用 `stty` 命令设置。


### vim操作

```bash
# 光标定位
hjkl  #上下左右
0 $   #行首行尾
gg  G   #页首页尾
3G  #进入第三行
/string   #查找字符，n下一个 （n N可以循环）

# 文本编辑
a i o  #插入模式
R  #替换模式

#替换  :范围 s/old/new/选项
:1,5 s/root/yang/   #从1-5行的root替换为yang

#读写文件
:w   #存储到当前文件
:w /tmp/aa.txt   #另存为/tmp/aa.txt
:1,3 w /tmp/2.txt
:r /etc/hosts  #读入文件到当前行后
:5 r /etc/hosts  #读入文件到第5行后

#设置环境
:set nu  #设置行号
:set ic  #不区分大小写
:set ai  #自动缩进
:set list  #显示控制字符
:set nonu  #取消设置行号
```
