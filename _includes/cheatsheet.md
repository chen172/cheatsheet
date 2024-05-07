# 1. Proxy setting
## Windows
```
set HTTP_PROXY=http://user:password@127.0.0.1:10809 or set HTTP_PROXY=http://127.0.0.1:10809
```

## python pip
```
pip install -r ./requirements.txt -i https://pypi.douban.com/simple --trusted-host=pypi.douban.com
pip3 install numpy -i https://pypi.douban.com/simple
```

## Go download
go env -w GOPROXY=https://goproxy.cn

*Note: If Makefile set GOPROXY by ```export GOPROXY ?= https://proxy.golang.org```, Be sure comment it.*

## conda download
```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
```

## npm download
```
npm config get registry
npm config set registry https://registry.npm.taobao.org
npm config set registry https://registry.npmjs.org (Note: used for set back)
```

## git bash download
```
git config --global https.proxy "https://127.0.0.1:10808"
```

## download video
<https://bilibili.iiilab.com/>

# 2. Useful command 
## Change suffix
rename 's/\.csv/\.txt/' *

## Vi delete a line
dd

## Linux convert all the .md file to .html file
for i in *.md ; do echo "$i" && pandoc -s $i -o $i.html ; done

## Linux rename multiple files
for example: rename `aro_tty-mIF-45875564pmo_opt` to `aro_tty-mImpFRA-45875564pmo_opt`

`for file in aro_tty-mIF-*_opt;do mv -i "${file}" "${file/-mIF-/-mImpFRA-}";done`

ref:
1. https://unix.stackexchange.com/questions/102647/how-to-rename-multiple-files-in-single-command-or-script-in-unix

## Nmap scan port
nmap 192.168.1.1  -p1-65535 

## vi copy a line
yy

## vi past a line
p

## add and remove library from executable file
```
patchelf --remove-needed libhello.so.1 hello  
patchelf --add-needed ./libhello.so.1 hello
```

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
str = URI.encode_www_form_component(str)

ref:
1. <https://rubyapi.org/3.1/o/uri#method-c-encode_www_form_component>

## Ruby 3 Encoding
string.force_encoding(Encoding::UTF_8)

ref:
1. <https://rubyapi.org/3.1/o/encoding>

## C language convert integer to string
sprintf(string, "%04d", integer);

## Linux not delete all the .txt files
rm !(*.txt)

## windows powershell processing all the file in a directory
foreach($file in (Get-ChildItem .\subdirectory\).Fullname) {echo $file}

## windows find exe file link library
dumpbin /dependents nm.exe

## windows find dll library info
dumpbin /headers nm.dll

## windows exports symbol from library
1. static lib
`DUMPBIN /SYMBOLS static.lib`
2. shared dll or import lib
`DUMPBIN /EXPORTS shared.dll/import.lib`

Note: If not display symbols, the lib may not export symbols when creating.

## Linux check OpenCV version
```
pkg-config opencv4 --modversion
```

## Path With Spaces in PowerShell
Use Single Quotes ' ' to Deal With Spaces in the Path in PowerShell

## Ubuntu install specific version package
```
apt list --all-versions package_name
sudo apt install package_name=package_version
```

## Run PowerShell script
1. set-ExecutionPolicy RemoteSigned
2. powershell.exe sh.ps1

ref:
1. <https://learn.microsoft.com/zh-cn/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.2>

## windows edit sql .dat file
<https://sqliteexpert.com/download.html>

## crack rar file (6 digit number)
1. .\rar2john.exe file.rar
2. .\hashcat.exe -a 3 -m 13000 --force '$rar5$16$bebb59a9f3408812c93cd3c9d074278b$15$3d7fdb029cd967b7342f13bdcfa94938$8$f1cc239aa078d2d2' ?d?d?d?d?d?d

## Linux Create Files Of A Certain Size
1. truncate -s 5M ostechnix.txt (data format)
2. yes > file.txt; truncate -s 1M file.txt (ASCII format)
3. dd if=/dev/urandom of=ostechnix.txt bs=5MB count=1 (random data)

ref:
1. <https://ostechnix.com/create-files-certain-size-linux/>

## Linux display binary file
```
hd file
```

## Linux add content to file header
sed -i '1s/^/This is my header\n/' filename

## Windows: Equivalent to linux time command
```
Measure-Command {start-process yourCommand.exe -argumentlist "argument1 argument2" -wait}
```

