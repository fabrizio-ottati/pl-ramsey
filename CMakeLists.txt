cmake_minimum_required(VERSION 3.25)

project(impcore C)

set(IMPCORE_SOURCE_DIR
    "${CMAKE_CURRENT_SOURCE_DIR}/third_party/build-prove-compare-student-code/bare/impcore")

add_executable(impcore
    "${IMPCORE_SOURCE_DIR}/arith.c"
    "${IMPCORE_SOURCE_DIR}/definition-code.c"
    "${IMPCORE_SOURCE_DIR}/env.c"
    "${IMPCORE_SOURCE_DIR}/error.c"
    "${IMPCORE_SOURCE_DIR}/eval.c"
    "${IMPCORE_SOURCE_DIR}/exp-code.c"
    "${IMPCORE_SOURCE_DIR}/fun-code.c"
    "${IMPCORE_SOURCE_DIR}/impcore.c"
    "${IMPCORE_SOURCE_DIR}/imptests.c"
    "${IMPCORE_SOURCE_DIR}/lex.c"
    "${IMPCORE_SOURCE_DIR}/linestream.c"
    "${IMPCORE_SOURCE_DIR}/list-code.c"
    "${IMPCORE_SOURCE_DIR}/name.c"
    "${IMPCORE_SOURCE_DIR}/overflow.c"
    "${IMPCORE_SOURCE_DIR}/par-code.c"
    "${IMPCORE_SOURCE_DIR}/parse.c"
    "${IMPCORE_SOURCE_DIR}/print.c"
    "${IMPCORE_SOURCE_DIR}/printbuf.c"
    "${IMPCORE_SOURCE_DIR}/printfuns.c"
    "${IMPCORE_SOURCE_DIR}/tableparsing.c"
    "${IMPCORE_SOURCE_DIR}/tests.c"
    "${IMPCORE_SOURCE_DIR}/unicode.c"
    "${IMPCORE_SOURCE_DIR}/xdef-code.c"
    "${IMPCORE_SOURCE_DIR}/xdefstream.c"
)

target_include_directories(impcore PRIVATE "${IMPCORE_SOURCE_DIR}")
target_compile_features(impcore PRIVATE c_std_11)

if(CMAKE_C_COMPILER_ID MATCHES "GNU|Clang")
    target_compile_options(impcore PRIVATE
        -pedantic
        -Wall
        -Wextra
        -Werror
        -Wno-overlength-strings
    )
endif()

set_target_properties(impcore PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/bin"
)
