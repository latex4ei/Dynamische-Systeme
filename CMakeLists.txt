cmake_minimum_required(VERSION 2.8)

project(FS NONE)
include(UseLATEX)

add_custom_target(
	writegitid ALL
	COMMAND ${CMAKE_CURRENT_SOURCE_DIR}/write-gitid.sh
	WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
)

set(DRAWINGS
)

set(IMAGES
	img/Logo.pdf
	img/block.pdf
)

add_latex_document(
	DynSysFS.tex
	FORCE_PDF
  INPUTS ${DRAWINGS}
	IMAGES ${IMAGES}
	DEPENDS writegitid
)
