cmake_minimum_required(VERSION 3.16)

set(LIB_NAME QLive2dWidget)
add_library(${LIB_NAME} SHARED)

# Set directory paths.
set(STB_PATH /usr/include/stb)
set(RES_PATH /usr/share/cubism/Resources)

# Set project.
project(${LIB_NAME})

# Define output directory.
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/${LIB_NAME})
# Set configuration (Release and Debug only).
set(CMAKE_CONFIGURATION_TYPES Debug Release
  CACHE STRING "Configurations" FORCE
)
# Suppress generation of ZERO_CHECK project.
set(CMAKE_SUPPRESS_REGENERATION ON)

# Specify version of compiler.
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Add Cubism Core.
find_package(CubismCore REQUIRED)
find_package(CubismFramework REQUIRED)
# find_package(OpenGL REQUIRED)
find_package(Qt5 COMPONENTS OpenGL Widgets REQUIRED)

# Link libraries to app.
target_link_libraries(${LIB_NAME}
  ${CubismFramework_LIBRARIES}
  ${CubismCore_LIBRARIES}
  Qt5::OpenGL Qt5::Widgets
)

# Specify include directories.
target_include_directories(${LIB_NAME} PRIVATE ${STB_PATH})

target_sources(${LIB_NAME}
    PRIVATE
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppAllocator.cpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppAllocator.hpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppDefine.cpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppDefine.hpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppDelegate.cpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppDelegate.hpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppWavFileHandler.cpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppWavFileHandler.hpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppLive2DManager.cpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppLive2DManager.hpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppModel.cpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppModel.hpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppPal.cpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppPal.hpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppSprite.cpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppSprite.hpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppTextureManager.cpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppTextureManager.hpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppView.cpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/LAppView.hpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/TouchManager.cpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/TouchManager.hpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/openglhelper.hpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/QLive2dWidget.cpp
      ${CMAKE_CURRENT_SOURCE_DIR}/src/QLive2dWidget.hpp
)
