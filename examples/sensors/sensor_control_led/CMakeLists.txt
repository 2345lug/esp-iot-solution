# The following lines of boilerplate have to be in your project's
# CMakeLists in this exact order for cmake to work correctly
cmake_minimum_required(VERSION 3.5)

#If IOT_SOLUTION_PATH is not defined, use relative path as default value
if(NOT DEFINED ENV{IOT_SOLUTION_PATH})
    get_filename_component(IOT_SOLUTION_PATH "${CMAKE_SOURCE_DIR}/../../.." ABSOLUTE)
    set(ENV{IOT_SOLUTION_PATH} ${IOT_SOLUTION_PATH})
    message(WARNING "IOT_SOLUTION_PATH not set, using default $ENV{IOT_SOLUTION_PATH}")
endif()

set(EXTRA_COMPONENT_DIRS ${EXTRA_COMPONENT_DIRS}
                        $ENV{IOT_SOLUTION_PATH}/components/button
                        $ENV{IOT_SOLUTION_PATH}/components/bus
                        $ENV{IOT_SOLUTION_PATH}/components/sensors
                        $ENV{IOT_SOLUTION_PATH}/components/sensors/gesture
                        $ENV{IOT_SOLUTION_PATH}/components/sensors/humiture
                        $ENV{IOT_SOLUTION_PATH}/components/sensors/imu
                        $ENV{IOT_SOLUTION_PATH}/components/sensors/light_sensor
                        $ENV{IOT_SOLUTION_PATH}/components/sensors/pressure
                        )

include($ENV{IDF_PATH}/tools/cmake/project.cmake)

project(sensors_monitor)
