cmake_minimum_required(VERSION 3.5)

project(sfml_template)
set (CMAKE_CXX_STANDARD 11)

add_executable(sfml_template main.cpp
)
execute_process(COMMAND git submodule update --init -- 3rdParty/SFML
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})

set(SFML_STATIC_LIBRARIES TRUE)

target_link_libraries(sfml_template PUBLIC sfml-graphics)

set_property(TARGET sfml_template PROPERTY VS_DEBUGGER_WORKING_DIRECTORY $<TARGET_FILE_DIR:sfml_template>)

add_subdirectory(3rdParty)