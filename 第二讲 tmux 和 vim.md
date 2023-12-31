### 第二讲 tmux 和 vim

#### **tmux** 

1. ##### 功能：

（1）分屏

（2）允许断开 Terminal 连接后，继续运行进程

2.  ##### 结构

（1）一个 tmux 可以包含多个 session，一个 session 可以包含多个 window，一个 window 可以包含多个 pane，实例：

```
tmux:
	session 0:
		window 0:
			pane 0
			pane 1
			pane 2
			...
		window 1
		window 2
	session 1
	session 2
	...
```

3.  ##### 操作

（1）`tmux`：新建一个 session，其中包含一个 window，window 中包含一个 pane，pane 里打开了一个 shell 对话框

（2）按下 `Ctrl + a` 后手指松开，然后按 `%`：将当前 pane 左右平分成两个 pane

（3）按下 `Ctrl + a` 后手指松开，然后按 `"`（注意是双引号）：将当前 pane 上下平分成两个 pane

（4）`Ctrl + d`：关闭当前 pane，如果当前 window 的所有 pane 均已关闭，则自动关闭 window ；如果当前 session 的所有 window 均已关闭，则自动关闭 session

（5）鼠标点击可以选 pane

（6）按下 `Ctrl + a` 后手指松开，然后按方向键：选择相邻的 pane

（7）鼠标拖动 pane 之间的分割线：可以调整分割线的位置

（8）按住 `Ctrl + a` 的同时按方向键，可以调整 pane 之间分割线的位置

（9）按下 `Ctrl + a` 后手指松开，然后按 `z`：将当前 pane 分屏/取消分屏

（10）按下 `Ctrl + a` 后手指松开，然后按 `d`：挂起当前 session

（11）`tmux a`：打开之前挂起的 session

（12）按下 `Ctrl + a` 后手指松开，然后按 `s`：选择其他 session

	方向键 上：选择上一项 session/window/pane
	
	方向键 下：选择下一项 session/window/pane
	
	方向键 右：展开当前项 session/window
	
	方向键 左：闭合当前项 session/window

（13）按下 `Ctrl + a` 后手指松开，然后按 `c`：在当前 session 中创建一个新的 window

（14）按下 `Ctrl + a` 后手指松开，然后按 `w`：选择其他 window，操作方法同（12）

（15）按下 `Ctrl + a` 后手指松开，然后按 `PageUp`：翻阅当前 pane 内的内容

（16）鼠标滚轮：翻阅当前 pane 内的内容

（17）在 tmux 中选中文本时，需要按住 `shift` 键

（18）tmux 中复制/粘贴文本的通用方式：

	① 按下 `Ctrl + a` 后松开手指，然后按 `[`
	
	② 用鼠标选中文本，被选中的文本会被自动复制到 tmux 的剪切板
	
	③ 按下 `Ctrl + a` 后松开手指，然后按 **]**，会将剪贴板中的内容粘贴到光标处

#### **vim**

1. ##### 功能

（1）命令行模式下的文本编辑器

（2）根据文件扩展名自动判别编程语言，支持代码缩进、代码高亮功能

（3）使用方式：`vim filename`

	① 如果已有该文件，则打开它
	
	② 如果没有该文件，则打开一个新的文件，并命名为 filename

2. ##### 模式

（1）一般命令模式

	默认模式。命令输入方式：按不同字符，可进行不同操作。可以复制、粘贴、删除文本等

（2）编辑模式

	在一般命令模式里按下 `I`，会进入编辑模式
	
	按下 `ESC` 会退出编辑模式，返回到一般命令模式

（3）命令行模式

	在一般命令模式里按下 `: / ?` 三个字符中的任意一个，会进入命令行模式，命令行在最下面。可以查找、替换、保存、退出、配置编辑器等

3. ##### 操作

（1）`i`：进入编辑模式

（2）`ESC`：进入一般命令模式

（3）`h 或 左箭头键`：光标向左移动一个字符

（4）`j 或 下箭头键`：光标向下移动一个字符

（5）`k 或 上箭头键`：光标向上移动一个字符

（6）`l 或 右箭头键`：光标向右移动一个字符

（7）`n + 空格`：$n$ 表示数字，按下数字后再按空格，光标会向右移动这一行的 $n$ 个字符

（8）`0 或 功能键 [Home]`：光标移动到本行开头

（9）`$ 或 功能键 [End]`：光标移动到本行末尾

（10）`G`：光标移动到最后一行

（11）`:n 或 nG`：$n$ 为数字，光标移动到第 $n$ 行

（12）`gg`：光标移动到第一行，相当于 `1G`

