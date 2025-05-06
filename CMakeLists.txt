cmake_minimum_required(VERSION 3.20)
project(libnya VERSION 1.0.1 LANGUAGES CXX)

# 定义 header-only 接口库
add_library(libnya INTERFACE)

# 添加 include 路径
target_include_directories(libnya INTERFACE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>)

# 安装头文件
install(DIRECTORY include/ DESTINATION include)

install(TARGETS libnya EXPORT libnyaTargets)
install(EXPORT libnyaTargets
    NAMESPACE libnya::
    DESTINATION lib/cmake/libnya)

# 安装 Config 文件
include(CMakePackageConfigHelpers)
configure_package_config_file(
    cmake/libnyaConfig.cmake.in
    ${CMAKE_CURRENT_BINARY_DIR}/libnyaConfig.cmake
    INSTALL_DESTINATION lib/cmake/libnya)

install(FILES
    ${CMAKE_CURRENT_BINARY_DIR}/libnyaConfig.cmake
    DESTINATION lib/cmake/libnya)