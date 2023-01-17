 
## Minecraft Replay Mod Settings

## ffmpeg specific stuff
- ensure we are using the following ffmpeg:
  https://github.com/BtbN/FFmpeg-Builds/releases
  this is a fully built and linked instance of it

these are the original cli parameters for ffmpeg (fresh mod):
```-y -f rawvideo -pix_fmt bgra -s %WIDTH%x%HEIGHT% -r %FPS% -i - %FILTERS%-an -c:v libx264 -b:v %BITRATE% -pix_fmt yuv420p "%FILENAME%"```

So far I have tried something like this:
```-y -f rawvideo -pix_fmt bgra -s %WIDTH%x%HEIGHT% -r %FPS% -i - %FILTERS%-an -profile main -c:v hevc_nvenc -b:v %BITRATE% -pix_fmt yuv420p "%FILENAME%"```

this is per https://trac.ffmpeg.org/wiki/HWAccelIntro

You can see available presets (including lossless for both hevc and h264), other options, and encoder info with `ffmpeg -h encoder=h264_nvenc` or `ffmpeg -h encoder=hevc_nvenc`.

the currently used ffmpeg uses the following build config:
```
built with gcc 12.2.0 (crosstool-NG 1.25.0.90_cf9beb1)
configuration: --prefix=/ffbuild/prefix --pkg-config-flags=--static --pkg-config=pkg-config --cross-prefix=x86_64-w64-mingw32- --arch=x86_64 --target-os=mingw32 --enable-gpl --enable-version3 --disable-debug --disable-w32threads --enable-pthreads --enable-iconv --enable-libxml2 --enable-zlib --enable-libfreetype --enable-libfribidi --enable-gmp --enable-lzma --enable-fontconfig --enable-libvorbis --enable-opencl --disable-libpulse --enable-libvmaf --disable-libxcb --disable-xlib --enable-amf --enable-libaom --enable-libaribb24 --enable-avisynth --enable-chromaprint --enable-libdav1d --enable-libdavs2 --disable-libfdk-aac --enable-ffnvcodec --enable-cuda-llvm --enable-frei0r --enable-libgme --enable-libkvazaar --enable-libass --enable-libbluray --enable-libjxl --enable-libmp3lame --enable-libopus --enable-librist --enable-libssh --enable-libtheora --enable-libvpx --enable-libwebp --enable-lv2 --disable-libmfx --enable-libvpl --enable-openal --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libopenh264 --enable-libopenjpeg --enable-libopenmpt --enable-librav1e --enable-librubberband --enable-schannel --enable-sdl2 --enable-libsoxr --enable-libsrt --enable-libsvtav1 --enable-libtwolame --enable-libuavs3d --disable-libdrm --disable-vaapi --enable-libvidstab --enable-vulkan --enable-libshaderc --enable-libplacebo --enable-libx264 --enable-libx265 --enable-libxavs2 --enable-libxvid --enable-libzimg --enable-libzvbi --extra-cflags=-DLIBTWOLAME_STATIC --extra-cxxflags= --extra-ldflags=-pthread --extra-ldexeflags= --extra-libs=-lgomp --extra-version=20230116
```
which confirms, btw, that the required flags have been enabled during build, so I should not need to rebuild the app.

## Replay Mod Settings

To get a really fast render with the hardware acceleration you might to also consider leaving Anti-Aliasing turned off entirely.