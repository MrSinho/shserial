# ShSerial
![windows_badge](windows-status.svg)
## [Windows build logs:](https://github.com/MrSinho/ShCI)
  `Build ran for 9.53s`
```bash $shci call$
choco install -y curl mingw cmake
Chocolatey v0.11.2
Installing the following packages:
curl;mingw;cmake
By installing, you accept licenses for the packages.
curl v7.80.0 already installed.
 Use --force to reinstall, specify a version to install, or try upgrade.
mingw v11.2.0.07112021 already installed.
 Use --force to reinstall, specify a version to install, or try upgrade.
cmake v3.22.0 already installed.
 Use --force to reinstall, specify a version to install, or try upgrade.

Chocolatey installed 0/3 packages. 
 See the log for details (C:\ProgramData\chocolatey\logs\chocolatey.log).

Warnings:
 - cmake - cmake v3.22.0 already installed.
 Use --force to reinstall, specify a version to install, or try upgrade.
 - curl - curl v7.80.0 already installed.
 Use --force to reinstall, specify a version to install, or try upgrade.
 - mingw - mingw v11.2.0.07112021 already installed.
 Use --force to reinstall, specify a version to install, or try upgrade.

```

```bash $shci call$
mingw-get install gcc mingw32-make gdb

```

```bash $shci call$
cd ShSerial && mkdir build && cd build && cmake -G"MinGW Makefiles" -DSH_SERIAL_BUILD_EXAMPLE=ON .. && mingw32-make
-- The C compiler identification is GNU 6.3.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: C:/MinGW/bin/gcc.exe - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: C:/Users/sino3/Desktop/GitHub/ShCI-implementation/bin/ShSerial/build
[ 25%] Building C object CMakeFiles/ShSerial.dir/ShSerial/src/ShSerial.c.obj
[ 50%] Linking C static library ..\bin\libShSerial.a
[ 50%] Built target ShSerial
[ 75%] Building C object CMakeFiles/ShSerialExample.dir/ShSerialExample/src/ShSerialExample.c.obj
[100%] Linking C executable ..\bin\ShSerialExample.exe
[100%] Built target ShSerialExample
