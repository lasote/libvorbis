SET(BII_LIB_SRC
    lib/analysis.c
    lib/bitrate.c
    lib/block.c
    lib/codebook.c
    lib/envelope.c
    lib/floor0.c
    lib/floor1.c
    lib/info.c
    lib/lookup.c
    lib/lpc.c
    lib/lsp.c
    lib/mapping0.c
    lib/mdct.c
    lib/psy.c
    lib/registry.c
    lib/res0.c
    lib/sharedbook.c
    lib/smallft.c
    lib/synthesis.c
    lib/vorbisenc.c
    lib/window.c
	lib/vorbisfile.c
)


IF(MSVC)
    ADD_DEFINITIONS(/D_UNICODE /DUNICODE)
    LIST(APPEND BII_LIB_SRC win32/vorbis.def)
ENDIF(MSVC)

LIST(APPEND BII_vq_distribution_SRC vq/bookutil.c)
LIST(APPEND BII_vq_huffbuild_SRC vq/bookutil.c)
LIST(APPEND BII_vq_latticebuild_SRC vq/bookutil.c)
LIST(APPEND BII_vq_latticetune_SRC vq/bookutil.c)

LIST(APPEND BII_test_test_SRC test/util.c)


ADD_BIICODE_TARGETS()

if(MINGW)
    target_compile_options(${BII_LIB_TARGET} PUBLIC "-std=gnu++11")
endif()