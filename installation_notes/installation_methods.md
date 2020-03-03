

Home assistant / velbus installation experience 

| Hardware       | OS             | Type of installation                        | Findings                                                     |
| -------------- | -------------- | ------------------------------------------- | ------------------------------------------------------------ |
| Rasberry pi 3b | hassos         | Flash micro SD card                         | Serial port is not accessible by velbus.  Hard to debug the container technology (apk add --no-cache python3, ...) |
| Rasberry pi 3b | raspbian       | Manual installation in venv                 | Serial port works for velbus but no supervisor tab in home assistant (so no node-red ...) |
| windows laptop | Virtual box VM | Boot VM from an image.                      | Access to velbus via velvserver (tcp).  Complete installation of home assistant |
| Rasberry pi 3b | raspbian lite  | Manual installation using docker containers | Serial port works for velbus and the home installation looks pretty complete |



