#Copyright (c) Microsoft. All rights reserved.
#Licensed under the MIT license. See LICENSE file in the project root for full license information.

#this is CMakeLists.txt for iothub_client_sample_mqtt

macro(compileAsC99)
  if (CMAKE_VERSION VERSION_LESS "3.1")
    if (CMAKE_C_COMPILER_ID STREQUAL "GNU")
      set (CMAKE_C_FLAGS "--std=c99 ${CMAKE_C_FLAGS}")
      set (CMAKE_CXX_FLAGS "--std=c++11 ${CMAKE_CXX_FLAGS}")
    endif()
  else()
    set (CMAKE_C_STANDARD 99)
    set (CMAKE_CXX_STANDARD 11)
  endif()
endmacro(compileAsC99)

cmake_minimum_required(VERSION 2.8.11)

if(WIN32)
    message(FATAL_ERROR "This CMake file is only support Linux builds!")
endif()

add_library(cjson
    cJSON.c
    cJSON.h
)

set(AZUREIOT_INC_FOLDER "/usr/include/azureiot" "/usr/include/azureiot/inc")

include_directories(${AZUREIOT_INC_FOLDER})

set(iothub_client_sample_mqtt_c_files
    iothub_client_sample_mqtt.c
)

set(iothub_client_sample_mqtt_h_files
    iothub_client_sample_mqtt.h
)

add_executable(iothub_client_sample_mqtt ${iothub_client_sample_mqtt_c_files} ${iothub_client_sample_mqtt_h_files})

target_link_libraries(iothub_client_sample_mqtt
    cjson
    iothub_client
    iothub_client_mqtt_transport
    iothub_client_http_transport
    parson
    aziotsharedutil
    umqtt
    pthread
    curl
    ssl
    crypto
    m
)

