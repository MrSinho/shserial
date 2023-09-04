# shserial

A simple Windows and Unix serial communication library using the win32 api and posix, written in C.

[![linux_badge](.ShCI/linux-status.svg)](https://github.com/MrSinho/ShSerial/tree/main/.ShCI/linux-log.md)
[![windows_badge](.ShCI/windows-status.svg)](https://github.com/MrSinho/ShSerial/tree/main/.ShCI/windows-log.md)

## Getting started

```bash
git clone https://github.com/mrsinho/shserial.git
mkdir build 
cd build
cmake -DSH_SERIAL_BUILD_LOGGER=ON ..
cmake --build .
```

## Example:

See the logger example [here](logger/src/logger.c)

```c
#ifdef __cplusplus
extern "C" {
#endif//__cplusplus



#include <shserial/shSerial.h>

#include <stdio.h>



int main(
    int    argc, 
    char** argv
) {
    ShSerialHandle handle = SH_SERIAL_NULL_HANDLE;
    char*          port   = "";
    char           msg[2] = "";
    uint8_t        r      = 0;

    if (argc < 2) {
        port = "COM5";
    }
    else {
        port = argv[1];
    }

    r = shSerialOpen(
        port,                 //port
        9600,                 //baud_rate
        500,                  //read_timeout_ms
        SH_SERIAL_READ_WRITE, //flags
        &handle               //p_handle
    );
    
    shSerialError(
        r == 0,
        "main: cannot open serial port",
        return -1
    );

    for (;;) {
        
        uint32_t bytes_read = 0;

        r = shSerialRead(
            1,           //size
            msg,         //dst
            &bytes_read, //p_bytes_read
            handle       //handle
        );
        
        shSerialError(
            r == 0,
            "main: failed reading from serial port",
            return -1
        );

        if (bytes_read != 0) {
            printf(msg);
        }

        bytes_read = 0;
    }
    
    shSerialClose(handle);
    
#ifdef _WIN32
    system("pause");
#endif

    return 0;
}



#ifdef __cplusplus
}
#endif//__cplusplus
```
