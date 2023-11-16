cmake_minimum_required(VERSION 3.10)
project(ogre_next_vendor)

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_vendor_package REQUIRED)

ament_vendor(ogre_next_vendor
  VCS_URL https://github.com/OGRECave/ogre-next.git
  VCS_VERSION master
  CMAKE_ARGS
    -DOGRE_STATIC:BOOL=OFF
    -DOGRE_BUILD_COMPONENT_OVERLAY:BOOL=ON
    -DOGRE_BUILD_COMPONENT_PLANAR_REFLECTIONS:BOOL=ON
    -DOGRE_BUILD_PLUGIN_PFX:BOOL=ON
    -DOGRE_BUILD_RENDERSYSTEM_GL3PLUS:BOOL=ON
    -DOGRE_BUILD_RENDERSYSTEM_VULKAN:BOOL=ON
    -DOGRE_BUILD_SAMPLES2:BOOL=OFF
    -DOGRE_BUILD_TESTS:BOOL=OFF
    -DOGRE_BUILD_TOOLS:BOOL=OFF
    -DOGRE_GLSUPPORT_USE_EGL_HEADLESS:BOOL=ON
    -DOGRE_GLSUPPORT_USE_GLX:BOOL=ON
    -DOGRE_VULKAN_WINDOW_NULL:BOOL=ON
    -DOGRE_VULKAN_WINDOW_XCB:BOOL=ON
    -DOGRE_USE_NEW_PROJECT_NAME:BOOL=ON
  PATCHES patches
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package(
  CONFIG_EXTRAS_POST "ogre_next_vendor-extras.cmake.in"
)
