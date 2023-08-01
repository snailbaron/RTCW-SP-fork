add_executable(extractfuncs
    extractfuncs.c
    l_log.c
    l_memory.c
    l_precomp.c
    l_script.c
)
target_compile_definitions(extractfuncs PRIVATE SCREWUP)