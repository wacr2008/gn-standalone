这货目前只支持vs2015编了，因为它依赖了这狗屎base库。。
另外，gn的\bootstrap\bootstrap.py 脚本需要修改才可以在windows上编过去。
1.是它还引用了一个base中没有的文件，直接删除就好
2.就是它少写了一个lib，自己加到脚本中即可。
3.对于is_win，它少包含了一些cc文件，如        'base/trace_event/malloc_dump_provider.cc',自己加上

难道google的员都不用windows了？？？


为了中国人民可以正常git clone,上传了一个压缩包 gn-standalone.7z，直接解压就好了。



1.C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC
2.vcvarsall.bat
3.python tools\gn\bootstrap\bootstrap.py -s


以下是参考信息

mkdir gn-standalone
cd gn-standalone
mkdir tools
cd tools
git clone https://chromium.googlesource.com/chromium/src/tools/gn
cd ..
mkdir -p third_party/libevent
cd third_party/libevent
wget --no-check-certificate https://chromium.googlesource.com/chromium/chromium/+archive/master/third_party/libevent.tar.gz
tar -xvzf libevent.tar.gz
cd ../..
git clone https://chromium.googlesource.com/chromium/src/base
git clone https://chromium.googlesource.com/chromium/src/build
git clone https://chromium.googlesource.com/chromium/src/build/config
mkdir testing
cd testing
git clone https://chromium.googlesource.com/chromium/testing/gtest
cd ..

# Build
cd tools/gn
./bootstrap/bootstrap.py -s

# At this point, the resulting binary is at:
# gn-standalone/out/Release/gn