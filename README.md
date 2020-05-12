# [1:User commands](http://man7.org/linux/man-pages/dir_section_1.html)

*man-pages* includes a very few Section 1 pages that document programs supplied by the GNU C library.

## [awk](http://man7.org/linux/man-pages/man1/awk.1p.html)

```
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

## [df](http://man7.org/linux/man-pages/man1/df.1.html)

```
df -h
df -h .
df -h .|awk '{print $5}'|grep -v U|cut -d "%" -f1
```

## [du](http://man7.org/linux/man-pages/man1/du.1.html)

```
du -h
du -Sh
du -S .|sort -nr|head -10
```

## [find](http://man7.org/linux/man-pages/man1/find.1.html)

```
find . -ls|sort -nrk7|head -10
find . -ls|sort -nrk7 --debug
find . -name '*.sh' | xargs chmod u+x
find . -name '*.sh' | xargs dos2unix
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
```

## [iostat](http://man7.org/linux/man-pages/man1/iostat.1.html)

```
iostat
iostat 1
iostat 1 5
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

## [top](http://man7.org/linux/man-pages/man1/top.1.html)

```
top
```

## [uname](http://man7.org/linux/man-pages/man1/uname.1.html)

```
uname -a
uname -a|awk '{print $2}'
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
netstat -tpc
netstat |grep -i listen
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

