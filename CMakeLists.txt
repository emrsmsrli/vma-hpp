cmake_minimum_required(VERSION 3.0)

project(vma-hpp VERSION 1.0.0
    DESCRIPTION "C++ bindings for the VulkanMemoryAllocator library."
    LANGUAGES CXX)

find_package(Vulkan REQUIRED)

add_library(vma-hpp
        include/priv/vk_mem_alloc.h
        include/vulkan_mem_alloc/alloc.hpp
        include/vulkan_mem_alloc/alloc_enums.hpp
        include/vulkan_mem_alloc/alloc_funcs.hpp
        include/vulkan_mem_alloc/alloc_handles.hpp
        include/vulkan_mem_alloc/alloc_raii.hpp
        include/vulkan_mem_alloc/alloc_structs.hpp
        src/VmaUsage.h
        src/VmaUsage.cpp)

add_library(Vulkan::MemoryAllocatorHpp ALIAS vma-hpp)

target_include_directories(vma-hpp PUBLIC include/)
target_link_libraries(vma-hpp PUBLIC Vulkan::Headers)
