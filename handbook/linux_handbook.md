# [1:User commands](http://man7.org/linux/man-pages/dir_section_1.html)

*man-pages* includes a very few Section 1 pages that document programs supplied by the GNU C library.

## [awk](http://man7.org/linux/man-pages/man1/awk.1p.html)

```
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

## [cp](https://man7.org/linux/man-pages/man1/cp.1.html)

```
cp source destination
cp -r dir1 dir2
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

## [df](http://man7.org/linux/man-pages/man1/df.1.html)

```
df -h
df -h .
df -h .|awk '{print $5}'|grep -v U|cut -d "%" -f1
```

## [du](http://man7.org/linux/man-pages/man1/du.1.html)

```
du -h
du -h -s
du -h -d 0
du -h -d 1
du -h -d 1|sort -nr|head -10
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

## [find](http://man7.org/linux/man-pages/man1/find.1.html)

```
find . -ls|sort -nrk7|head -10
find . -ls|sort -nrk7 --debug
find . -type f -ls|sort -nrk7
find . -name '*.sh' | xargs chmod u+x
find . -name '*.sh' | xargs dos2unix
find . -name '*.sh' -ls
find . -type f -name 'c*' -ls
#find . -type f -name "*.txt" -print|xargs -n 1
find . -type f -name "*.txt" -print0|xargs -0 -n 1
find . -type f -name "*.txt" -print0|xargs -0 ls -l
find . -type f -name "*.txt" -print0|xargs -0 -I {} ls -l {}
```

## [grep](http://man7.org/linux/man-pages/man1/grep.1.html)

```
grep root /etc/passwd
grep -v root /etc/passwd
```

## [head](http://man7.org/linux/man-pages/man1/head.1.html)

```
head -10 a.txt
head -n 10 a.txt
head -1 test.sh |wc
head -1 test.sh |wc -c
head -c 10 test.sh
```

## [iostat](http://man7.org/linux/man-pages/man1/iostat.1.html)

```
iostat
iostat 1
iostat 1 5
```

## [kill](https://man7.org/linux/man-pages/man1/kill.1.html)

```
kill -9 pid
kill -15 pid
kill -l
```

## [pgrep](https://man7.org/linux/man-pages/man1/pgrep.1.html)

```
pgrep -a sshd
pgrep sshd
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

## [tail](http://man7.org/linux/man-pages/man1/tail.1.html)

```
tail -5 a.txt
tail -n 5 a.txt
tail -f a.txt
tail -f -n 100 a.txt
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
```

# [8:Superuser and system administration commands](http://man7.org/linux/man-pages/dir_section_8.html)

*man-pages* includes a very few Section 8 pages that document programs supplied by the GNU C library.

## [dumpe2fs](http://man7.org/linux/man-pages/man8/dumpe2fs.8.html)

```
sudo dumpe2fs -h /dev/sda2|grep -i block
```

## [iostat](http://man7.org/linux/man-pages/man1/iostat.1.html)

```
iostat
iostat 1
iostat 1 5
```

## [netstat](http://man7.org/linux/man-pages/man8/netstat.8.html)

```
netstat
netstat -tanp
netstat -tpc
netstat -tanpc|grep 5432
netstat |grep -i listen
netstat -rn
```

## [route](https://man7.org/linux/man-pages/man8/route.8.html)

```
route -n
sudo route add default gw 192.168.199.1
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

