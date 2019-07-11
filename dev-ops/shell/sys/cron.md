## 定时任务

### 基本用法

* crontab -l 查看
* crontab -e 编辑
* crontab task.cron 添加定时任务，从文件中读取

### 时间格式

* 分钟/小时/天/月份/工作日 + 命令, 工作日可省略
* 通配符 * 表示每x, 例如 * / 5 每5分钟

```
#每小时清空一次回收站
0 * * * * rm -rf /root/Trash/*

#每天5，6，7点执行一次脚本
00 5,6,7 * * /home/test.sh

```




