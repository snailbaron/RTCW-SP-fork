add_library(splines STATIC
    math_angles.cpp
    math_matrix.cpp
    math_quaternion.cpp
    math_vector.cpp
    q_parse.cpp
    q_shared.cpp
    splines.cpp
    util_str.cpp
)
target_compile_definitions(splines PRIVATE _LIB)