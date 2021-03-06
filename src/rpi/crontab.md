# 使用crontab

## 一、配置crontab

进入corntab配置文件：

```bash
crontab -e
```

如果你是第一次使用，crontab可能需要你选择默认的编辑器，这边我一般会选择vim作为我的编辑器，因此输入2：

```
Select an editor.  To change later, run 'select-editor'.
  1. /bin/nano        <---- easiest
  2. /usr/bin/vim.basic
  3. /usr/bin/vim.tiny
  4. /bin/ed
```

你也可以在后面更改默认的编辑器：

```bash
select-editor
```

默认编辑器选择完后就会进入编辑界面，在文件末尾添加以下内容：

```
30 23 * * 0-5 sudo /usr/sbin/shutdown -h now

@reboot gpio mode 15 out && gpio write 15 1
@reboot /usr/local/bin/clash
@reboot sleep 10 && /home/pi/Projects/Autologin/autologin.sh
```

查看已有任务：

```bash
crontab -l
```

## 二、contab语法

基本格式：

```
* * * * * [username] command(s)
- - - - -
| | | | |
| | | | ----- Day of week  (0 - 7) (Sunday=0 or 7)
| | | ------- Month        (1 - 12)
| | --------- Day of month (1 - 31)
| ----------- Hour         (0 - 23)
------------- Minute       (0 - 59)
```

部分符号含义：

|  符号   |   含义   |
| :-----: | :------: |
|    *    |  任意值  |
|    ,    |  分割符  |
|    -    |  范围符  |
|    /    |  步数符  |
| @reboot | 启动事件 |

```admonish info
crontab在线编辑器：[crontab.guru](https://crontab.guru)
```

## 三、示例

```
* */2 * * * root apt-get update && apt-get upgrade -y
```

每两小时自动更新apt。

```
30 23 * * 0-5 sudo /usr/sbin/shutdown -h now
```

周日到周五晚23:30自动关机，即跳过星期六。

```
@reboot gpio mode 15 out && gpio write 15 1
```

开机自动调用wiringpi打开风扇。
