file(GLOB COMMON_SOURCE_FILES [!main]*.cpp)

set(CMAKE_CXX_FLAGS "-fstandalone-debug")

add_executable(${PROJECT_NAME} ${COMMON_SOURCE_FILES} main.cpp)

SET(CTEST_OUTPUT_ON_FAILURE TRUE)

file(GLOB TEST_SOURCE_FILES test/*.cpp)
add_executable(unit_tests ${TEST_SOURCE_FILES} ${COMMON_SOURCE_FILES})
target_link_libraries(unit_tests gtest_main)
gtest_discover_tests(unit_tests)