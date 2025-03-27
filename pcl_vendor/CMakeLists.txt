cmake_minimum_required(VERSION 3.8)
project(pcl_vendor)

set(tinyxml2_MAJOR_VERSION 0)
set(tinyxml2_MINOR_VERSION 0)
set(tinyxml2_PATCH_VERSION 0)
set(tinyxml2_VERSION
  ${tinyxml2_MAJOR_VERSION}.${tinyxml2_MINOR_VERSION}.${tinyxml2_PATCH_VERSION})

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

include(FetchContent)
FetchContent_Declare(
  pcl
  URL https://github.com/PointCloudLibrary/pcl/archive/refs/tags/pcl-1.13.1.tar.gz
  SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/ext/
)

set(WITH_LIBUSB OFF)
set(WITH_CUDA OFF)
set(WITH_PCAP OFF)
set(WITH_OPENGL OFF)

FetchContent_MakeAvailable(pcl)
