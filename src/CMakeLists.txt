include_directories(${PROJECT_SOURCE_DIR}/libhello)


# 加入一个配置头文件，用于处理 CMake 对源码的设置
configure_file (
        "${PROJECT_SOURCE_DIR}/config.h.in"
        "${PROJECT_BINARY_DIR}/config.h"
)

# 是否使用自己的 MathFunctions 库
option (USE_MYMATH
        "Use provided math implementation" OFF)

# 是否加入 MathFunctions 库
if (USE_MYMATH)
    include_directories ("${PROJECT_SOURCE_DIR}/math")
    set (EXTRA_LIBS ${EXTRA_LIBS} MathFunctions)
endif (USE_MYMATH)


set (EXTRA_LIBS ${EXTRA_LIBS} libhello)

aux_source_directory(. APP_SRC)
add_executable(hello ${APP_SRC})

target_link_libraries(hello ${EXTRA_LIBS})
