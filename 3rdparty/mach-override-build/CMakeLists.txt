set(SRC_DIR "${CMAKE_CURRENT_SOURCE_DIR}/../mach-override-src")

if(NOT EXISTS "${SRC_DIR}/README.markdown")
	message(FATAL_ERROR
		"\"${SRC_DIR}/README.markdown\" was not found.\n"
		"Please checkout the submodule:\n"
		"git submodule update --init --recursive"
	)
endif()

add_library(mach-override STATIC)

target_include_directories(mach-override PUBLIC SYSTEM ${SRC_DIR})

target_sources(mach-override
	PUBLIC
		"${SRC_DIR}/mach_override.h"
	PRIVATE
		"${SRC_DIR}/mach_override.c"
		"${SRC_DIR}/udis86.h"

		"${SRC_DIR}/libudis86/decode.c"
		"${SRC_DIR}/libudis86/decode.h"
		"${SRC_DIR}/libudis86/extern.h"
		"${SRC_DIR}/libudis86/input.c"
		"${SRC_DIR}/libudis86/input.h"
		"${SRC_DIR}/libudis86/itab.c"
		"${SRC_DIR}/libudis86/itab.h"
		"${SRC_DIR}/libudis86/syn.c"
		"${SRC_DIR}/libudis86/syn-att.c"
		"${SRC_DIR}/libudis86/syn-intel.c"
		"${SRC_DIR}/libudis86/syn.h"
		"${SRC_DIR}/libudis86/types.h"
		"${SRC_DIR}/libudis86/udint.h"
		"${SRC_DIR}/libudis86/udis86.c"
)

target_disable_warnings(mach-override)
