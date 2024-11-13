
# librdkafka

## 依赖

1. zlib is installed automatically from NuGet,
   but probably requires the NuGet VS extension.

2. OpenSSL-win32 must be installed in C:\OpenSSL-win32 and C:\OpenSSL-Win64


## Build with MSVC

### Release Build

```bash
> cmd
> "C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Auxiliary\Build\vcvars64.bat"
> cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=D:\devtools\librdkafka-2.6.0
> ninja & ninja install
```

### Debug Build

```bash
> cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Debug -DCMAKE_INSTALL_PREFIX=D:\devtools\librdkafka-2.6.0
```