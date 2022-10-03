# 1. Fast download in China
## python pip
pip install -r ./requirements.txt -i https://pypi.douban.com/simple --trusted-host=pypi.douban.com

## Go download
go env -w GOPROXY=https://goproxy.cn

*Note: If Makefile set GOPROXY by ```export GOPROXY ?= https://proxy.golang.org```, Be sure comment it.*

# 2. Useful command 
## Change suffix
rename 's/\.csv/\.txt/' *

## Vi delete a line
dd

## Linux convert all the .md file to .html file
for i in *.md ; do echo "$i" && pandoc -s $i -o $i.html ; done

## Nmap scan port
nmap 192.168.1.1  -p1-65535 

## vi copy a line
yy

## vi past a line
p

## add and remove library from executable file
patchelf --remove-needed libhello.so.1 hello  
patchelf --add-needed ./libhello.so.1 hello

## Linux lists all open files
lsof

## Show Files Accessed by Network Connections
sudo lsof -i

## Linux show all used tcp and udp port
sudo netstat -tunlp


## Install specifical gem package
sudo gem install rack -v "2.2.4"

## vi append just after the current cursor position
a

## Linux edit hosts file
sudo vi /etc/hosts

## clone a specific directory from Github
1. Replace ```tree/master``` with ```trunk```, so download https://github.com/torvalds/linux/tree/master/net/mac80211 would be:
```
svn checkout https://github.com/torvalds/linux/trunk/net/mac80211
```

2. Replace ```tree/v5.13``` with ```tags/v5.13```, so download https://github.com/torvalds/linux/tree/v5.13/net/mac80211 would be:
```
svn checkout https://github.com/torvalds/linux/tags/v5.13/net/mac80211
```

## gcc link openssl
gcc XXX.c -lcrypto -lssl

## gcc not show warning
gcc XXX.c -w

## Ruby 3 encode url
str = URI.encode_www_form_component(str) (https://rubyapi.org/3.1/o/uri#method-c-encode_www_form_component)

## Ruby 3 Encoding
string.force_encoding(Encoding::UTF_8) (https://rubyapi.org/3.1/o/encoding)

## C language convert integer to string
sprintf(string, "%04d", integer);

## Linux not delete all the .txt files
rm !(*.txtx)