（13）`n + 回车`：**n** 为数字，光标向下移动 **n** 行

（14）`/word`：向光标之下寻找第一个值为 word 的字符串

（15）`?word`：向光标之上寻找第一个值为 word 的字符串

（16）`n`：重复前一个查找操作

（17）`N`：反向重复前一个查找操作

（18）`:n1,n2s/word1/word2/g`：n1 与 n2 为数字，在第 n1 行与 n2 行之间需找 word1 这个字符串，并将该字符串替换为 word2

（19）`:1,$s/word1/word2/g`：将全文的 word1 替换为 word2

（20）`:1,$s/word1/word2/gc`：将全文的 word1 替换为 word2，且在替换前要求用户确认

（21）`v`：选中文本

（22）`d`：删除选中的文本（相当于剪切）

（23）`dd`：删除当前行（相当于剪切）

（24）`y`：复制选择的文本

（25）`yy`：复制当前行

（26）`p`：将复制的数据在光标的下一行/下一个位置粘贴

（27）`u`：撤销

（28）`Ctrl + r`：取消撤销

（29）`>`：将选中的文本整体向右缩进一次

（30）`<`：将选中的文本整体向左缩进一次

（31）`:w`：保存

（32）`:w!`：强制保存

（33）`:q`：退出

（34）`:q!`：强制退出

（35）`:wq`：保存并退出

（36）`:set paste`：设置成粘贴模式，取消代码自动缩进

（37）`:set nopaste`：取消粘贴模式，开启代码自动缩进

（38）`:set nu`：显示行号

（39）`:set nonu`：隐藏行号

（40）`gg=G`：将全文代码格式化

（41）`:noh`：关闭查找关键词高亮

（42）`Ctrl + q`：当 vim 卡死时，可以取消当前正在执行的命令

4. ##### 异常处理

	每次用 vim 编辑文件时，会自动创建一个 `.filename.swp` 的临时文件

	如果打开某个文件时，该文件的 `swp` 文件已存在，则会报错。此时解决办法有两种：

	① 找到正在打开该文件的程序，并退出

	② 直接删掉 `swp` 文件即可

#### **作业**

（1）进入 homework_0 文件夹，创建文件 names.txt，并顺次将下列姓名写入该文件，每个名字占一行。AcWing、yxc、Bob、张强、李明、Alice

```shell
cd homework_0
vim names.txt
i（进入编辑模式）
依次输入各个单词
ESC（返回一般命令模式）
:wq<Enter>（保存并退出）
```

（2）进入 homework_1 文件夹，打开 problem.txt，并依次删除下列字符：
    [1] 最后一行第101个字符
    [2] 第3行第8个字符
    [3] 第1行第30个字符
    [4] 第16行第55个字符
    [5] 第9行第80个字符
    最后保存文件并退出。

```shell
cd homework_1
vim problem.txt
[1] G（跳转到最后一行）101<Space>（第101个字符）i（进入编辑模式）<Backspace>（删除）<ESC>（返回一般命令模式）
[2] 3G（跳转到第3行）8<Space>（第8个字符）i（进入编辑模式）<Backspace>（删除）<Esc>（返回一般命令模式）
[3] gg（跳转到第1行）30<Space>（第30个字符）i（进入编辑模式）<Backspace>（删除）<Esc>（返回一般命令模式）
[4] :16<Enter>（跳转到第16行）55<Space>（第55个字符）i（进入编辑模式）<Backspace>（删除）<ESc>（返回一般命令模式）
[5] 9G（跳转到第9行）80<Space>（第80个字符）i（进入编辑模式）<Backspace>（删除）<Esc>（返回一般命令模式）
:wq<Enter>（保存并退出）
```

（3）进入 homework_2 文件夹，打开 problem.txt，并依次执行如下操作：
    [1] 在第1个 "two" 的后面添加 "abc"
    [2] 在第2个 "two" 的前面添加 "def"
    [3] 将第3个 "two" 后面的连续 12 个字符删掉
    [4] 将第4个 "two" 所在的行删掉
    最后保存文件并退出。

```shell
cd homework_2
vim problem.txt
[1] /two<Enter>（查找第一个two）i（进入编辑模式）在后面添加"abc"<Esc>（返回一般命令模式）
[2] n（重复前一个查询操作）i（进入编辑模式）在前面添加"def"<Esc>（返回一般命令模式）
[3] n（重复前一个查询操作）i（进入编辑模式）用<del>删除12个字符<Esc>（返回一般命令模式）
[4] n（重复前一个查询操作）dd（删除所在的行）
:wq<Enter>（保存并退出）
```

