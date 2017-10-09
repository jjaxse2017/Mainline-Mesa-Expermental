# Mainline-Mesa-Expermental

--One open source radeon gpu performs better than two windows crossfire radeon gpu's

1.) Download the latest source code from https://github.com/mesa3d/mesa
1a.) Download the compiled radeon driver from releases that has libexpat precompiled for x86_64 &x86_32 to /usr/local/lib/ or mainline compile/install libexpat from https://github.com/libexpat/libexpat (special note here the libexpat source was included in the release just incase)
2b.) LLVM 5 & 6 were obtained from https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa/ or https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa  while gcc 7.0 was obtained from https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/test

2.) Copy the src directory files included into the mesa 3d source code (name changes ac_llvm_build.c to ac_llvm_build.cpp)

3.) Run autogen.sh (needed to generate a configure file /w the updated file name changes)

4.) For 32 bit configure file over the newly generated configure file (forces LLVM cflags) 4.a) Change the march=native or to the specific arch run configure and make -j4 the compiled files will be located in the lib folder 4.b) Google the missing libraries during compile -l stands for lib, getting 32 bit version's on a 64 bit will be tedious since they don't show up often, so you'll have to add :i386 at the end of the said reference. Cross compiling from 64 bit to 32 bit worked when using gcc 6/llvm 5.

