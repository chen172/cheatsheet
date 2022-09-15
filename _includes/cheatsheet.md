# Linux
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
sudo lsof -i

## Linux show all used tcp and udp port
netstat -tunlp
