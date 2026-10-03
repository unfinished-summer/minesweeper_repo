cmake_minimum_required(VERSION 3.10)

project(Minesweeper LANGUAGES CXX)

# C++ 标准 + 中文编码（源文件是 UTF-8 无 BOM）
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if(MSVC)
    add_compile_options(/utf-8)
endif()

# ---- EasyX 依赖位置（本机 VS 目录，换电脑只需改这两行）----
set(EASYX_INCLUDE_DIR "C:/Program Files/Microsoft Visual Studio/18/Community/VC/Auxiliary/VS/include")
set(EASYX_LIB_DIR     "C:/Program Files/Microsoft Visual Studio/18/Community/VC/Auxiliary/VS/lib/x64")

add_executable(Minesweeper Minesweeper.cpp)

target_include_directories(Minesweeper PRIVATE ${EASYX_INCLUDE_DIR})
target_link_directories(Minesweeper PRIVATE ${EASYX_LIB_DIR})
target_link_libraries(Minesweeper PRIVATE EasyXw.lib)
target_compile_definitions(Minesweeper PRIVATE UNICODE _UNICODE)


# 每次编译后自动把 res 文件夹拷到 exe 旁边（复刻原 vcxproj 的"生成后事件"）
add_custom_command(                    # 注册一条自定义命令
    TARGET Minesweeper                 # 挂在 Minesweeper 目标上
    POST_BUILD                         # 时机：编译完成后执行
    COMMAND ${CMAKE_COMMAND} -E copy_directory   # 执行: cmake -E copy_directory
        "${CMAKE_CURRENT_SOURCE_DIR}/res"                    # 参数1：从源码目录的 res 拷
        "$<TARGET_FILE_DIR:Minesweeper>/res"                   # 参数2：拷到 exe 旁边的 res
)

