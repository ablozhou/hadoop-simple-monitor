# author: Zhou Haihan
# web: http://abloz.com
# date: 2012.8.22
# email: ablozhou@gmail.com
# Release SMR 1.0
# Simple Monitor for Hadoop Processes, Memory and Diskspace usage. 

# Provided as-is; use at your own risk; no warranty; no promises; enjoy!
# Copyright (c) 2013-2015 by Andy Zhou.

用于监控hadoop系统各主机状态，如内存占用，硬盘占用，进程是否存在。如果达到一定阈值则发送email告警。

下载地址：https://code.google.com/p/hadoop-simple-monitor/

==特点：==
  # 很简单的用于监控Hadoop各节点状况，包括内存占用情况，硬盘占用情况，进程是否存在等。如果出问题将发送email告警。
  # 部署非常简单。只需下载或解压到一台机器上，配置完毕，即可监控所有节点。不需到远程去部署。
  # 用Bash脚本写成，方便修改
  # 用于监控Java(Hadoop相关的，如HBase，Thrift，Hadoop )进程。也可监控其他进程，需少量修改。

==部署:==
  # 下载解压到一台机器上，远程监控的机器不需要下载和配置
  # 配置config.sh,设置好要监控哪些机器，哪些进程
  # 修改loopcheck.sh, 设置好路径，该文件供crontab使用。
  # 可以测试一下邮件发送是否正常
  # 添加到crontab，如5分钟运行一次

0-59/5 `*` `*` `*` `*`     $HOME/smr/loopcheck.sh

----
Simple Monitor for Hadoop Processes, Memory and Diskspace usage. If memory and disk usage reaches to a threshold, or some hadoop system process exit, the program will send email to make warnings.

==Features:==
  # Simple Monitor  Hadoop Processes, Memory and Diskspace usage of every hosts that configured.
  # Deploy is simple. Just copy or uncompress the code to one station, and it can monitor each remote hosts.
  # Write by Bash script, It's easy to modify.
  # It can monitor java processes(Such as HBase,Thrift,Hadoop processes) or other processes(need a little change)


==Deploy:==
Just copy or uncompress the code to a directory, configured to monitor all remote hosts, the remote hosts needn't any configure or   deploy.

  # modify config.sh to configure parameters
  # check loopcheck.sh to modify paths, because crontab has a limited env and PATH
  # check email sending is ok or not, you may need configure MTA such as Postfix
  # configure crontab, every 5 minutes check the hosts

#0-59/5 `*` `*` `*` `*`     $HOME/smr/loopcheck.sh
0-59/5 * * * *     $HOME/smr/loopcheck.sh

To test email:

And uncomment EMAIL="Zhouhh@aaa.com,zhouhh@bbb.com" of sendmail.sh, modify to your email address 

for test email sending, edit a email, save as emailbody.txt,run
./sendmail.sh  emailbody.txt

