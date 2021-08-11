# GreenhouseWallet
A C# Implementation of Chia Client

How to compile Chiapos on Windows Visual Studio Community

install windows
update windows
install visual studio community edition
choosing .NET desktop development, desktop development with C++, UWP development
install tortoisegit
install gitforwindows
git checkout chiapos from the chia repository https://github.com/Chia-Network/chiapos
open chiapos solution from cmake file in visualstudio
install clang 11 compiler for windows
download source for filesystem cxxopts https://github.com/jarro2783/cxxopts/tree/v2.2.1 and pybind11 https://github.com/pybind/pybind11/tree/v2.6.2
open cmake file and Build-> Install
failed for chaipos, succeeded for cxxopts and filesystem, failed for pybind11
because missing: PYTHON_EXECUTABLE, install python 3 from tools 64bit. 
missing pytest, install python language support
python environments, drop down "packages" and search pytest
open pybind11 and install
unknown type _m256i clang, probably not good enough cpu?
added CMAKE_C_FLAGS -mavx512f -mavx512vl in visual studio
it can't find the standard library maybe c:\programx86\microsoft visual studio\2019\community\vc\tools\llvm\x64\lib\clang\11\include

dylex commented on Mar 21, 2018
I had the same problem on the build machine a while ago, and it turned out to be due to boost's config stdlib autodetection not using the right set of system header files. I believe adding CXXFLAGS=-I/usr/local/opt/llvm/include LDFLAGS=-L/usr/local/opt/llvm/lib to the environment fixed it.
