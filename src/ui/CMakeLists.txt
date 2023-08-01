add_library(ui SHARED
    ui.def
    ui_atoms.c
    ui_gameinfo.c
    ui_main.c
    ui_players.c
    ui_shared.c
    ui_syscalls.c
    ui_util.c
    ../game/bg_misc.c
    ../game/q_math.c
    ../game/q_shared.c
)
target_compile_definitions(ui PRIVATE _USRDLL UI_EXPORTS)
target_link_libraries(ui PRIVATE odbc32 odbccp32)
set_target_properties(ui PROPERTIES OUTPUT_NAME uix86)

install(TARGETS ui DESTINATION ".")