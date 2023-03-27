# Generated Cmake Pico project file

cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# Initialise pico_sdk from installed location
# Pull in Raspberry Pi Pico SDK (must be before project)
include(pico_sdk_import.cmake)

project(ds1631 C CXX ASM)

# Initialise the Raspberry Pi Pico SDK
pico_sdk_init()

# Add executable. Default name is the project name, version 0.1
add_executable(ds1631 main.c )

pico_set_program_name(ds1631 "ds1631")
pico_set_program_version(ds1631 "0.1")

pico_enable_stdio_uart(ds1631 1)
pico_enable_stdio_usb(ds1631 1)

target_sources(ds1631 PRIVATE
        ${CMAKE_CURRENT_LIST_DIR}/main.c
        ${CMAKE_CURRENT_LIST_DIR}/loop.c
        ${CMAKE_CURRENT_LIST_DIR}/blinker.c
        ${CMAKE_CURRENT_LIST_DIR}/ds1631.c
        )

# Add the standard library to the build
target_link_libraries(ds1631 pico_stdlib)

# Add any user requested libraries
target_link_libraries(ds1631
        hardware_timer
	hardware_i2c
        )


