# 1. Proxy setting
## Windows
```
set HTTP_PROXY=http://user:password@127.0.0.1:10809 or set HTTP_PROXY=http://127.0.0.1:10808
set HTTPS_PROXY=http://user:password@127.0.0.1:10809 or set HTTPS_PROXY=http://127.0.0.1:10808
```

## python pip
```
pip install -r ./requirements.txt -i https://pypi.douban.com/simple --trusted-host=pypi.douban.com
pip3 install numpy -i https://pypi.douban.com/simple
```

## Go download
go env -w GOPROXY=https://goproxy.cn

*Note: If Makefile set GOPROXY by ```export GOPROXY ?= https://proxy.golang.org```, Be sure comment it.*

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

## Windows terminal process multiple files
```
for %i in (*.txt.html) do echo "%~i"
```

## Windows text to speech
```
echo 'Welcome to the world of speech synthesis!' | .\piper.exe --model en_US-hfc_female-medium.onnx --output_file welcome
.wav
```

## Windows audio to text
1. `ffmpeg -i input.mp3 -ar 16000 -ac 1 -c:a pcm_s16le output.wav`
2. `.\main.exe .\output.wav -m .\models\ggml-model-whisper-base.en.bin`

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
5. sudo ufw allow to 192.168.1.0/24
6. sudo ufw allow from 192.168.1.0/24 to any port 22
```

ref:
1. <https://serverfault.com/questions/74023/ufw-on-ubuntu-to-allow-all-traffic-on-lan>

## Linux get all files size of directory
```
du -sh /path/to/directory
```

## Windows create directory link
```
mklink /j linkDir TargetDir
```

## VSCode multiline selection
`shift + alt`

ref:
1. https://superuser.com/questions/1503953/vscode-multiline-select-how-to-delete-without-removing-blank-lines

## Windows restore ESP partition to EFI
```
diskpart

list disk
select disk 0
list partition
select partition 1
set id=C12A7328-F81F-11D2-BA4B-00A0C93EC93B
```

## Linux sort all directories and files based on their size
`du -sh -- *  | sort -rh`

ref:
1. https://unix.stackexchange.com/questions/106330/sort-all-directories-based-on-their-size

## Windows Linux sort all directories and files based on their size
<https://windirstat.net/>

## Package Management for MINGW64
### Start MING64
open git bash as admin

### Finding a package
`pacman -Ss <name or part of the name of the package>`

### Installing a package
`pacman -S <name of the package>`

### Uninstalling a package
`pacman -R <name of the package>`

### Update to fix problem(invalid or corrupted package)
`pacman -Syu`

ref:
1. https://www.msys2.org/docs/package-management/

## MINGW64 use cmake
### install cmake
`pacman -S cmake`

### check generator
`cmake -E capabilities`

### install generator
`pacman -S ninja`

### build
```
mkdir build && cd build
cmake -G Ninja <path-to-source> -DCMAKE_BUILD_TYPE=Release
cmake --build .
```

ref:
1. https://www.msys2.org/docs/cmake/

## Copy all deps to a directory
`ldd exe | grep "c/vcpkg" | awk '{print $3}' | xargs cp -t ./package`

## Linux show GPU VRAM
`sudo dmesg | grep drm`

## Linux display memory usage
`free -m`

## Fix Python UnicodeEncodeError: 'gbk' codec can't encode character
`str.encode('utf-8').decode('gbk')`(first convert string to byte string(utf-8), then convert back to string(gbk))

## Curl download multiple files
`curl -O https://example.com/file[1-10].png`

ref:
1. https://unix.stackexchange.com/questions/243134/curl-download-multiple-files-with-brace-syntax

## Download youtube video
1. `.\yt-dlp.exe -v --write-auto-subs --sub-langs en -I 12:14 https://www.youtube.com/watch?v=AsygBRaRnUA`
2. max quality: `-S "res:1080"`
3. only audio: `-x`


ref:
1. https://github.com/yt-dlp/yt-dlp

## VLC subtitle shortcuts
1. H (if dialogue comes later) to delay the subtitles by 50 ms
2. G (if dialogue comes first) to forward the subtitles by 50 ms

## VLC forwarding shortcuts
1. Shift + Right arrow: Forward by 3 seconds
2. Alt + Right arrow: Forward by 10 seconds
3. Ctrl + Right arrow: Forward by a minute

## VLC snapshot name
name-time code of the video: `$N-$T-`

ref:
1. https://wiki.videolan.org/Documentation:Format_String/


## Windows install android apk
1. close, open developer mode
2. .\adb.exe kill-server
3. .\adb.exe connect 127.0.0.1:58526
4. .\adb.exe install "path\to\name.apk"

## WSA proxy
### method 1
1. v2rayN use `Tun`
### method 2
1. .\adb.exe shell settings put global http_proxy 192.168.2.102:10808
2. .\adb.exe shell settings put global http_proxy :0

## Linx find a file whose name contains "Victoria" in a directory and its subdirectories
`find /path/to/directory -type f -name "*Victoria*"`

## Select text from a specific point to the end of the file
### Windows/Linux:
Press Ctrl + Shift + End
This will select the text from your current cursor position to the end of the file.

### macOS:
Press Cmd + Shift + Down Arrow
This will also select the text from the current cursor position to the end of the file.

## pandoc convert epub to txt
`pandoc input.epub -t plain -o output.txt`

# Run pip in ComfyUI
`python -m pip list`

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

ref:
1. https://stackoverflow.com/questions/8696653/dynamically-load-a-function-from-a-dll

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

## Predefined C/C++ macros for cross-platform development
```c
#if defined(__linux__)
#include <unistd.h>
#elif _WIN32
#include <windows.h>
// fix windows min, max macro
#ifdef max
#undef max
#endif
#ifdef min
#undef min
#endif
#endif
```

ref:
1. https://dev.to/tenry/predefined-c-c-macros-43id

## Cross-platform development
```c
#if defined(__linux__)
        sleep(dt);
#elif _WIN32
        Sleep(dt*1000);
#endif
```
<https://github.com/win32ports>

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

## Download pdf and book
1. find doi link by <https://www.researchgate.net>
2. download pdf by <https://sci-hub.usualwant.com/>
3. download book by <https://libgen.rs>
