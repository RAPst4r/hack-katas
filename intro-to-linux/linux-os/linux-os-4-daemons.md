Pronounced “Day-mens”, this part of the OS is another name for processes that run in the background. For example, when you login or when you send a print command, the login or printing service is run as a daemon.  

In Linux, we can see the list of processes that are running by using the `ps -ef`{{execute}} command. Each process has a unique identifier called PID which standards for Process IDentifier.  

One of the most important processes in Linux is the `init` process, which can be thought of as the grandfather of all processes, because every other process that runs, except the kernel, is a child of this `init` process and can be traced back to `init`. The kernel itself runs in PID 0 while the `init` process has a PID of 1.  

Technically, a daemon is a parent process that is started when the Operating System boots is initialized and boots up. So daemons are configured to run from `/etc/initd` where `initd` stands for initial daemons. This means that they usually have a PPID (Parent Process IDentifier) of 1. So we can look for all processes and search for the pattern where the PPID is equal to 1 to find daemons.  

Type `ps -ef | awk '$3 == 1'`{{execute}} and enter.  
When you run the `ps -ef` command, you see that all processes are standard output to your display as shown below. The 2nd column shows the Process ID (PID) and the 3rd Column shows the Parent PID. So the `awk` command here takes the 3rd column (denoted by $3) and checks to see if the PPID is equal (==) 1, which is the PPID for daemons.  
`root       285     1  0 20:39 ?        00:00:00 /lib/systemd/systemd-udevd
root       749     1  0 20:39 ?        00:00:00 /usr/lib/accountsservice/accounts-daemon
root       766     1  0 20:39 ?        00:00:00 /usr/sbin/cron -f
root       768     1  0 20:39 ?        00:00:00 /lib/systemd/systemd-logind
syslog     777     1  0 20:39 ?        00:00:00 /usr/sbin/rsyslogd -n
root       908     1  0 20:39 ?        00:00:02 /usr/bin/containerd
root       959     1  0 20:39 ?        00:00:01 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock
root       960     1  0 20:39 ?        00:00:00 /usr/sbin/sshd -D
root      4599     1  0 22:30 ?        00:00:00 /lib/systemd/systemd --user`  