5.) strip --strip-unneeded --remove-section=.comment lib/*

6.) Move the files into appropriate directory see the compiled radeon driver https://github.com/jjaxse2017/Mainline-Mesa-Expermental/releases for instructions on how to run the driver.

7.) --Assuming you're using using LLVM 6/GCC7, Make clean then configure again making the r600 driver with just GCC 7 and copy the files contained in the gallium directory over to the desired lib directory minus swrast. (special note here the gallium and dri files can/should be put into one single directory)

8.) To compile the 32 bit files... I had to use GCC6/LLVM5 on a 64 bit OS, though I tried gcc7/llvm6:i386

Check out https://github.com/jjaxse2017/scorched-earth-3d for a free open source game to try out the mainline driver on. 

64bit (GCC6/LLVM5)

./configure CFLAGS='-march=core2 -O3' CXXFLAGS='-march=core2 -std=gnu++17' LLVM_CFLAGS='-march=core2 -O3' LLVM_CPPFLAGS='-march=core2 -O3 -std=gnu++17' --with-platforms='x11,drm' --with-gallium-drivers='r600,swrast,radeonsi' --with-dri-drivers='swrast,radeon' --enable-glx-tls --enable-xa --enable-osmesa --enable-texture-float --enable-gles1 -enable-gles2 --enable-gbm --enable-dri  --enable-glx --enable-opengl --enable-shared-glapi --enable-va --enable-vdpau --enable-dri3 --enable-llvm --with-vulkan-drivers='radeon' --enable-opencl --enable-opencl-icd



32bit (GCC6/LLVM5)

./configure CFLAGS='-pipe -m32 -march=core2 -O3' CXXFLAGS='-pipe -m32 -march=core2 -O3 -std=c++1z -std=c++17' CPPFLAGS='-pipe -march=core2 -O3 -std=gnu++1z' LLVM_CFLAGS='-pipe -m32 -march=core2 -O3' LLVM_CPPFLAGS='-pipe -m32 -march=core2 -O3 -std=c++1z -std=c++17' --with-platforms='x11,drm' --with-gallium-drivers='r600,swrast,radeonsi' --with-dri-drivers='swrast,radeon' --enable-glx-tls --enable-xa --enable-osmesa --enable-nine --enable-texture-float --enable-gles1 --enable-gles2 --enable-shared-glapi --enable-gbm --enable-dri  --enable-glx --enable-opengl --enable-va --enable-vdpau --enable-dri --enable-dri3 --enable-llvm --enable-llvm-shared-libs --with-vulkan-drivers='radeon' --host=i686-pc-linux-gnu --target=i686-pc-linux-gnu

#better off disable mmx/sse/3d now in the config file... cp /home/pi/Documents/mesa-master/src/mapi/entry_x86_tls.h /home/pi/Documents/mesa-master/src/mapi/entry_x86-64_tls.h

64bit2(GCC7/LLVM) Used for DRI/everything

./configure CFLAGS='-pipe -march=core2 -O3' CPPFLAGS='-pipe -march=core2 -O3 -std=gnu++1z' CXXFLAGS='-pipe -march=core2 -O3 -std=gnu++1z' LLVM_CFLAGS='-pipe -march=core2 -O3' LLVM_CPPFLAGS='-pipe -march=core2 -O3 -std=c++1z -std=c++17' LDFLAGS='-lstdc++ -lz' --with-platforms='x11,drm' --with-gallium-drivers='' --with-dri-drivers='swrast,radeon' --enable-glx-tls --enable-xa --enable-texture-float --enable-opengl --enable-glx --enable-gles1 -enable-gles2 --enable-gbm --enable-dri --enable-dri3  --enable-osmesa --enable-shared-glapi --enable-va --enable-vdpau  --enable-llvm --enable-llvm-shared-libs --with-vulkan-drivers='radeon'

64bit2(GCC7) Used for missing R600 driver

./configure CFLAGS='-pipe -march=core2 -O3' CPPFLAGS='-pipe -march=core2 -O3 -std=gnu++1z' CXXFLAGS='-pipe -march=core2 -O3 -std=gnu++1z' LLVM_CFLAGS='-pipe -march=core2 -O3' LLVM_CPPFLAGS='-pipe -march=core2 -O3 -std=c++1z -std=c++17' LDFLAGS='-lstdc++ -lz' --with-platforms='x11,drm' --with-gallium-drivers='r600' --with-dri-drivers='' --enable-glx-tls --enable-xa --enable-texture-float --enable-opengl --enable-glx --enable-gles1 -enable-gles2 --enable-gbm --enable-dri --enable-dri3  --enable-osmesa --enable-shared-glapi --enable-va --enable-vdpau --disable-gallium-llvm --disable-llvm


<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html><head>

<h1>Unigine Heaven Benchmark 4.0 -- Single GPU linux mesa 13.0-dev</h1>
<table class="result">
<tr><td class="right">FPS:</td><td><div class="orange"><strong>83.5</strong></div></td></tr>
<tr><td class="right">Score:</td><td><div class="orange"><strong>2104</strong></div></td></tr>
<tr><td class="right">Min FPS:</td><td><div class="orange"><strong>31.8</strong></div></td></tr>
<tr><td class="right">Max FPS:</td><td><div class="orange"><strong>147.9</strong></div></td></tr>
</table>
<h2>System</h2>
<table class="detail">
<tr><td class="right">Platform:</td><td><div class="highlight">Linux 4.14.0-999-generic x86_64</div></td></tr>
<tr><td class="right">CPU model:</td><td><div class="highlight">Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz (3829MHz) x2</div></td></tr>
<tr><td class="right">GPU model:</td><td><div class="highlight">Unknown GPU (256MB) x1</div></td></tr>
</table>
<h2>Settings</h2>
<table class="detail">
<tr><td class="right">Render:</td><td><div class="highlight">OpenGL</div></td></tr>
<tr><td class="right">Mode:</td><td><div class="highlight">1680x1050 8xAA windowed</div></td></tr>
<tr><td class="right">Preset</td><td><div class="highlight">Custom</div></td></tr>
<tr><td class="right">Quality</td><td><div class="highlight">High</div></td></tr>
<tr><td class="right">Tessellation:</td><td>Disabled</td></tr>
</table>
<div class="engine">Powered by <a href="http://unigine.com/products/unigine/">UNIGINE Engine</a></div>
<div class="copyright"><a href="http://unigine.com/">Unigine Corp.</a> &copy; 2005-2013</div>
</body></html>


<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html><head>

<h1>Unigine Heaven Benchmark 4.0 -- Crossfire windows 10 latest ATI/AMD driver</h1>
<table class="result">
<tr><td class="right">FPS:</td><td><div class="orange"><strong>56.4</strong></div></td></tr>
<tr><td class="right">Score:</td><td><div class="orange"><strong>1422</strong></div></td></tr>
<tr><td class="right">Min FPS:</td><td><div class="orange"><strong>8.6</strong></div></td></tr>
<tr><td class="right">Max FPS:</td><td><div class="orange"><strong>99.5</strong></div></td></tr>
</table>
<h2>System</h2>
<table class="detail">
<tr><td class="right">Platform:</td><td><div class="highlight">Windows NT 6.2 (build 9200) 64bit</div></td></tr>
<tr><td class="right">CPU model:</td><td><div class="highlight">Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz (3829MHz) x2</div></td></tr>
<tr><td class="right">GPU model:</td><td><div class="highlight">AMD Radeon HD 5800 Series 15.201.1151.1008 (1024MB) x2</div></td></tr>
</table>
<h2>Settings</h2>
<table class="detail">
<tr><td class="right">Render:</td><td><div class="highlight">Direct3D11</div></td></tr>
<tr><td class="right">Mode:</td><td><div class="highlight">1680x1050 8xAA fullscreen</div></td></tr>
<tr><td class="right">Preset</td><td><div class="highlight">Custom</div></td></tr>
<tr><td class="right">Quality</td><td><div class="highlight">High</div></td></tr>
<tr><td class="right">Tessellation:</td><td>Disabled</td></tr>
</table>
<div class="engine">Powered by <a href="http://unigine.com/products/unigine/">UNIGINE Engine</a></div>
<div class="copyright"><a href="http://unigine.com/">Unigine Corp.</a> &copy; 2005-2013</div>
</body></html>
