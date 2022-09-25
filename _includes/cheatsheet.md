# 1. Fast download in China
## python pip
pip install -r ./requirements.txt -i https://pypi.douban.com/simple --trusted-host=pypi.douban.com

## Go download
go env -w GOPROXY=https://goproxy.cn

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
netstat -tunlp


## Install specifical gem package
sudo gem install rack -v "2.2.4"

## vi append just after the current cursor position
a

## Linux edit hosts file
sudo vi /etc/hosts
