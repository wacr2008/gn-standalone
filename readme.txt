使用vs2015 community update3编绎，在windows上编过去。
1.bootstrap\bootstrap_new.py  
 
set WINSDK_DIR =""C:\Program Files (x86)\Windows Kits\10\Include\10.0.10586.0\ucrt
 
如果您不能正常git clone google的官网，请使用gn-standalone.7z

以下命令用来强制更新服务器版本
git rebase -i origin/master



1.cd C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC
2.vcvarsall.bat
3.cd tools\gn\
3.python bootstrap\bootstrap_new.py -s


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
mkdir testing
cd testing
git clone https://chromium.googlesource.com/chromium/testing/gtest
cd ..

# Build
windows:
1.install vs2015 update3 ,vs14-kb3165756.exe ,window sdk 10 
2.cd C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\
3.vcvarsall.bat

cd tools/gn
./bootstrap/bootstrap.py -s

# At this point, the resulting binary is at:
# gn-standalone/out/Release/gn