
# 1、命令补全（Command-Line Completion）

在 Bash（或任何其他的 Shell）下输入命令时你不必把命令输全，按下 Tab 键， Bash Shell 就能自动补全你所要输入的命令。
```bash
pw<tab>  # 输入pw之后按下<Tab>，自动补全为 pwd 
```

# 2、通配符

字符含义
- `*`：匹配 0 或多个字符
- `?`：匹配任意一个字符
- `[…]`：匹配任何包含在括号里的单字符

```bash
pw*  # 输入pw之后输入*，自动把 pw* 替换为 pwd 
```

# 3、命令历史记录

Bash Shell 也支持命令历史记录。这意味着 Bash 保留了一定数目的你先前已经在 Shell 里输入过的命令。Bash 把先前输入的命令文本保存在一个历史列表中。当你用你的帐号登录后历史列表将根据一个历史文件被初始化。历史文件的文件名被一个叫 HISTFILE 的 Bash 变量指定。历史文件的缺省名字是 .bash_history 。这个文件通常在你的用户目录($HOME)中。

使用历史记录列表最简单的方法是用 上方向键（↑）。按下上方向键后最后键入的命令将出现在命令行上，再按一下则倒数第二条命令会出现，以此类推。如果上翻多了的话也可以用向下的方向键来下翻。如果需要的话，显示在命令行上的历史命令可以被编辑。

# 4、重定向

Linux Shell 重定向分为两种，一种输入重定向，一种是输出重定向；从字面上理解，输入输出重定向就是改变输入与输出的方向的意思。

输入输出方向就是数据的流动方向：

输入方向就是数据从哪里流向程序。数据默认从键盘流向程序，如果改变了它的方向，数据就从其它地方流入，这就是输入重定向。
输出方向就是数据从程序流向哪里。数据默认从程序流向显示器，如果改变了它的方向，数据就流向其它地方，这就是输出重定向。
输出重定向

输出重定向是指命令的结果不再输出到显示器上，而是输出到其它地方，一般是文件中。这样做的最大好处就是把命令的结果保存起来，当我们需要的时候可以随时查询。此外，输出重定向可以用于把一个命令的输出当作另一个命令的输入时。输出重定向的符号是 > 。

        重定向举例，当你要把 ls 命令的输出保存为一个名为 1.out 的文件时，你可以使用下面的命令：

ls > 1.out
1
输入重定向
        输入重定向就是改变输入的方向，不再使用键盘作为命令输入的来源，而是使用文件作为命令的输入。输入重定向的使用与输出重定向很相似，但是输出重定向的符号是 < 。

5、管道

        管道可以把一系列命令连接起来。这意味着第一个命令的输出会通过管道传给第二个命令而作为第二个命令的输入，第二个命令的输出又会作为第三个命令的输入，以此类推。而管道行中最后一个命令的输出才会显示在屏幕上（如果命令行里使用了输出重定向的话，将会放进一个文件里）。

6、提示符

        Bash 有两级用户提示符。第一级是你经常看到的 Bash 在等待命令输入时的提示符。缺省的一级提示符是字符$（如果是超级用户，则是#号）。

7、作业控制（Job Control）

        作业控制能够控制当前正在运行的进程的行为。特别地，你能把一个正在运行的进程挂起，稍后再恢复它的运行。Bash 保持对所有已启动的进程的跟踪，你能在一个正在运行的进程的生命期内的任何时候把它挂起或是使它恢复运行。

        按下 Ctrl-Z 使一个运行的进程挂起。bg 命令使一个被挂起的进程在后台恢复运行，反之 fg 命令使进程在前台恢复运行。这几个命令在当用户想在后台运行而意外的把它放到了前台时，经常被用到。当一个命令在前台被运行时，它会禁止用户与 Shell 的交互，直到该命令结束。这通常不会造成麻烦，因为大多数命令很快就执行完了。如果你要运行的命令要花费很长的时间的话，我们通常会把它放到后台，以使我们能在前台继续输入其他命令。

8、 用户化配置bash

        把任何想每次进入 Bash 都执行的命令放到初始化文件里。Bash 的初始化文件叫做 profile。每个使用 Bash 的用户都有一个 .profile 文件在他的用户目录里（也可能是.bash_profile）。Bash在每次启动时都读取这个文件，并执行所有包含的命令。启动 Bash 时会读取指定的配置文件，以规划 Bash 的工作环境。

系统配置文件，设置所有用户的环境
/etc/profile

/etc/profile		# 一般来说设置的变量主要有以下
PATH  				# 根据用户标识符（UID）决定要不要将系统命令目录/sbin加入到PATH
MAIL  				# 根据账号设置mailbox->/var/spool/mail/账号
HISTSIZE  			# 历史命令记录条数, 一般为1000
USER
HOSTNAME

# 调用的外部数据
/ert/profile.d/*.sh, 并且具有r权限, 则会被/etc/profile调用
# 这个目录指定了操作接口的颜色, 命令的别名等, 可自行新建sh文件并设置一些共享的命令别名
1
2
3
4
5
6
7
8
9
10
11
12
用户配置文件，即个人设置文件
 ~/.bash_profile
 ~/.bash_login
 ~/.profile

# 调用的外部数据
~/.bashrc
/etc/bashrc
1
2
3
4
5
6
7
读取配置文件
        修改完配置文件后，需要在下次登录后才能生效，可利用如下命令重新读取配置文件
source ~/.bashrc
. ~/.bashrc
————————————————
版权声明：本文为CSDN博主「长路漫漫2021」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/xq151750111/article/details/114491731