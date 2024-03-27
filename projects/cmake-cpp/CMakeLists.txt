cmake_minimum_required(VERSION <<@CMAKE_CURRENT_VERSION@>>+)

project(<<@PROJECT_NAME@>> CXX)
set(CMAKE_CXX_STANDARD 20)

file(GLOB_RECURSE SOURCE_FILES ${CMAKE_SOURCE_DIR}/src/*.cpp)
file(GLOB_RECURSE HEADER_FILES ${CMAKE_SOURCE_DIR}/src/*.hpp)

add_executable(${PROJECT_NAME} ${HEADER_FILES} ${SOURCE_FILES})

set(LIBS ${LIBS})

if (USE_ASAN)
    message("Link config: Address Sanitizer")
    target_link_libraries(${PROJECT_NAME} ${LIBS} -fsanitize=address)
else ()
    message("Link config: Default")
    target_link_libraries(${PROJECT_NAME} ${LIBS})
endif()
