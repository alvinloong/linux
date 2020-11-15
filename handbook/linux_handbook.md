# [1:User commands](http://man7.org/linux/man-pages/dir_section_1.html)

*man-pages* includes a very few Section 1 pages that document programs supplied by the GNU C library.

## [awk](http://man7.org/linux/man-pages/man1/awk.1p.html)

```
awk 'NF' files.txt

df -h .|awk '{print $5}'

echo -e "line1\nline2" | awk 'BEGIN{ print "Start" } { print } END{print "End" } '

awk -F: '{print $1, $NF}' /etc/passwd
awk -F: '{print $1 "-" $NF}' /etc/passwd

awk -F: 'NR<5 { print $1 }' /etc/passwd
awk -F: 'NR==1,NR==4 { print $NF }' /etc/passwd
awk -F: '/^a/ { print $1 }' /etc/passwd
awk -F: '!/^a/ { print $1 }' /etc/passwd

awk -F: '{ print $NF }' /etc/passwd
awk 'BEGIN { FS=":" } { print $NF }' /etc/passwd
awk -v FS=":" '{ print $NF }' /etc/passwd
```

## [bg](https://man7.org/linux/man-pages/man1/bg.1p.html)

```
jobs -l
fg 1
#Ctrl z
bg 1
```

## [chown](https://man7.org/linux/man-pages/man1/chown.1.html)

```
chown -R root:staff /u
chown root /u
chown root:staff /u
#chown root.staff /u
chown -hR root /u
```

## [cp](https://man7.org/linux/man-pages/man1/cp.1.html)

```
cp source destination
cp -r dir1 dir2
cp -a dir1 dir2
cp -avr dir1 dir2
```

## [crontab](https://man7.org/linux/man-pages/man1/crontab.1.html)

```
crontab -l
crontab -e
```

```
# m h  dom mon dow   command
#every hour
0 * * * * ~/test.sh
#every day at 03:00 am
0 3 * * * ~/test.sh
#every minute
*/1 * * * * ~/test.sh
```

Quick and simple editor for cron schedule expressions:

