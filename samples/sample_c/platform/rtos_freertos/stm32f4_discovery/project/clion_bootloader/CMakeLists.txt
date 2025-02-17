#THIS FILE IS AUTO GENERATED FROM THE TEMPLATE! DO NOT CHANGE!
set(CMAKE_SYSTEM_NAME Generic)
set(CMAKE_SYSTEM_VERSION 1)
cmake_minimum_required(VERSION 3.5)

# project settings
project(dji_sdk_demo_bootloader C CXX ASM)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_C_STANDARD 11)

add_definitions(-DUSE_HAL_DRIVER)
add_definitions(-DSTM32F407xx)
add_definitions(-DUSE_CMSIS_RTOS=1)
add_definitions(-DHSE_VALUE=8000000)
set(DEVICE STM32F407IG)
set(DEVICE_FAMILY STM32F40_41xxx)

#Uncomment for hardware floating point
add_compile_definitions(ARM_MATH_CM4;ARM_MATH_MATRIX_CHECK;ARM_MATH_ROUNDING)
add_compile_options(-mfloat-abi=hard -mfpu=fpv4-sp-d16)
add_link_options(-mfloat-abi=hard -mfpu=fpv4-sp-d16)

#Uncomment for software floating point
#add_compile_options(-mfloat-abi=soft)

add_compile_options(-mcpu=cortex-m4 -mthumb -mthumb-interwork)
add_compile_options(-ffunction-sections -fdata-sections -fno-common -fmessage-length=0)

# uncomment to mitigate c++17 absolute addresses warnings
#set(ADDITIONAL_CORE_FLAGS "-Wno-unused-function -Wno-missing-braces")
#set(CORE_FLAGS "-mthumb -mcpu=cortex-m4 -mlittle-endian -mfpu=fpv4-sp-d16 -mfloat-abi=softfp -mthumb-interwork --specs=nano.specs --specs=nosys.specs ${ADDITIONAL_CORE_FLAGS}")
set(CMAKE_C_FLAGS "${CORE_FLAGS} -fno-builtin -Wall -std=gnu99 -fdata-sections -ffunction-sections -g3 -gdwarf-2" CACHE INTERNAL "c compiler flags")
#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-register")

if ("${CMAKE_BUILD_TYPE}" STREQUAL "Release")
    message(STATUS "Maximum optimization for speed")
    add_compile_options(-Ofast)
elseif ("${CMAKE_BUILD_TYPE}" STREQUAL "RelWithDebInfo")
    message(STATUS "Maximum optimization for speed, debug info included")
    add_compile_options(-Ofast -g)
elseif ("${CMAKE_BUILD_TYPE}" STREQUAL "MinSizeRel")
    message(STATUS "Maximum optimization for size")
    add_compile_options(-Os)
else ()
    message(STATUS "Minimal optimization, debug info included")
    add_compile_options(-Og -g)
endif ()

include_directories(
        ../../../common
        ../../../common/osal
        ../../hal
        ../../application
        ../../bootloader
        ../../drivers/BSP
        ../../drivers/STM32F4xx_HAL_Driver/Inc
        ../../drivers/STM32F4xx_HAL_Driver/Inc/Legacy
        ../../drivers/CMSIS/Device/ST/STM32F4xx/Include
        ../../drivers/CMSIS/Include
        ../../middlewares/Third_Party/FreeRTOS/Source/include
        ../../middlewares/Third_Party/FreeRTOS/Source/portable/GCC/ARM_CM4F
)

add_definitions(-DUSE_HAL_DRIVER -DSTM32F407xx)

file(GLOB_RECURSE SOURCES
        "../../../common/*.c"
        "../../hal/*.c"
        "../../bootloader/*.c"
        "../../drivers/BSP/*.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_rcc.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_rcc_ex.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_flash.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_flash_ex.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_flash_ramfunc.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_cortex.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_dma.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_dma_ex.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_pwr.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_pwr_ex.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_gpio.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_tim.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_tim_ex.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_rng.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_can.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_i2c.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_i2c_ex.c"
        "../../drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_uart.c"
        "../../drivers/CMSIS/Device/ST/STM32F4xx/Source/Templates/system_stm32f4xx.c"
        "../../drivers/CMSIS/Device/ST/STM32F4xx/Source/Templates/gcc/startup_stm32f407xx.s"
        "../../middlewares/Third_Party/FreeRTOS/Source/portable/GCC/ARM_CM4F/port.c"
        "../../middlewares/Third_Party/FreeRTOS/Source/portable/MemMang/heap_4.c"
        "../../middlewares/Third_Party/FreeRTOS/Source/croutine.c"
        "../../middlewares/Third_Party/FreeRTOS/Source/event_groups.c"
        "../../middlewares/Third_Party/FreeRTOS/Source/list.c"
        "../../middlewares/Third_Party/FreeRTOS/Source/queue.c"
        "../../middlewares/Third_Party/FreeRTOS/Source/tasks.c"
        "../../middlewares/Third_Party/FreeRTOS/Source/timers.c"
        )

#[[ LINK SCRIPT ]]
set(FLASH_START 0x08000000)
set(FLASH_SIZE 1024k)
set(RAM_SIZE 128k)
set(CCMRAM_SIZE 64k)
set(HEAP_SIZE 0x800)
set(STACK_SIZE 0x800)

include_directories(../../../../../../../out/include)

configure_file(linker_script/stm32f407igt.ld.in ${CMAKE_CURRENT_BINARY_DIR}/stm32f407igt.ld)
get_filename_component(LINKER_SCRIPT ${CMAKE_CURRENT_BINARY_DIR}/stm32f407igt.ld ABSOLUTE)

add_link_options(-Wl,-gc-sections,--print-memory-usage,-Map=${PROJECT_BINARY_DIR}/${PROJECT_NAME}.map)
add_link_options(-mcpu=cortex-m4 -mthumb -mthumb-interwork)
add_link_options(-T ${LINKER_SCRIPT})

add_executable(${PROJECT_NAME}.elf ${SOURCES} ${LINKER_SCRIPT})

set(HEX_FILE ${PROJECT_BINARY_DIR}/${PROJECT_NAME}.hex)
set(BIN_FILE ${PROJECT_BINARY_DIR}/${PROJECT_NAME}.bin)

add_custom_command(TARGET ${PROJECT_NAME}.elf POST_BUILD
        COMMAND ${CMAKE_OBJCOPY} -Oihex $<TARGET_FILE:${PROJECT_NAME}.elf> ${HEX_FILE}
        COMMAND ${CMAKE_OBJCOPY} -Obinary $<TARGET_FILE:${PROJECT_NAME}.elf> ${BIN_FILE}
        COMMENT "Building ${HEX_FILE}
Building ${BIN_FILE}")

configure_file(${CMAKE_CURRENT_LIST_DIR}/download_script/download.jlink.in ${CMAKE_CURRENT_BINARY_DIR}/download.jlink)
configure_file(${CMAKE_CURRENT_LIST_DIR}/download_script/download.sh.in ${CMAKE_CURRENT_BINARY_DIR}/download.sh)
configure_file(${CMAKE_CURRENT_LIST_DIR}/debug_script/gdbserver.sh.in ${CMAKE_CURRENT_BINARY_DIR}/gdbserver.sh)
execute_process(COMMAND chmod 777 download.sh WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR})
execute_process(COMMAND chmod 777 gdbserver.sh WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR})