# CMakeList.txt: проект CMake для CMakeProject7; включите исходный код и определения,
# укажите здесь логику для конкретного проекта.
#
cmake_minimum_required (VERSION 3.8)

project ("CM")

# Добавьте источник в исполняемый файл этого проекта.
add_executable (CM "Tests.cpp" "CMakeProject7.h" "BitArray.cpp" "BitArray.h")

include(FetchContent)
FetchContent_Declare(
	googletest
	URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip
)


# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

enable_testing()

target_link_libraries(
  CM
  GTest::gtest_main
)

include(GoogleTest)
gtest_discover_tests(CM)