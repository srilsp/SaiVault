20220824:
cat /etc/os-release [what system do I run]
cat /etc/*-release [what system do i run for all flavours of linux]
uname -r
echo $SHELL
grep ec2-user /etc/passwd
rpm -qa | grep httpd
systemctl status httpd
ldd `which cat`
who -r
systemctl get-default
systemctl isolate multi-user.target
sudo init {runtime level}
uptime
ps -ef | grep init
ps -ef | grep systemd
sudo su - {same as sudo -i}
yum install httpd
runlevel
chkconfig --list  {systemV only}
systemctl list unit-files
ps -ef | grep httpd
systemctl isolate multi-user.target
pwd
grep Password /etc/ssh/sshd_config | grep -v "#"  {-v means to omit any that has ""}
less /etc/ssh/sshd_config
ls -al | grep ssh     [ll or ll -a]
pwconv
/etc/sudoers.d  [is directory]
/etc/default.list
sudo visudo
-Defaults editor=/usr/bin/vi
yy [in vim editor yy copies, p for paste, x for delete]
usermod -aG sudo [username]
username  ALL=(ALL) NOPASSWD:ALL
curl http://privIP/latest/meta-data/instance-id
lsblk [list volumes]
fdisk -l [shows detailed drive]
fdisk /dev/xvdf [m for help and other commands]
[this command to find out format of drive]
mkfs --type ext4 /dev/xvdf1 [format the filesystem]
file -s /dev/xvdf1 [will show the type of filesystem being used]
mount /dev/xvdf1 /mnt
fdisk /disk/[namehere]
df -kh [to check if drive is mounted]
df -kh . [as above in current directory]
df [find available free space, -H for in MB]
umount /[directory]
cat /etc/fstab
blkid
vim /etc/fstab
UUID=c150e2d7-f235-4102-a8bc-19af615e4db7 /mnt  ext4  defaults,noatime,nofail  1  0  
automount drive - https://www.linuxbabe.com/desktop-linux/how-to-automount-file-systems-on-linux

which ls [mkdir, touch, ls, cat][find libraries\directories]
export PATH="[path]"
echo PATH="[path]"
du -sh [filename][usage in megabytes]
tree -L 1 / --inodes -I "proc|sys|dev"
stat
ln /home/ec2-user/testforlink kayshardlink  [link files]
stat [linkname]
rm [file/link]
ln -s test testsoftlink
chmod 777 [filename]
chmod u+rwx,g+rwx,o+r [filename]
ls -l or ls -al
lsof -p [id] [used to check what is open]
HEREDOC
ls -l | awk "{print $[column#]}'


attaching following command under vim /etc/fstab did not work and failed the restart checks - please get new one;
UUID="c150e2d7-f235-4102-a8bc-19af615e4db7" /mnt ext3 defaults 0 0
https://tldp.org/LDP/intro-linux/html/sect_03_01.html

SystemV:
chkconfig ntpupdate --level3 on^C
runlevel
service ntpupdate status
curl http:/IP
chkconfig --list

lscpu | grep -i svm 

cp /home/BSD.txt > /home/BSD_DELETE.txt [copy command]

2022-09-14
rpm -qa | grep ssh
yum list installed
yum list installed | grep which

https://tldp.org/LDP/Bash-Beginners-Guide/html/

egrep -i "^a" group^C
vi group
egrep "A" group
egrep -i "^a" group
egrep "A$" group
egrep "a." group
egrep ".a" group
egrep "!." group
egrep -i "a." group
egrep "a." group
egrep "+." group
egrep "a+" group
egrep "." group


sudo -i
ls
rpm -qlp [sysstat-2nd line atbottom of output]
rpm -qlp glibc-devel
rpm -qlp kernal

rm -Rf sysstat [remove everything recursively and force it to remove]
rmp2cpio ../sysstat-10.1.5-18.amzn2.0.1.x86_64.rpm | cpio -id
history | tail -5 [to run the last 5 commands]
man cpio
[tar -x = extract an archive & tar -c = create an archive]

rpm -qa | grep sysstat [yum is better to install packages as it also installs the dependencies]
rpm -i [sysstat-package]
rpm -e [to remove/uninstall the package]
dpkg [to list all dependencies for the package]  

yumdownloader --source [will download the source rpm]
yum.repos.
yum-config-manager epel | grep enabled [--enable/disable epel no grep at the end]

yum repolist
yumdownloader --source httpd
ls
rpm2cpio httpd-2.4.54-1.amzn2.src.rpm | cpio -id [Listing the files in a package file]
ls
[grep "^Requires" *.spec]

sudo yum install httpd
yum search atop
yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
sudo yum install atop
atop
top

which rpm ?????
rpm -qpR httpd httpd-2.4.54-1.amzn2.src.rpm

& [ send command in background]
$ bash <script name> & [to run a bash script]

Q ASKED IN INTERVIEW - WHAT IS THE RUNLEVEL
0. HALT
1. SINGLE USER
2. MULTI-USER - NO NETWORK
3. MUTLI-USER
4. NOT USED
5. GUI
6. REBOOT

./sshd help
cd ../rc3.d
sshd
sshd -l
../init.d/sshd stop
ls -l http
rpm -q httpd
rpm -q httpd
ls -l http
service httpd status
sudo service httpd status
sudo chkconfig --list httpd
sudo chkconfig httpd on
sudo chkconfig --list httpd

systemctl enable httpd
systemctl status httpd
systemctl start httpd

journalctl --file system.journal


issue with todays lab: [[https://helpdeskgeek.com/linux-tips/top-3-ways-to-fix-no-space-left-on-device-error-in-linux/](https://helpdeskgeek.com/linux-tips/top-3-ways-to-fix-no-space-left-on-device-error-in-linux/)]
	df -kh [no issues with available space]
	umask [no issues with permissions]
	df -i [identified inodes issue]
	ls -al [shows the hidden files - .directory0 is massive]

netstat -tulnpa
top
cat /etc/services | grep -i ssh
cat /etc/services | grep -i 443
yum whatprovides [command]
i.e. yum whatprovides lshw
ifconfig -a
lshw -C network
dmidecode [network traffic]
uuid - disc name
ss -tulnpa [port]
netstat -telpn | grep LISTEN
route or netstat -r 
traceroute
systemctl list-unit-files : grep -i Network
arp -an
arping  172.31.32.1
arping google.com
ping facebook.com

cat /var/lib/dhclient/dhclient--eth0.lease
cat /var/log/messages | grep DHCP
hostnamectl set-hostname testInstance-1
hostname

nslookup [domainname]
dig amazon.com +trace
host amazon.com

curl -Ivlk http://test101.xyz

iptables -L -v
iptables -A
iptables -D
iptables -F [remove all the rules]
iptables -A INPUT -p tcp --dport 443 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-requests -j REJECT
iptables -A OUTPUT -p icmp -j REJECT
nc
traceroute
tcpdump
mtr
h3ping [uses different protocols to icmp]
lperf [common for customer to use this]
sudo traceroute -T -p 22 -m 75 www.amazon.com
who am in
whois [ip]
nc -zv [ip] [port]
telnet
curl
loopback is 127.0.0.1
tcpdump -i eth0
tcpdump -i eth0 tcp port 22 -nn 
systemctl status httpd
ps -ef
runlevel
man runlevel
systemctl get-default
systemctl set-default multi-user.target

daemon [a program that runs in the background without requiring any user interaction.  The file name of a software daemon usually ends in the letter d i.e. systemd, sshd or httpd - service -->daemon-->process]
& [if you run a command and enter '&' it'll automatically run it to the background']

vim 'HelloWorld.sh' [to create a simple bash script as an application.  this one sends out the echo every 2 seconds]
#!/bin/bas
while true
do
		echo "Hello World!"
		sleep 2
done
chmond 700 helloWorld.sh
./helloWorld.sh
man nohop
nohup ./helloWorld.sh & [pushes the application to the background]
tail -f nohup.out [ will show the output from the application]
jobs [shows running jobs in background]
fg [will bring the running jobs or applications to the foreground]
ps -ef [process status ]
ps -A or ps -e [output all running processes at a glance]
ps -T [view processes associated with the terminal]
ps -a [view processes not associated with the terminal]
ps -ax [view all current processes]
pts [pseudo terminal slave]
ps -eo pid,user,ni,%cpu,comm | head [see the nice value per pid]
[it shows all processes -e Select all processes. Identical to -A. -f Do full-format listing. This option can be combined with many other UNIX-style options to add additional columns. It also causes the command arguments to be printed. When used with -L, the NLWP (number of threads) and LWP (thread ID) columns will be added. See the c option, the format keyword args, and the format keyword comm.]

pstree
process status in the man pages
D = uninterruptible sleep
O = idle
R  = Running
S = sleeping
t = stopped by job control signal
t = stopped by debugger
z = zombie
top  - in the info shown it will s is un-interruptable and i is interruptable

ls -lrth

yum whatprovides [command] used to find the packages/compilers
yum list kernal --showduplicates

nice -n -5 nohub sleep 300 &
ps -eo pid, user,ni,%cpu,comm | grep sleep
renice -n 5 -p [pid]
dmesg -T [systemd command need to remember for ]
cd /var/log/        
tail -f [shows the live update on the file]
tail -40 messages
cd audit/ [to enable audit logs]
ls -lrth 
tail audit.log
gcc test.c -o test
ls -lrth
ps -ef
pstree
./test
interupt means to interupt the process
ps -ef | grep test
ps -ef | grep testorphan [testorphan]

man kill
kill -l [shows all the processes/signals]
i.e. sigint, sigkill, sigstop, sigterm
kill [signal # that you can see in kill -l] [pid] [to stop a process] i.e. 
kill -9 -3794 [will stop process with pid 3794]
kill -1  [used to send different kind of kills]

kill -9 [pid] will shutdown the parent straight away but the child processes will shutdown later naturally
kill -15 [pid] will shutdown gracefully and the parent will tell the child process to shutdown which if that has a child process will issue the command down the line.

CPU monitoring:
top
lscpu
/proc/cpuinfo
sar
https://www.brendangregg.com/Perf/linux_observability_sar.png
sar -P all 
sar 2 5 [gives you a live details about how the cpu performance is]
dd if=/dev/urandom of=/dev/hull count=10
nohup [command i.e. the one above] &
https://aws.amazon.com/premiumsupport/knowledge-center/ec2-enable-epel/
sudo amazon-linux-extras install epel -y
yum install stress -y
sudo stress --cpu 8 --timeout 20 & [if cpu is maxed will affect performance, processing time, extra command execution]
sar 2
&& [will allow you to execute 2 commands on the same line between 2 commands, similar to the | symbol]

what not to use no nmap, sqlmap without authorization of customers

sudo stress --cpu 8 --timeout 100 &
pstree
ps -ef | grep xyz
lshw -u 
/proc/cpuinfo - important
lscpu - important

https://tldp.org/LDP/intro-linux/html/sect_03_01.html
/proc  \running processes
/etc     \
/tmp   \temporary

cpu thread v cpu core - Cores is an actual hardware component whereas thread is a virtual component that manages the tasks Cores use content switching while threads use multiple CPUs for operating numerous processes. Cores require only a signal process unit whereas threads require multiple processing units. 

cpus = 16
threads per core = 2
core per socket = 8
socket = 1
vcpu is is virtual

cpu has cores on it which has threads in it
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-optimize-cpu.html
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-optimize-cpu.html
nproc --all
man nproc
lscpu

memory - ram v rom - persistent and non-persistent

swap
cat /proc/vm
cat /proc/swaps
cat  /proc/sys/vm/swappiness [60]
sysctl vm.swappiness
sysctl vm.swappiness=10 [does not make persistent change]
man sysctl
man systemctl
top
free -m [shows memory free and used] https://www.linuxatemyram.com/
ls -lrth /proc/sys/vm/drop_caches
echo 3 > /proc/sys/vm/drop_caches
free -m
time cat /etc/*release  
time cat large_file >> /dev/null  * 

whois 
dig +trace linuxatemyram.com

oom_reaper 

What is the OOM score of process httpd?
ps -ef | grep httpd
cat /proc/3948/oom_score [pid of parent httpd]
pidof httpd
netstat -tnlp | grep httpd
pstree -p | grep httpd
ps aux | grep httpd


# Displays running processes in ascending order of OOM score #!/bin/bash while read -r pid comm do printf '%d\t%d\t%s\n' "$pid" "$(cat /proc/$pid/oom_score)" "$comm" done < <(ps -e -o pid= -o comm=) | sort -k2 -n

https://www.kernel.org/doc/gorman/html/understand/understand016.html
https://www.linuxatemyram.com/
https://www.vidarholen.net/contents/index.html

blkid | grep UUID

investigate cpu and 
ps -eo pid,user,ni,%cpu,comm 
ps -ef | grep [pid]
systemctl status [pid]
top | grep [pid]
cat /proc/sys/kernel/pid_max
sysctl -a | grep pid


Find anything in linux
find . -name testfile.txt [Find a file called testfile.txt in current and sub-directories.]
find /home -name *.jpg [Find all `.jpg` files in the `/home` and sub-directories.]
find . -type f -empty [Find an empty file within the current directory.]
find /home -user exampleuser -mtime -7 -iname ".db" [Find all `.db` files (ignoring text case) modified in the last 7 days by a user named exampleuser.]