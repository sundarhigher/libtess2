cmake_minimum_required(VERSION 3.12 FATAL_ERROR)

project(libtess2)

set(LIBTESS2_HDRS
	Source/bucketalloc.h
	Source/dict.h
	Source/geom.h
	Source/mesh.h
	Source/priorityq.h
	Source/sweep.h
	Source/tess.h
)

set(LIBTESS2_INCLUDES
	Include/tesselator.h
)

set(LIBTESS2_SRCS
	Source/bucketalloc.c
	Source/dict.c
	Source/geom.c
	Source/mesh.c
	Source/priorityq.c
	Source/sweep.c
	Source/tess.c
)

add_library(libtess2 STATIC ${LIBTESS2_SRCS} ${LIBTESS2_HDRS} ${LIBTESS2_INCLUDES})

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/Include)

file(WRITE "${CMAKE_BINARY_DIR}/libtess2-config.cmake" "include(\"\${CMAKE_CURRENT_LIST_DIR}/libtess2-targets.cmake\")")
install(FILES "${CMAKE_BINARY_DIR}/libtess2-config.cmake" DESTINATION "share/libtess2/")

install(TARGETS libtess2 EXPORT libtess2-targets)

install(EXPORT libtess2-targets DESTINATION share/libtess2/)

install(FILES ${LIBTESS2_INCLUDES} DESTINATION include/libtess2)





