## sendosc
sendosc is a simple command-line tool for sending OSC packet.

timboll/sendosc fork adds to sendosc.cpp a line of code that enables broadcast capability (ip address x.x.x.255) 
``` 50    transmitSocket.SetEnableBroadcast(true); ```

https://github.com/RossBencina/oscpack/blob/master/ip/UdpSocket.h#L94C1-L95C1

## usage
```
sendosc
usage : sendosc dst_host dst_port path [[type] [param]] ...
 
   type
     i : int
     f : float
     b : boolean (true/false)
     s : string
 
   example
     ./sendosc 127.0.0.1 5678 /test1 i 123
     ./sendosc 127.0.0.1 5678 /test2 f 123.45
     ./sendosc 127.0.0.1 5678 /test3 s teststring
     ./sendosc 127.0.0.1 5678 /test4 b true
     ./sendosc 127.0.0.1 5678 /test5 s teststring i 123 f 123.4 b false
```

## How to install
### macOS
```
% cd ~
% git clone https://github.com/timboll/sendosc.git
% cd sendosc
% cmake .
% make
% sudo cp ./sendosc /usr/local/bin/sendosc
```

### debian & ubuntu
```
$ sudo apt-get install liboscpack-dev
$ cd ~
$ git clone https://github.com/timboll/sendosc.git
$ cd sendosc
$ cmake .
$ make
$ sudo make install  
```

### Archlinux
##### get dependencies and prepare folder
````
$ cd ~
$ git clone https://github.com/arturoc/oscpack
$ cd oscpack 
````

##### enable -fpic flag for shared library linking
```
$ nano Makefile 
```
change this line
```
COPTS = -Wall -O3
```
for this one
```
COPTS = -Wall -O3 -fPIC
```
##### compile and install 
```
$ make
$ sudo make install
```

#### clone, compile and install sendosc 
```
$ cd ~
$ git clone https://github.com/timboll/sendosc.git
$ cd sendosc
$ sudo pacman -S cmake
$ cmake .
$ make
$ sudo cp ./sendosc /usr/local/bin/sendosc
```
## Windows (experimental)

```
> git clone https://github.com/timboll/sendosc.git
> cd sendosc
> mkdir build
> cd build
> cmake ..
> MSBuild.exe sendosc.vcxproj /t:clean;rebuild /p:Configuration=Release;Platform="win32"
> cd Release
> dir sendosc.exe

 Volume in drive C is XXXXXXXX
 Volume Serial Number is XXXX-XXXX

 Directory of C:\work\sendosc\build\Release

2019/01/16  20:38            18,432 sendosc.exe
               1 File(s)         18,432 bytes
```

## Copyright and license
Copyright (c) 2015 yoggy

Released under the [MIT license](LICENSE.txt)
