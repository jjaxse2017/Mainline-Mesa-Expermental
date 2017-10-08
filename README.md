# Mainline-Mesa-Expermental

1.) Download the latest source code from https://github.com/mesa3d/mesa
2.) Copy the filed included into the mesa 3d source code (name changes ac_llvm_build.c to ac_llvm_build.cpp)
3.) run configure.ac (needed to generate a configure file /w the updated file name changes)
4.) copy either the 32 bit or 64 bit configure files over the newly generated configure file (needed to hard wire the configure optimization options listed below and remove debugging) and then run configure
the files will be located in the lib folder
5.) strip --strip-unneeded --remove-section=.comment lib/*
6.) Move the files into appropriate directory see the compiled radeon driver for instructions on how to run 

64bit (GCC6/LLVM5)

./configure CFLAGS='-march=core2 -O3' CXXFLAGS='-march=core2 -std=gnu++17' LLVM_CFLAGS='-march=core2 -O3' LLVM_CPPFLAGS='-march=core2 -O3 -std=gnu++17' --with-platforms='x11,drm' --with-gallium-drivers='r600,swrast,radeonsi' --with-dri-drivers='swrast,radeon' --enable-glx-tls --enable-xa --enable-osmesa --enable-texture-float --enable-gles1 -enable-gles2 --enable-gbm --enable-dri  --enable-glx --enable-opengl --enable-shared-glapi --enable-va --enable-vdpau --enable-dri3 --enable-llvm --with-vulkan-drivers='radeon' --enable-opencl --enable-opencl-icd



32bit

./configure CFLAGS='-pipe -m32 -march=core2 -O3' CXXFLAGS='-pipe -m32 -march=core2 -O3 -std=c++1z -std=c++17' CPPFLAGS='-pipe -march=core2 -O3 -std=gnu++1z' LLVM_CFLAGS='-pipe -m32 -march=core2 -O3' LLVM_CPPFLAGS='-pipe -m32 -march=core2 -O3 -std=c++1z -std=c++17' --with-platforms='x11,drm' --with-gallium-drivers='r600,swrast,radeonsi' --with-dri-drivers='swrast,radeon' --enable-glx-tls --enable-xa --enable-osmesa --enable-nine --enable-texture-float --enable-gles1 --enable-gles2 --enable-shared-glapi --enable-gbm --enable-dri  --enable-glx --enable-opengl --enable-va --enable-vdpau --enable-dri --enable-dri3 --enable-llvm --enable-llvm-shared-libs --with-vulkan-drivers='radeon' --host=i686-pc-linux-gnu --target=i686-pc-linux-gnu

#better off disable mmx/sse/3d now in the config file... cp /home/pi/Documents/mesa-master/src/mapi/entry_x86_tls.h /home/pi/Documents/mesa-master/src/mapi/entry_x86-64_tls.h

64bit2(GCC7/LLVM) Used for DRI/everything

./configure CFLAGS='-pipe -march=core2 -O3' CPPFLAGS='-pipe -march=core2 -O3 -std=gnu++1z' CXXFLAGS='-pipe -march=core2 -O3 -std=gnu++1z' LLVM_CFLAGS='-pipe -march=core2 -O3' LLVM_CPPFLAGS='-pipe -march=core2 -O3 -std=c++1z -std=c++17' LDFLAGS='-lstdc++ -lz' --with-platforms='x11,drm' --with-gallium-drivers='' --with-dri-drivers='swrast,radeon' --enable-glx-tls --enable-xa --enable-texture-float --enable-opengl --enable-glx --enable-gles1 -enable-gles2 --enable-gbm --enable-dri --enable-dri3  --enable-osmesa --enable-shared-glapi --enable-va --enable-vdpau  --enable-llvm --enable-llvm-shared-libs --with-vulkan-drivers='radeon'

64bit2(GCC7) Used for missing R600 driver

./configure CFLAGS='-pipe -march=core2 -O3' CPPFLAGS='-pipe -march=core2 -O3 -std=gnu++1z' CXXFLAGS='-pipe -march=core2 -O3 -std=gnu++1z' LLVM_CFLAGS='-pipe -march=core2 -O3' LLVM_CPPFLAGS='-pipe -march=core2 -O3 -std=c++1z -std=c++17' LDFLAGS='-lstdc++ -lz' --with-platforms='x11,drm' --with-gallium-drivers='r600,swrast,radeonsi' --with-dri-drivers='' --enable-glx-tls --enable-xa --enable-texture-float --enable-opengl --enable-glx --enable-gles1 -enable-gles2 --enable-gbm --enable-dri --enable-dri3  --enable-osmesa --enable-shared-glapi --enable-va --enable-vdpau --with-vulkan-drivers='radeon' --disable-gallium-llvm --disable-llvm
