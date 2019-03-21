# Visual Studio Remote Debug

1. clone仓库到本地，打开vs解决方案。

2. 执行命令`docker-compose up`。

3. 在菜单栏中，选择调试->附加到进程。

![menu](https://github.com/w12379564/dev_demo_vs/blob/master/images/menu.png)

4. 连接类型选择`SSH`，连接目标输入`root@localhost`，Enter。

![ssh](https://github.com/w12379564/dev_demo_vs/blob/master/images/ssh.png)

5. 在弹出窗口中输入SSH登录信息，端口2222，密码[screencast](https://github.com/w12379564/dev_demo_vs/blob/master/postsvr_vs/Dockerfile#L19)。

![conn](https://github.com/w12379564/dev_demo_vs/blob/master/images/conn.png)

6. 附加到选中进程。

![attach](https://github.com/w12379564/dev_demo_vs/blob/master/images/attach.png)

7. 选择gdb调试。

![gdb](https://github.com/w12379564/dev_demo_vs/blob/master/images/gdb.png)
