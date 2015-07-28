用于监控hadoop系统各主机状态，如内存占用，硬盘占用，进程是否存在。如果达到一定阈值或进程退出则发送email告警。

下载地址：https://code.google.com/p/hadoop-simple-monitor/

## 特点： ##
  1. 很简单的用于监控Hadoop各节点状况，包括内存占用情况，硬盘占用情况，进程是否存在等。如果出问题将发送email告警。
  1. 部署非常简单。只需下载或解压到一台机器上，配置完毕，即可监控所有节点。不需到远程去部署。
  1. 用Bash脚本写成，方便修改
  1. 用于监控Java(Hadoop相关的，如HBase，Thrift，Hadoop, ZooKeeper, Hive, Pig等 )进程。也可监控其他进程，需少量修改。

## 部署: ##
  1. 下载解压到一台机器上，远程监控的机器不需要下载和配置
  1. 配置config.sh,设置好要监控哪些机器，哪些进程
  1. 修改loopcheck.sh, 设置好路径，该文件供crontab使用。
  1. 可以测试一下邮件发送是否正常
  1. 添加到crontab，如5分钟运行一次

0-59/5 `*` `*` `*` `*`     $HOME/smr/loopcheck.sh

## 测试邮件发送 ##
  1. 编辑sendmail.sh
  1. 将EMAIL变量注释去掉,修改成自己的email
  1. 编辑邮件正文，保存到emailbody.txt
  1. 运行命令 ./sendmail.sh emailbody.txt


---

Simple Monitor for Hadoop Processes, Memory and Diskspace usage. If memory and disk usage reaches to a threshold, or some hadoop system process exit, the program will send email to make warnings.

## Features: ##
  1. Simple Monitor  Hadoop Processes, Memory and Diskspace usage of every hosts that configured.
  1. Deploy is simple. Just copy or uncompress the code to one station, and it can monitor each remote hosts.
  1. Write by Bash script, It's easy to modify.
  1. It can monitor java processes(Such as HBase,Thrift,Hadoop processes) or other processes(need a little change)


## Deploy: ##
Just copy or uncompress the code to a directory, configured to monitor all remote hosts, the remote hosts needn't any configure or   deploy.

  1. modify config.sh to configure parameters
  1. check loopcheck.sh to modify paths, because crontab has a limited env and PATH
  1. check email sending is ok or not, you may need configure MTA such as Postfix
  1. configure crontab, every 5 minutes check the hosts

0-59/5 `*` `*` `*` `*`     $HOME/smr/loopcheck.sh

## Test Email ##
And uncomment EMAIL="Zhouhh@aaa.com,zhouhh@bbb.com" of sendmail.sh, modify to your email address

for test email sending, edit a email, save as emailbody.txt,run
./sendmail.sh  emailbody.txt