The `vcgencmd` tool is used to output information from the VideoCore GPU on the Raspberry Pi.
To get a list of all commands supported by `vcgencmd`, use `vcgencmd commands`. Some useful commands and their required parameters are listed below.

**vcos**
The `vcos` command has two useful sub-commands:
- `version` displays the build date and version of the firmware on the VideoCore
- `log status` displays the error log status of the various VideoCore firmware areas

**version**
Displays the build date and version of the VideoCore firmware.

**get_throttled**
Returns the throttled state of the system. This is a bit pattern. A bit being set indicates the following meanings:

| Bit | Hexa    | Meaning                             |
| --- | ------- | ----------------------------------- |
| 0   | 0x1     | Undervoltage detected               |
| 1   | 0x2     | Arm frequency capped                |
| 2   | 0x4     | Currently throttled                 |
| 3   | 0x8     | Soft temperature limit active       |
| 16  | 0x10000 | Undervoltage has occurred           |
| 17  | 0x20000 | Arm frequency capping has occurred  |
| 18  | 0x40000 | Throttling has occurred             |
| 19  | 0x80000 | Soft temperature limit has occurred |

**measure_temp**
Returns the temperature of the SoC as measured by its internal temperature sensor. On Raspberry Pi 4, measure_temp pmic returns the temperature of the PMIC.

**measure_clock** [clock]
This returns the current frequency of the specified clock. Accepts the following clock values:


| Clock | Description                       |
| ----- | --------------------------------- |
| arm   | ARM core(s)                       |
| core  | GPU core                          |
| h264  | H.264 block                       |
| isp   | Image Sensor Pipeline             |
| v3d   | 3D block                          |
| uart  | UART                              |
| pwm   | PWM block (analogue audio output) |
| emmc  | SD card interface                 |
| pixel | Pixel valves                      |
| vec   | Analogue video encoder            |
| hdmi  | HDMI                              |
| dpi   | Display Parallel Interface        |

e.g. `vcgencmd measure_clock arm`

**measure_volts** [block]
Displays the current voltages used by the specific block. Accepts the following block values:

| block   | Description        |
| ------- | ------------------ |
| core    | VC4 core voltage   |
| sdram_c | SDRAM Core Voltage |
| sdram_i | SDRAM I/O voltage  |
| sdram_p | SDRAM Phy Voltage  |


##### otp_dump
Displays the content of the OTP (one-time programmable) memory inside the SoC. These are 32-bit values, indexed from 8 to 64. See the OTP bits page for more details.

##### get_config [configuration item|int|str]
Displays the value of the configuration setting specified: alternatively, specify either int (integer) or str (string) to see all configuration items of the given type. For example, the following command returns the total memory on the device in megabytes:
`vcgencmd get_config total_mem`

##### get_mem type
Reports on the amount of memory addressable by the Arm and the GPU. To show the amount of Arm-addressable memory, use `vcgencmd get_mem arm`; to show the amount of GPU-addressable memory, use `vcgencmd get_mem gpu`. On devices with more than 1GB of memory, the `arm` parameter will always return 1GB minus the `gpu` memory value, since the GPU firmware is only aware of the first 1GB of memory. To get an accurate report of the total memory on the device, see the `total_mem` configuration item and the [[#**get_config** [configuration item int str|get_config]] section above.

##### codec_enabled [type]
Reports whether the specified codec type is enabled. Possible options for type are AGIF, FLAC, H263, H264, MJPA, MJPB, MJPG, MPG2, MPG4, MVC0, PCM, THRA, VORB, VP6, VP8, WMV9, WVC1. Note that because the H.265 HW block on the Raspberry Pi 4 and 400 is not part of the VideoCore GPU, its status is not accessed via this command.

##### mem_oom
Displays statistics on any OOM (out of memory) events occurring in the VideoCore memory space.

##### mem_reloc_stats
Displays statistics from the relocatable memory allocator on the VideoCore.

##### read_ring_osc
Returns the current speed, voltage and temperature of the ring oscillator.