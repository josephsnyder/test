cmake_minimum_required(VERSION 3.15)

project(test)

include(CTest)

SET(GCC_COVERAGE_COMPILE_FLAGS "-g -O0 -coverage -fprofile-arcs -ftest-coverage")
SET(GCC_COVERAGE_LINK_FLAGS    "-coverage -lgcov")
SET( CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} ${GCC_COVERAGE_COMPILE_FLAGS}" )
SET( CMAKE_EXE_LINKER_FLAGS  "${CMAKE_EXE_LINKER_FLAGS} ${GCC_COVERAGE_LINK_FLAGS}" )

add_executable(testExec test.cxx)
add_test(NAME exec    COMMAND "testExec")
add_test(NAME example COMMAND "echo" "test")
add_test(NAME examplenotrun  COMMAND "echod" "test")

add_test(NAME my_test COMMAND bash -c "
echo '<CTestMeasurementFile type=\"image/png\" name=\"ValidImage\">${CMAKE_CURRENT_SOURCE_DIR}/a.png</CTestMeasurementFile>'
echo '<CTestMeasurementFile type=\"image/png\" name=\"TestImage\">${CMAKE_CURRENT_SOURCE_DIR}/b.png</CTestMeasurementFile>'
exit 0
")