[https://crontab.guru](https://crontab.guru)

## [curl](https://man7.org/linux/man-pages/man1/curl.1.html)

```
curl http://127.0.0.1:8080
curl -v http://127.0.0.1:8080
curl http://127.0.0.1:8080/getInfo?name=ming&passwd=123
curl -X GET  'http://127.0.0.1:8080/getInfo'  --header 'sessionid:123456789'
curl -i --user name:pwd http://127.0.0.1:8080/getInfo
curl -d "name=ming&passwd=12345" "http://127.0.0.1:8080/getInfo"     
curl -i -H "Content-Type:application/json" -X POST --data '{"name": "xiaoming"}'  http://127.0.0.1:8080/getInfo
curl -X POST "http://127.0.0.1:8080/getInfo" -H "Content-Type:application/json"  -d ""dataparams":{ "name":"xiaoming"，"type":"A"}"
curl http://127.0.0.1:8080/uploadFile  -F "file=@D:\Users\myFile\123.txt"
curl  --include  --no-buffer  --header "Connection: Upgrade"  --header  "Upgrade: websocket"   --header  "Sec-WebSocket-Key: SGVsbG8sIHdvcmxkIQ=="   --header "Sec-WebSocket-Version: 13"  http://abc.xxx.com:80/connection?key=abcd
curl --include --no-buffer  --header "Connection: close"  --header "Upgrade: websocket"  --header "Sec-WebSocket-Key: SGVsbG8sIHdvcmxkIQ=="   --header "Sec-WebSocket-Version: 13" http://abc.xxx.com:80/connection?key=abcd
```

## [cut](https://man7.org/linux/man-pages/man1/cut.1.html)

```
echo 'abc12345'| cut -c 2-
cut -f 1,2 -d ':' /etc/passwd
awk -F: '{print $1 ":" $2}' /etc/passwd
```

## [date](https://man7.org/linux/man-pages/man1/date.1.html)

```
date +%Y%m%d
date +%Y%m%d_%w
date +%Y%m%d_%H%M
date +%Y%m%d_%H%M%S
date '+%Y%m%d %H:%M:%S'
date -d '1 day ago' '+%Y-%m-%d'
date -d '1 day ago' '+%Y-%m-%d 00:00:00
```

## [df](http://man7.org/linux/man-pages/man1/df.1.html)

```
df -h
df -h .
df -h .|awk '{print $5}'|grep -v U|cut -d "%" -f1
df -i
```

## [du](http://man7.org/linux/man-pages/man1/du.1.html)

```
du -h
du -sh
du -sh .
du -sh *
du -sh *|sort -nr
du -h -s
du -h -d 0
du -h -d 1
du -h -d 1|sort -nr|head -10
du -h --max-depth=0 .
du -ah --max-depth=1
du -Sh
du -S .|sort -nr|head -10
```

## [echo](https://man7.org/linux/man-pages/man1/echo.1.html)

```
echo '\t'
echo -e '\t'
echo -e 'abc\n'
echo -n 'abc'
echo hi |tee -a out.txt
```

## [fg](https://man7.org/linux/man-pages/man1/fg.1p.html)

```
jobs -l
fg 1
#Ctrl z
bg 1
```

## [find](http://man7.org/linux/man-pages/man1/find.1.html)

```
find . -ls|sort -nrk7|head -10
find . -ls|sort -nrk7 --debug
find . -type f -ls|sort -nrk7
find . -name '*.sh' | xargs chmod u+x
find . -name '*.sh' | xargs dos2unix
find . -name '*.sh' -ls
find . -iname "a*.txt"
find . ! -name '*.sh'
find . -not -name '*.sh'
find . ! -name 'abc*.txt'
find . -name "*.txt" ! -name "abc*"
find . -name "*.txt" ! -name "abc*" -name "c*.txt"
find . -name "*.txt" ! -name "abc*" ! -name "c*.txt"
find . -name "abc*" ! -name "*.*"
find . -type f -name 'c*' -ls
#find . -type f -name "*.txt" -print|xargs -n 1
find . -type f -name "*.txt" -print0|xargs -0 -n 1
find . -type f -name "*.txt" -print0|xargs -0 ls -l
find . -type f -name "*.txt" -print0|xargs -0 -I {} ls -l {}
find . -amin -1
find . -amin 1
find . -amin +1
find . -atime -1
find . -atime +1
find . -mtime 0
find . -mtime +0
find . -mtime -1
find . -cmin -1
find . -cmin +1
find . -mmin +1 -mmin -10 -ls
find . -mtime +1 -mtime -10 -ls
find . -maxdepth 1 -type f -size +20k -exec ls -lh '{}' \;
find . -maxdepth 1 -type f -size +20k -print0|xargs -0 ls -lh
find . -depth
find . -maxdepth 2
find . -mindepth 2
find . -type f
find . -type d
find . -user root
find . -regex ".*/[Aa-z]*/*.txt"
find . -regex ".*/[Aa-z]*/*"
find . -regex ".*/[Aa-z]*/*.*"
```

## [grep](http://man7.org/linux/man-pages/man1/grep.1.html)

```
grep root /etc/passwd
grep -v root /etc/passwd
grep -i ERROR a.txt
grep -i -E 'ERROR|conflict' a.txt
egrep -i 'ERROR|conflict' a.txt
grep -i -E 'ERROR|conflict' a.txt -c
egrep -i 'ERROR|conflict' a.txt -c
```

## [head](http://man7.org/linux/man-pages/man1/head.1.html)

```
head -10 a.txt
head -n 10 a.txt
head -1 test.sh |wc
head -1 test.sh |wc -c
head -c 10 test.sh
```

## [hostname](https://man7.org/linux/man-pages/man1/hostname.1.html)

```
hostname
sudo hostname alvinpc-new
sudo vi /etc/hostname
sudo vi /etc/hosts
service hostname restart
```

## [hostnamectl](https://man7.org/linux/man-pages/man1/hostnamectl.1.html)

```
hostnamectl status
hostnamectl set-hostname alvinpc
```

## [iostat](http://man7.org/linux/man-pages/man1/iostat.1.html)

```
iostat
iostat 1
iostat 1 5
```

## [jobs](https://man7.org/linux/man-pages/man1/jobs.1p.html)

```
jobs -l
jobs -p
jobs -r
jobs -s
jobs -n
fg 1
#Ctrl z
bg 1
```

## [kill](https://man7.org/linux/man-pages/man1/kill.1.html)

```
kill -9 pid
kill -15 pid
kill -l
```

## [ln](https://man7.org/linux/man-pages/man1/ln.1.html)

```
ln -s /mnt/temp/ /temp
rm /temp #NOT rm /temp/
unlink /temp #NOT unlink /temp/
```

## [ls](https://man7.org/linux/man-pages/man1/ls.1.html)

```
ls -l
ls -lt
ls -lh
ls -lhS
ls -lht
ls -lhtr
ls -lah
ls -li
ls -dils
ls -l|grep '[Aa-z].txt'
```

## [lscpu](https://man7.org/linux/man-pages/man1/lscpu.1.html)

```
lscpu
lscpu | egrep 'Model name|Socket|Thread|NUMA|CPU\(s\)'
lscpu -p
cat /proc/cpuinfo
echo "CPU threads: $(grep -c processor /proc/cpuinfo)"
grep 'cpu cores' /proc/cpuinfo | uniq
```

## [mkdir](https://man7.org/linux/man-pages/man1/mkdir.1.html)

```
mkdir dir1
mkdir dir1 dir2 dir3
mkdir -p dir1
mkdir -p dir1 dir2 dir3
mkdir -p dir1/dir11
mkdir -p dir1/{dir11,dir12,dir13}
```

## [nohup](https://man7.org/linux/man-pages/man1/nohup.1.html)

```
nohup ./s.sh >>s.log 2>&1 &
jobs -l
fg 1
#Ctrl z
bg 1
```

## [pgrep](https://man7.org/linux/man-pages/man1/pgrep.1.html)

```
pgrep -a sshd
pgrep sshd
```

## [ps](https://man7.org/linux/man-pages/man1/ps.1.html)

```
ps -ef
ps -ef | egrep "1029|PID"
ps -efH | grep 1029
ps --no-headers -o comm 1
ps -fu oracle
ps -ef|grep EAS|grep -v grep|awk '{print $2}'|xargs -I {} kill -9 {}
```

## [readlink](https://man7.org/linux/man-pages/man1/readlink.1.html)

```
ln -s /a/b/c /test
readlink -f /test
BASE_DIR=$(dirname $(readlink -f $0))
BASE_DIR=$(dirname $(readlink -f $0))
BASE_DIR=$(cd $(dirname $(readlink -f $0)) && pwd)
BASE_DIR=$(cd $(dirname $(readlink -f $BASH_SOURCE)) && pwd)
```

## [rsync](https://man7.org/linux/man-pages/man1/rsync.1.html)

```
rsync -p ~/.ssh/* alvin@10.20.20.1:~/.ssh/
rsync --list-only alvin@10.20.20.1::test/
rsync -av /test/dir1 alvin@10.20.20.1::test/
rsync -aP /test/dir1 alvin@10.20.20.1::test/
rsync -aP /test/dir1 alvin@10.20.20.1::test/ --password-file=$PASSWORD_FILE
rsync -aP /test/dir1 alvin@10.20.20.1::test/ --password-file=$PASSWORD_FILE --exclude-from="$EXCLUDE_FILE"
rsync -aP --bwlimit 7.5M /test/dir1 alvin@10.20.20.1::test/
rsync -aP --bwlimit 76800 /test/dir1 alvin@10.20.20.1::test/
rsync -a --partial /test/dir1 alvin@10.20.20.1::test/
rsync -av --delete /test/dir1 alvin@10.20.20.1::test/
rsync -av --delete /test/dir1/ alvin@10.20.20.1::test/
```

## [screen](https://man7.org/linux/man-pages/man1/screen.1.html)

```
script /dev/null
screen -S test
screen -ls
#Ctrl+a d
screen -r test
```

## [sed](https://man7.org/linux/man-pages/man1/sed.1.html)

```
sed -i -r 's/(.*)(password=")(.*)(")/\1\2\4/g' a.txt
find . -type f |xargs sed -i -r 's/(.*)(password="")/\1\2\4/gi'
sed 's/root/du/g' /etc/passwd | head -2
sed '2s/bin/du/' /etc/passwd | head -2
sed '2,4d' /etc/passwd | head -3
echo "world" | sed 'i\hello'
sed '$a\nihao' a.txt
echo 'a,b,c' | sed 's/,/\n/g'
for i in `echo 'a,b,c' | sed 's/,/\n/g'`;
  do
    echo $i
done
```

## [seq](https://man7.org/linux/man-pages/man1/seq.1.html)

```
seq 0 5
seq 0 3 15
seq -s ',' 0 3 15
seq -w 0 3 15
```

## [sleep](https://man7.org/linux/man-pages/man1/sleep.1.html)

```
sleep 5
sleep 5s
sleep 1m
sleep 0.5m
sleep 0.5h
sleep 1d
```

## [ssh](https://man7.org/linux/man-pages/man1/ssh.1.html)

```
ssh hostname
ssh -p 2222 hostname
ssh 'alvin@10.20.20.1'
ssh alvin@10.20.20.1
ssh -V
ssh -v localhost
#ssh -A ...
#ForwardAgent
#AllowAgentForwarding
export GIT_SSH=/usr/bin/git_ssh
```

```
cat /usr/bin/git_ssh
#!/bin/bash
ssh -i ~/.ssh/id_rsa $@
```

## ssh-copy-id

```
ssh-copy-id server4
ssh-copy-id -i ~/.ssh/id_rsa.pub root@10.20.20.1
ls -la ~/.ssh/
```

## [ssh-add](https://man7.org/linux/man-pages/man1/ssh-add.1.html)

```
ssh-add
ssh-add ~/.ssh/id_rsa
ssh-add ~/.ssh/id_rsa*
ssh-add -L
ssh-add -l
ssh-add -D
```

## [ssh-agent](https://man7.org/linux/man-pages/man1/ssh-agent.1.html)

```
ssh-agent $SHELL
eval $(ssh-agent)
eval `ssh-agent -s`
ssh-agent -k
echo $SSH_AGENT_PID
echo $SSH_AUTH_SOCK
ps -efH |grep 1029
```

## [ssh-keygen](https://man7.org/linux/man-pages/man1/ssh-keygen.1.html)

```
ssh-keygen
ssh-keygen -t rsa
ssh-keygen -t rsa -P '' -f ~/.ssh/id_rsa
ssh-keygen -p
ssh-keygen -f "~/.ssh/known_hosts" -R "hostname"
ls -la ~/.ssh/
chmod 0600 ~/.ssh/authorized_keys
chmod 0600 ~/.ssh/id_rsa
```

## [sort](http://man7.org/linux/man-pages/man1/sort.1.html)

```
sort a.txt
sort -r a.txt
sort -nrk7 --debug
```

## [stat](http://man7.org/linux/man-pages/man1/stat.1.html)

```
stat -fc %s .
```

## [systemctl](https://man7.org/linux/man-pages/man1/systemctl.1.html)

```
sudo systemctl status mongod
sudo systemctl start mongod
sudo systemctl stop mongod
sudo systemctl restart mongod
sudo systemctl enable mongod
sudo systemctl disable mongod
```

## [tail](http://man7.org/linux/man-pages/man1/tail.1.html)

```
tail -5 a.txt
tail -n 5 a.txt
tail -f a.txt
tail -f -n 100 a.txt
```

## [tar](https://man7.org/linux/man-pages/man1/tar.1.html)

```
tar -czvf archive.tar.gz stuff
tar -czvf archive.tar.gz /dir1 /dir2
tar -czvf archive.tar.gz /home --exclude=/home/ubuntu --exclude=/home/temp
tar -czvf archive.tar.gz /home/ubuntu --exclude=*.mp4
tar -cjvf archive.tar.bz2 stuff
tar -xzvf archive.tar.gz -C /tmp/
tar -cvf etc.tar /etc
tar -c -v -f etc.tar /etc
tar -zxvf etc.tar.gz
```

## [tee](https://man7.org/linux/man-pages/man1/tee.1.html)

```
echo hi |tee -a out.txt
```

## [top](http://man7.org/linux/man-pages/man1/top.1.html)

```
top
```

## [uname](http://man7.org/linux/man-pages/man1/uname.1.html)

```
uname -a
uname -a|awk '{print $2}'
uname -r
```

## [unlink](https://man7.org/linux/man-pages/man1/unlink.1.html)

```
ln -s /mnt/temp/ /temp
rm /temp #NOT rm /temp/
unlink /temp #NOT unlink /temp/
```

## [wc](https://man7.org/linux/man-pages/man1/wc.1.html)

```
wc
wc -l test.sh
wc -c test.sh
echo test.sh |wc -l
head -1 test.sh |wc
head -1 test.sh |wc -c
```

## [xargs](https://man7.org/linux/man-pages/man1/xargs.1.html)

```
cat a.txt |xarg
cat a.txt |xargs -n 3
echo "splitXsplitXsplitXsplit" | xargs -d X
echo "splitXsplitXsplitXsplit" | xargs -d X -n 2
cat args.txt | xargs -n 2 ./cecho.sh
cat args.txt | xargs ./cecho.sh
cat args.txt | xargs -I {} ./cecho.sh -p {} -l
find . -type f -name "*.txt" -print0|xargs -0 ls -l
find . -type f -name "*.txt" -print0|xargs -0 -I {} ls -l {}
ps -ef|grep EAS|grep -v grep|awk '{print $2}'|xargs -I {} kill -9 {}
```

# [8:Superuser and system administration commands](http://man7.org/linux/man-pages/dir_section_8.html)

*man-pages* includes a very few Section 8 pages that document programs supplied by the GNU C library.

## dhclient

```
sudo dhclient -r
sudo dhclient
#if not work, try restarting server
```

## [dumpe2fs](http://man7.org/linux/man-pages/man8/dumpe2fs.8.html)

```
sudo dumpe2fs -h /dev/sda2|grep -i block
```

## [ifconfig](https://man7.org/linux/man-pages/man8/ifconfig.8.html)

```
ifconfig
sudo ifconfig enp0s3 up
sudo ifconfig enp0s3 down
ifconfig -s
netstat -i
```

## [iostat](http://man7.org/linux/man-pages/man1/iostat.1.html)

```
iostat
iostat 1
iostat 1 5
```

## [iptables](https://man7.org/linux/man-pages/man8/iptables.8.html)

```
iptables -A INPUT -s 10.20.20.1 -j REJECT
iptables -D INPUT -s 10.20.20.1 -j REJECT
```

## [lsof](https://man7.org/linux/man-pages/man8/lsof.8.html)

```
lsof /dev/hd4
lsof -i 4 -a -p 1234
lsof -i 6
lsof -p 6558
lsof -p 456,123,789 -u 1234,abe
lsof -u alvin
lsof -c mysql
lsof -c mysql -c apache
lsof -u test -c mysql
lsof -u ^root
lsof /home/alvin/test/s.sh
lsof +D /home/alvin/test/
lsof |grep /home/alvin/test/
lsof -s|grep deleted|sort -nr -k7
```

## [netstat](http://man7.org/linux/man-pages/man8/netstat.8.html)

```
netstat
netstat -tanp
netstat -t4npl
netstat -tnpl
netstat -tanp|grep -i listen
netstat -tpc
netstat -tanpc|grep 5432
netstat -rn
netstat -i
ifconfig -s
```

## [route](https://man7.org/linux/man-pages/man8/route.8.html)

```
route -n
sudo route add default gw 10.20.20.1
```

## [tcpdump](https://man7.org/linux/man-pages/man8/tcpdump.8.html)

```
sudo tcpdump host 10.20.20.1
sudo tcpdump src 10.20.20.1
sudo tcpdump dst 10.20.20.1
sudo tcpdump net 10.20.20.0/24
sudo tcpdump port 5432
sudo tcpdump src port 5432
sudo tcpdump portrange 21-23
sudo tcpdump -nnvvS src 10.5.2.3 and dst port 3389
sudo tcpdump -i enp0s3
```

## [top](http://man7.org/linux/man-pages/man1/top.1.html)

```
top
```

## [vmstat](http://man7.org/linux/man-pages/man8/vmstat.8.html)

```
vmstat
vmstat 1
vmstat 1 5
```

