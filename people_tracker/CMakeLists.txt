cmake_minimum_required(VERSION 2.4.6)
include($ENV{ROS_ROOT}/core/rosbuild/rosbuild.cmake)

# Set the build type.  Options are:
#  Coverage       : w/ debug symbols, w/o optimization, w/ code-coverage
#  Debug          : w/ debug symbols, w/o optimization
#  Release        : w/o debug symbols, w/ optimization
#  RelWithDebInfo : w/ debug symbols, w/ optimization
#  MinSizeRel     : w/o debug symbols, w/ optimization, stripped binaries
#set(ROS_BUILD_TYPE RelWithDebInfo)

rosbuild_init()

#set the default path for built executables to the "bin" directory
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#set the default path for built libraries to the "lib" directory
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)
set(OPEN_NI_UNSTABLE "/home/liz/codescratch/ThirdpartyLibs/kinect12.04/openni/" CACHE STRING "Location of Unstable OpenNI")
set(OPEN_NITE_UNSTABLE "/home/liz/codescratch/ThirdpartyLibs/kinect12.04/nite/" CACHE STRING "Location of Unstable NITE")
include_directories("${OPEN_NI_UNSTABLE}/Include" "${NITE_UNSTABLE}/Include")
link_directories("${OPEN_NI_UNSTABLE}/Lib" "${NITE_UNSTABLE}/Lib")
#uncomment if you have defined messages
#rosbuild_genmsg()
#uncomment if you have defined services
#rosbuild_gensrv()

#common commands for building c++ executables and libraries
#rosbuild_add_library(${PROJECT_NAME} src/example.cpp)
#target_link_libraries(${PROJECT_NAME} another_library)
#rosbuild_add_boost_directories()
#rosbuild_link_boost(${PROJECT_NAME} thread)
rosbuild_add_executable(tracker src/followerPI.cpp)
target_link_libraries(tracker OpenNI)
