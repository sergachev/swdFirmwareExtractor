cmake_minimum_required(VERSION 3.2)
project(swdFirmwareExtractor)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -std=c11")

add_definitions(-DSTM32L152xE -DUSE_HAL_DRIVER)

set(SRC_LIST
        Src/main.c
        Src/swd.c
        Src/target.c
        Src/uart.c
        Src/stm32l1xx_hal_msp.c
        Src/stm32l1xx_it.c
        Src/system_stm32l1xx.c

        Inc/main.h
        Inc/stm32l1xx_hal_conf.h
        Inc/stm32l1xx_it.h
        Inc/swd.h
        Inc/target.h
        Inc/uart.h
        Drivers/STM32L1xx_HAL_Driver/Inc/stm32l1xx_hal.h
        Drivers/STM32L1xx_HAL_Driver/Inc/stm32l1xx_hal_pwr.h
        Drivers/STM32L1xx_HAL_Driver/Inc/stm32l1xx_hal_rcc.h
        Drivers/STM32L1xx_HAL_Driver/Inc/stm32l1xx_hal_uart.h

        Drivers/STM32L1xx_HAL_Driver/Src/stm32l1xx_ll_gpio.c
        Drivers/STM32L1xx_HAL_Driver/Src/stm32l1xx_hal.c
        Drivers/STM32L1xx_HAL_Driver/Src/stm32l1xx_hal_gpio.c
        Drivers/STM32L1xx_HAL_Driver/Src/stm32l1xx_hal_uart.c
)

include_directories(
        Inc
        Drivers/STM32L1xx_HAL_Driver/Inc
        Drivers/STM32L1xx_HAL_Driver/Inc/Legacy
        Drivers/CMSIS/Device/ST/STM32L1xx/Include
        Drivers/CMSIS/Include
)

add_executable(${PROJECT_NAME} ${SRC_LIST})
