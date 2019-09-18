cmake_minimum_required(VERSION 2.6)
project(libaudio_converter)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "-D__STDC_CONSTANT_MACROS")
set(AVCODEC_INCLUDE_DIR include)
set(AVUTIL_INCLUDE_DIR include)

find_path(AVCODEC_INCLUDE_DIR avcodec/avcodec.h)
find_library(AVCODEC_LIBRARY avcodec)

find_path(AVUTIL_INCLUDE_DIR avutil/avutil.h)
find_library(AVUTIL_LIBRARY avutil)

add_executable(libaudio_converter src/main.c)
target_include_directories(libaudio_converter PRIVATE ${AVCODEC_INCLUDE_DIR} ${AVUTIL_INCLUDE_DIR} )
target_link_libraries(libaudio_converter PRIVATE ${AVCODEC_LIBRARY} ${AVUTIL_LIBRARY} m pthread z swresample rt)
