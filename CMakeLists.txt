cmake_minimum_required(VERSION 3.5)
project(
    "libfvad"
    VERSION 1.0.1
    LANGUAGES C
)

set(SOURCES
    src/common.h
    src/fvad.c
    src/signal_processing/division_operations.c
    src/signal_processing/energy.c
    src/signal_processing/get_scaling_square.c
    src/signal_processing/resample_48khz.c
    src/signal_processing/resample_by_2_internal.h
    src/signal_processing/resample_by_2_internal.c
    src/signal_processing/resample_fractional.c
    src/signal_processing/signal_processing_library.h
    src/signal_processing/spl_inl.h
    src/signal_processing/spl_inl.c
    src/vad/vad_core.h
    src/vad/vad_core.c
    src/vad/vad_filterbank.h
    src/vad/vad_filterbank.c
    src/vad/vad_gmm.h
    src/vad/vad_gmm.c
    src/vad/vad_sp.h
    src/vad/vad_sp.c
)

set(HEADERS include/fvad.h)

add_library(fvad STATIC ${SOURCES} ${HEADERS})
target_include_directories(
    fvad PUBLIC $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
)

set_property(TARGET fvad PROPERTY POSITION_INDEPENDENT_CODE 1)
install(TARGETS fvad DESTINATION lib)
install(DIRECTORY include DESTINATION .)
