set(GAME_MODULE_C_FILES
    ai_cast.c
    ai_cast_characters.c
    ai_cast_debug.c
    ai_cast_events.c
    ai_cast_fight.c
    ai_cast_func_attack.c
    ai_cast_func_boss1.c
    ai_cast_funcs.c
    ai_cast_script.c
    ai_cast_script_actions.c
    ai_cast_script_ents.c
    ai_cast_sight.c
    ai_cast_think.c
    bg_animation.c
    bg_misc.c
    bg_pmove.c
    bg_slidemove.c
    g_active.c
    g_alarm.c
    g_bot.c
    g_client.c
    g_cmds.c
    g_combat.c
    g_items.c
    g_main.c
    g_mem.c
    g_misc.c
    g_missile.c
    g_mover.c
    g_props.c
    g_save.c
    g_script.c
    g_script_actions.c
    g_session.c
    g_spawn.c
    g_svcmds.c
    g_syscalls.c
    g_target.c
    g_team.c
    g_tramcar.c
    g_trigger.c
    g_utils.c
    g_weapon.c
    q_math.c
    q_shared.c
)

add_custom_command(
    COMMENT "generating g_funcs.h and g_func_decs.h"
    WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}"
    COMMAND
        "$<TARGET_FILE:extractfuncs>"
        *.c
        "${CMAKE_CURRENT_BINARY_DIR}/include"
    DEPENDS
        extractfuncs
        ${GAME_MODULE_C_FILES}
    OUTPUT
        "${CMAKE_CURRENT_BINARY_DIR}/include/g_funcs.h"
        "${CMAKE_CURRENT_BINARY_DIR}/include/g_func_decs.h"
)

add_library(game SHARED
    "${CMAKE_CURRENT_BINARY_DIR}/include/g_funcs.h"
    "${CMAKE_CURRENT_BINARY_DIR}/include/g_func_decs.h"
    game.def
    ${GAME_MODULE_C_FILES}
    ../botai/ai_chat.c
    ../botai/ai_cmd.c
    ../botai/ai_dmnet.c
    ../botai/ai_dmq3.c
    ../botai/ai_main.c
    ../botai/ai_team.c
)
target_include_directories(game PRIVATE "${CMAKE_CURRENT_BINARY_DIR}/include")
target_compile_definitions(game PRIVATE GAMEDLL)
target_link_libraries(game PRIVATE winmm)
set_target_properties(game PROPERTIES OUTPUT_NAME qagamex86)

install(TARGETS game DESTINATION ".")