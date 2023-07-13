cmake_minimum_required(VERSION 3.20.0)

set(CONF_FILE "")
list(APPEND CONF_FILE
    ${CMAKE_CURRENT_SOURCE_DIR}/conf/prj.conf
    ${CMAKE_CURRENT_SOURCE_DIR}/conf/rtt.conf
    ${CMAKE_CURRENT_SOURCE_DIR}/conf/tf.conf
)

find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
project(tensorflow_hello_world)

# These samples use local static initialization. Since Zephyr doesn't support the
# C++ ABI for thread-safe initialization of local statics and the constructors don't
# appear to require thread safety, we turn it off in the C++ compiler.
set(NO_THREADSAFE_STATICS $<TARGET_PROPERTY:compiler-cpp,no_threadsafe_statics>)
zephyr_compile_options($<$<COMPILE_LANGUAGE:CXX>:${NO_THREADSAFE_STATICS}>)

target_sources(app PRIVATE ./src/main.c)
