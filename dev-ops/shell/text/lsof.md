## lsof

list open file 

文件是系统对输入输出设备的抽象，例如socket, 文件系统，standard io 都是文件，每个被进程打开的文件都包含一个特定的文件描述符，通过lsof,我们可以通过进程或打开的文件追溯相关信息

* lsof -i 查看被打开的socket文件，根据条件(协议，端口，ip等）进行查询
    * lsof -i:3306 查看端口为3306的socket及其进程
    * lsof -i tcp 查看协议为tcp的socket及其进程

* lsof | grep [文件名] 
    * 根据文件名查找打开该文件的进程

* lsof -p [进程名]
    * 根据进程名，查看该进程打开的所有文件
    * 通常一个进程会打开多个文件，至少包括一个标准的输入和输出

