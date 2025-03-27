cmake_minimum_required(VERSION 3.8)
project(ceres_vendor)

set(ceres_vendor_MAJOR_VERSION 0)
set(ceres_vendor_MINOR_VERSION 0)
set(ceres_vendor_PATCH_VERSION 0)
set(ceres_vendor_VERSION
  ${ceres_vendor_MAJOR_VERSION}.${ceres_vendor_MINOR_VERSION}.${ceres_vendor_PATCH_VERSION})

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)


include(FetchContent)
FetchContent_Declare(
  ceres
  URL https://github.com/ceres-solver/ceres-solver/archive/refs/tags/2.1.0.tar.gz
  SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/ext/
)

set(MINIGLOG ON CACHE BOOL "Use a stripped down version of glog." FORCE)
set(GFLAGS OFF CACHE BOOL "Enable Google Flags." FORCE)
set(BUILD_SHARED_LIBS ON CACHE BOOL "Build Shared Library" FORCE)
set(BUILD_EXAMPLES OFF CACHE BOOL "BUILD_EXAMPLES" FORCE)
set(BUILD_TESTING OFF CACHE BOOL "BUILD_TESTING" FORCE)
set(BUILD_BENCHMARKS OFF CACHE BOOL "BUILD_BENCHMARKS" FORCE)
set(CMAKE_BUILD_TYPE Release)

FetchContent_MakeAvailable(ceres)
