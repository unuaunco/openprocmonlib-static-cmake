# Define executable

add_executable(openprocmon_test optest.cpp)

# Define static libprocmon library

# libprocmon links
set(PROCMON_LIBRARY ${CMAKE_SOURCE_DIR}/src/libprocmon/libprocmon.lib )
set(PROCMON_INCLUDE_DIR ${CMAKE_SOURCE_DIR}/include/libprocmon)

include_directories(${PROCMON_INCLUDE_DIR})

add_library(libprocmon STATIC IMPORTED)

set_target_properties(libprocmon PROPERTIES
  IMPORTED_LOCATION ${PROCMON_LIBRARY}
  INTERFACE_INCLUDE_DIRECTORIES ${PROCMON_INCLUDE_DIR}
)

set_target_properties(openprocmon_test PROPERTIES LINK_FLAGS "/MANIFESTUAC:\"level='requireAdministrator' uiAccess='false'\"")

target_link_libraries(openprocmon_test PRIVATE libprocmon)