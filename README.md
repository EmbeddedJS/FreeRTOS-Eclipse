# FreeRTOS for Eclipse

### 필요 프로그램
- Eclipse
- GNU ARM Plugin
- ARM EABI Cross 컴파일러
- OpenOCD

### 폴더 및 파일
- Driver
  - CMSIS
  - STM32F2xx_HAL_Driver
  - BSP
- Middlewares
  - Thrid Party
    - FreeRTOS
- Include
- Src
- Utilities

### Define
- USE_HAL_DRIVER
- USE_STM322xG_EVAL
- STM32F207xx

### Include Path
- Drivers/STM32F2xx_HAL_Driver/Inc
- Drivers/BSP/Components/Common
- Drivers/BSP/Components/stmpe811
- Drivers/CMSIS/Include
- Include
- Middleware/Thrid_party/FreeRTOS/Include
- Middleware/Thrid_party/FreeRTOS/Source/portable/gcc/ARM_CM3
- Middleware/Third_party/FreeRTOS/CMSIS_RTOS
- Drivers/CMSIS/Device/ST/STM32F2xx/Incldue

### Startup
- startup_stm32f207xx.S
  반드시 s는 대문자
  
### Linker Script
- STM32F217IG_FLASH.ld

### OpenOCD and JTAG
#### Olimex ARM USB OCD
- openocd -f interface/olimex-arm-usb-ocd.cfg -f target/stm32f2x.cfg

### FreeRTOS Hard Fault Problem
FreeRTOSConfig.h에 아래와 같이 한줄 추가
#define configUSE_TIME_SLICING 0

### JTAG 접속 불가
main함수내의 GPIO_ConfigAN() 주석처리
(모든 GPIO 핀을 disable 시키는 함수, 전력소모 방지)
