project(GeneralsCodeLibrariesSourceCompressionEAC)

set(HEADERS gimex.h codex.h btreecodex.h huffcodex.h refcodex.h)

set(SOURCES
    btreeabout.cpp
    btreedecode.cpp
    btreeencode.cpp
    huffabout.cpp
    huffdecode.cpp
    huffencode.cpp
    refabout.cpp
    refdecode.cpp
    refencode.cpp)

if(BUILD_SHARED_LIBS)
  add_library(${PROJECT_NAME} SHARED)
else()
  add_library(${PROJECT_NAME} STATIC)
endif()

target_compile_features(${PROJECT_NAME} PUBLIC cxx_std_23)
target_include_directories(${PROJECT_NAME} PUBLIC ${PROJECT_SOURCE_DIR})

target_sources(
  ${PROJECT_NAME}
  PUBLIC ${HEADERS}
  PRIVATE ${SOURCES})

add_library(Generals::Compression::EAC ALIAS ${PROJECT_NAME})
