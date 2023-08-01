add_subdirectory(botlib)
add_subdirectory(cgame)
add_subdirectory(extractfuncs)
add_subdirectory(game)
add_subdirectory(renderer)
add_subdirectory(splines)
add_subdirectory(ui)

add_executable(wolf WIN32
    client/cl_cgame.c
    client/cl_cin.c
    client/cl_console.c
    client/cl_input.c
    client/cl_keys.c
    client/cl_main.c
    client/cl_net_chan.c
    client/cl_parse.c
    client/cl_scrn.c
    client/cl_ui.c
    qcommon/cm_load.c
    qcommon/cm_patch.c
    qcommon/cm_polylib.c
    qcommon/cm_test.c
    qcommon/cm_trace.c
    qcommon/cmd.c
    qcommon/common.c
    qcommon/cvar.c
    qcommon/files.c
    qcommon/huffman.c
    qcommon/md4.c
    qcommon/msg.c
    qcommon/net_chan.c
    game/q_math.c
    game/q_shared.c
    client/snd_adpcm.c
    client/snd_dma.c
    client/snd_mem.c
    client/snd_mix.c
    client/snd_wavelet.c
    server/sv_bot.c
    server/sv_ccmds.c
    server/sv_client.c
    server/sv_game.c
    server/sv_init.c
    server/sv_main.c
    server/sv_net_chan.c
    server/sv_snapshot.c
    server/sv_world.c
    qcommon/unzip.c
    qcommon/vm.c
    qcommon/vm_interpreted.c
    qcommon/vm_x86.c
    win32/win_input.c
    win32/win_main.c
    win32/win_net.c
    win32/win_shared.c
    win32/win_snd.c
    win32/win_syscon.c
    win32/win_wndproc.c
)
target_link_libraries(wolf PRIVATE
    botlib
    #cgame
    #game
    renderer
    splines
    #ui

    winmm
    wsock32
)
set_target_properties(wolf PROPERTIES OUTPUT_NAME WolfSP)
target_compile_definitions(wolf PRIVATE __USEA3D __A3D_GEOM)

install(TARGETS wolf DESTINATION ".")