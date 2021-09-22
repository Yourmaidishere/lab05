[![Build Status](https://app.travis-ci.com/Yourmaidishere/lab05.svg?branch=main)](https://app.travis-ci.com/Yourmaidishere/lab05)
[![Coverage Status](https://coveralls.io/repos/github/Yourmaidishere/lab05/badge.svg)](https://coveralls.io/github/Yourmaidishere/lab05)
Записала код в test.cpp, а для прохождения тестов подгрузила еще соответствующую библиотеку.
Добавила изменения в CMakeLists.txt для его корректной работы:
SET(COVERAGE OFF CACHE BOOL "Coverage")
enable_testing()
add_subdirectory(third-party/gtest)
include_directories(${gtest_SOURCE_DIR}/include ${gtest_SOURCE_DIR})

add_executable(runUnitTests test.cpp)
target_compile_options(runUnitTests PRIVATE --coverage)
target_link_libraries(runUnitTests PRIVATE --coverage gtest gtest_main)
add_test( runUnitTests runUnitTests )

Подключив Coveralls к GitHub, внесла в travis.yml:

before_install:
- pip install --user cpp-coveralls

after_success:
- coveralls --root . -E ".*gtest.*" -E ".*CMakeFiles.*"