## git clone a tag to repo
```
git clone -b <tagname> --single-branch <repository> .
git remote set-url origin [new-url]
git branch <new-branch>
git push origin heads/<new-branch>
```
ref:
1. <https://www.techiedelight.com/clone-specific-tag-with-git/>
2. <https://komodor.com/learn/how-to-fix-fatal-remote-origin-already-exists-error/>
3. <https://www.git-tower.com/learn/git/faq/create-branch>

## Windows set env only affects current shell
```
set PATH=%PATH%;C:\your\path\here\
```

## Windows Powershell show env
```
echo $Env:PATH
```

ref:
1. <https://superuser.com/questions/341192/how-can-i-display-the-contents-of-an-environment-variable-from-the-command-promp>

## Check Disk Space in Linux
```
df -h
```

ref:
1. <https://phoenixnap.com/kb/linux-check-disk-space>

## Linux set time
```
sudo timedatectl set-time "YYYY-MM-DD HH:MM:SS"
```

## Linux enable ssh service
```
sudo systemctl enable ssh.service
sudo systemctl is-enabled ssh.service
```

## Linux show battery info
```
upower -i /org/freedesktop/UPower/devices/battery_BAT0
```

## Linux allow port through firewall
```
1. sudo apt-get install ufw
2. sudo ufw allow 22
3. sudo ufw enable
4. sudo ufw status
```

## Linux get all files size of directory
```
du -sh /path/to/directory
```

## Windows create directory link
```
mklink /j linkDir TargetDir
```

# Useful code
## convert from `int` to the `string` in C++
```c++
#include <string> 

std::string s = std::to_string(42);
int i = std::stoi("45");
```
ref:
1. <https://stackoverflow.com/questions/5590381/how-to-convert-int-to-string-in-c>

## write lines to a file in C++
```c++
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main (){
    ofstream myfile("CSC2134.txt");

    if(myfile.is_open())
    {
        string str;
        do{
            getline(cin, str);
            myfile<<str<< endl;
        }while(str!="");
        myfile.close();
    }
    else cerr<<"Unable to open file";

    return 0;
}
```

## windows call dll in C++
```c++
#include <windows.h>
#include <iostream>

/* Define a function pointer for our imported
 * function.
 * This reads as "introduce the new type f_funci as the type: 
 *                pointer to a function returning an int and 
 *                taking no arguments.
 *
 * Make sure to use matching calling convention (__cdecl, __stdcall, ...)
 * with the exported function. __stdcall is the convention used by the WinAPI
 */
typedef int (__stdcall *f_funci)();

int main()
{
    HINSTANCE hGetProcIDDLL = LoadLibrary("path/to/dll");

    if (!hGetProcIDDLL) {
        std::cout << "could not load the dynamic library" << std::endl;
        return EXIT_FAILURE;
    }

    // resolve function address here
    f_funci funci = (f_funci)GetProcAddress(hGetProcIDDLL, "setup");
    if (!funci) {
        std::cout << "could not locate the function" << std::endl;
        return EXIT_FAILURE;
    }
        
    std::cout << "funci() returned " << funci() << std::endl;
    FreeLibrary(hGetProcIDDLL);
    return 0;
}
```

## call python in C++
```c++
#include "Python.h"
    // c++ call python example
    Py_SetPythonHome(L"path/to/python3_x64-windows/tools/python3");
    Py_Initialize();
    PyRun_SimpleString("import os");
    PyRun_SimpleString("print ('Python example')");
    // call this function will destory all python context
    Py_Finalize();
```

# Useful link
## music link
1. <https://music.163.com/#/playlist?id=2945028696>
2. <https://music.163.com/#/playlist?id=2748492595>
3. <https://music.163.com/#/playlist?id=7581120144>

## English dictionary link
1. <https://www.collinsdictionary.com/dictionary/english/refuge>
2. <https://dict.youdao.com/result?word=umbrage&lang=en>

## neural network link
1. <https://github.com/glouw/tinn>
2. <https://hackaday.com/2018/04/08/tiny-neural-network-library-in-200-lines-of-code/>
3. <http://neuralnetworksanddeeplearning.com/>

## free mail
1. <https://www.guerrillamail.com/>

## File sharing and storage platform 
1. <https://gofile.io/>

## build, test and debug regex
1. <https://regex101.com/>
