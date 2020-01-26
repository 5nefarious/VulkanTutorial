cmake_minimum_required (VERSION 3.12)

if(DEFINED ENV{VCPKG_ROOT} AND NOT DEFINED CMAKE_TOOLCHAIN_FILE)
  set(CMAKE_TOOLCHAIN_FILE "$ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake"
      CACHE STRING "")
endif()

project (VulkanTutorial CXX)

set (CMAKE_CXX_STANDARD 17)

find_package (Vulkan REQUIRED)
find_package (glfw3 CONFIG REQUIRED)
find_package (glm CONFIG REQUIRED)

add_subdirectory (shaders)

add_executable (hello hello.cpp)
add_dependencies (hello shaders)
target_link_libraries (hello PRIVATE Vulkan::Vulkan glfw glm)
