
# This file was generated by the build system used internally in the Yandex monorepo.
# Only simple modifications are allowed (adding source-files to targets, adding simple properties
# like target_include_directories). These modifications will be ported to original
# ya.make files by maintainers. Any complex modifications which can't be ported back to the
# original buildsystem will not be accepted.


find_package(Python3 REQUIRED COMPONENTS Development)

add_library(python-driver-native INTERFACE)
target_link_libraries(python-driver-native INTERFACE
  contrib-libs-linux-headers
  contrib-libs-cxxsupp
  yutil
  library-query-engine
  python-driver-lib
  yt-yt-ytlib
  server-lib-chunk_pools
  Python3::Module
)

add_global_library_for(python-driver-native.global python-driver-native)
target_compile_options(python-driver-native.global PRIVATE
  -DPYCXX_PYTHON_2TO3
  -DPYCXX_6_2_COMPATIBILITY
  -DPy_LIMITED_API=0x03040000
  -Wno-register
)
target_link_libraries(python-driver-native.global PUBLIC
  contrib-libs-linux-headers
  contrib-libs-cxxsupp
  yutil
  library-query-engine
  python-driver-lib
  yt-yt-ytlib
  server-lib-chunk_pools
  Python3::Module
)
target_sources(python-driver-native.global PRIVATE
  ${CMAKE_SOURCE_DIR}/yt/yt/python/driver/native/driver.cpp
)
