cmake_minimum_required(VERSION 3.8)
project(tinyxml2)

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
  tinyxml2
  URL https://github.com/leethomason/tinyxml2/archive/refs/tags/10.0.0.tar.gz
  # SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/ext/
)

set(tinyxml2_SHARED_LIBS ON)
set(CMAKE_BUILD_TYPE Release)
set(tinyxml2_BUILD_TESTING OFF)

FetchContent_MakeAvailable(tinyxml2)