（4）进入 homework_3 文件夹，打开 problem.txt，并依次执行如下操作：
    [1] 将第 5 行至第 15 行中所有 of 替换成 OF
    [2] 将全文中所有的 the 替换成 THE
    [3] 将第偶数个 is 替换成 IS，第奇数个 is 不变。下标从 1 开始

```shell
cd homework_3
vim problem.txt
[1] :5,15s/of/OF/g（替换5到15行的of为OF）
[2] :1,$s/the/THE/g（替换全文的the为THE）
[3] :1,$s/is/IS/gc（手动控制将第偶数个is替换为IS，第奇数个is不替换）
:wq<Enter>（保存并退出）
```

（5）进入 homework_4 文件夹，打开 problem.txt，并依次执行如下操作：
    [1] 删除第 11 行
    [2] 将所删除的行粘贴到文件最后一行的下一行
    [3] 复制第 5 行
    [4] 将所复制的行粘贴到文件当前最后一行的下一行

```shell
cd homework_4
vim problem.txt
[1] 11G（跳转到第11行）dd（删除所在行）
[2] G（跳转到最后一行）p（将复制数据粘贴到下一行）
[3] 5G（跳转到第5行）yy（复制当前行）
[4] G（跳转到最后一行）p（将复制数据粘贴到下一行）
:wq<Enter>（保存并退出）
```

（6）进入 homework_5 文件夹，打开 problem.txt，并依次执行如下操作：
    [1] 删除第 11 行第 15 个字符（包含该字符）至第 13 行第 5 个字符（包含该字符）
    [2] 将所删除的内容粘贴到文件末尾（注意不要另起一行）
    [3] 复制第 5 行第 88 个字符（包含该字符）至第 7 行第 6 个字符（包含该字符）
    [4] 将所复制的内容粘贴到当前文件末尾（注意不要另起一行）

```shell
cd homework_5
vim problem.txt
[1] 11G（跳转到第11行）14<Space>（第14个字符，注意是第15个字符的前一个字符）v（选中）13G（跳转到第13行）5<Space>（第5个字符）d（删除所选文本）
[2] G（跳转到最后一行）$（光标移到本行末尾）p（将复制数据粘贴到下一个位置）
[3] 5G（跳转到第5行）87<Space>（第87个字符，注意是第88个字符的前一个字符）v（选中）7G（跳转到第7行）6<Space>（第6个字符）y（复制所选文本）
[4] G（跳转到最后一行）$（光标移到本行末尾）p（将复制数据粘贴到下一个位置）
:wq<Enter>（保存并退出）
```

（7）进入 homework_6 文件夹，并依次执行如下操作：
    [1] 清空 source0.cpp
    [2] 将 source1.cpp 中的第 1-3 行和第 12-24 行复制到 source0.cpp 中

```shell
cd homework_6
vim source0.cpp
[1] gg（跳转到第一行）d（删除）G（到最后一行）
[2] Ctrl + a + " （在tmux中打开一个新的pane）
vim source1.cpp
:set nonu （取消行号）
Ctrl + a + z （将sourcce1.cpp所在pane全屏）
Shift 鼠标选择前3行
Ctrl + Insert （复制选中内容）
Ctrl + a + z （取消sourcce1.cpp所在pane全屏）
鼠标选择source0.cpp所在pane
:set paste （进入粘贴模式）
i （进入编辑模式）
Shift + Insert（粘贴内容）
同理操作source1.cpp的第12-24行
:wq<Enter>（保存并退出source0.cpp）
:wq<Enter>（保存并退出source1.cpp）
```

（8）进入 homework_7 文件夹，格式化 source.cpp

```shell
cd homework_7
vim source.cpp
gg（跳转到第一行）=（格式化）G（到最后一行）
:wq<Enter>（保存并退出）
```

（9）进入 homework_8 文件夹，打开 source.cpp，并依次执行如下操作：
    [1] 将第 15-21 行向右缩进 2 次
    [2] 将第 22-23 行向左缩进 1 次

```shell
cd homework_8
vim source.cpp
[1] 15G（跳转到第15行）v（选中）21G（到第21行）
>（向右缩进一次）
同理再缩进一次
[2] 22G（跳转到第22行）v（选中）23G（到第23行）
<（向左缩进一次）
:wq<Enter>（保存并退出）
```

（10）进入homework_9文件夹，打开链接：[A + B](https://www.acwing.com/activity/content/code/content/1694465/)，新建文件source.cpp，将链接中的代码抄进source.cpp文件中。

```shell
cd homework_9
vim source.cpp
打开链接，Ctrl + Insert 复制
Shift + Insert（粘贴内容到source.cpp）
:wq<Enter>（保存并退出）
```