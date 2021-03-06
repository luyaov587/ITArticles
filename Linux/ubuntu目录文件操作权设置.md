#ubuntu目录文件操作权设置

chmod是用来改变文件或目录权限的命令，但只有文件的属主和超级权限用户root才 有这种权限。通过chmod来改变文件或目录的权限有两种方法：一种是通过八进制的语法，另一种是通过助记语法。

##助记语法设置文件权限

chmod的主机语法相对简单，对文件或目录的权限改变时，是通过比较直观的字符形式来 完成。在助记语法中，相关字母的定义如下。

用户或用户组定义

    u:代表属主；
    g:代表属组；
    o:代表其他用户；
    a:代表属主、数组和其他用户，也就是上面三个用户（或组）的所有。

权限定义

    r:代表读权；
    w:代表写权；
    x:代表执行权。

权限增减字符

    -:代表减去相关权限；
    +:代表增加相关权限。

用助记语法比较灵活，组合起来比较方便，比如：

- u=r+x 为文件属主添加读、写权限；
- ug=rwx, o-r 为属主和属组添加读、写、执行权限，为其他用户设置读权限；
- a+x 为文件的属主、属组和其他用户添加执行权限；
- g=u 让文件的属组和属主的权限相同。 

##八进制表示法设置权限

八进制语法的数字说明

| 单个权限 |	对应八进制数字 |
|---------|---------------|
|R	      |4              |
|W        |	2             |
|X	      | 1             |
|-	      | 0             |

然后再把相应权限的数值相加，得到一个组的权限描述。因为一个文件包括三 个权限 组，所以对于一个文件的权限描述来说，八进制描述包括从0到7的数字，这三个数值分别对应属主、属组和其他用户的权限描述，比如文件的权限位rwxr- xr-x，对应的八进制描述如下： 

- 属主的权限用数字表达：属主的权限是rwx，也就是4+2+1，应该是7；
- 属组的权限用数字表达：属组的权限是r-x，也就是4+0+1，应该是5；
- 其他用户的权限数字表达：其他用户权限是t-x，也就是4+0+1，应该是5。

所以整个文件的权限用八进制描述就是755。 

##语法

    usr@ubuntu:~$ chmod [权限八进制数值] [文件或目录名 称]

从上面的分析可以看出，每三位的权限代码（分别是属主、属组和其他用户）组合，有8种可 能，如下表所示。
 
组权限与八进制数值的映射关系

|八进制数值	| 三位组合权限|
|-----------|------------|
|0	        | —          |
|1          |	–x       |
|2          |	-w-      |
|3          |	-wx      |
|4          |	r–       |
|5          |	r-x      |
|6          |	rw-      |
|7	        | rwx        |
