cmake_minimum_required(VERSION 3.8)
project(flann_vendor)

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
  flann
  URL https://github.com/flann-lib/flann/archive/refs/tags/1.9.2.tar.gz
  SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/ext/
)

set(BUILD_PYTHON_BINDINGS OFF)
set(BUILD_MATLAB_BINDINGS OFF)
set(BUILD_EXAMPLES OFF)
set(BUILD_TESTS OFF)
set(BUILD_DOC OFF)

FetchContent_MakeAvailable(flann)
