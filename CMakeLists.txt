project(test)

include(CTest)

add_executable(testExec test.cxx)
add_test(NAME exec    COMMAND "testExec")
add_test(NAME example COMMAND "echo" "test")
