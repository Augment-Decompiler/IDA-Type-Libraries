
# <arch><sub>-<vendor>-<sys>-<abi>
list(APPEND TARGETLIST 
    x86_64-linux-gnu
    # i386-pc-linux-gnu
    # arm-pc-linux-gnu
    )

set(TIL_NAME "gnuc++")
set(TIL_DESC "\"GNU STL headers for linux\"")

set(IDACLANG_ARGS "${IDACLANG_ARGS} --idaclang-log-all")
set(IDACLANG_ARGS "${IDACLANG_ARGS} --idaclang-tildesc ${TIL_DESC}")
set(INPUT_FILE "${CMAKE_CURRENT_SOURCE_DIR}/gnuc++.h")
set(GNUSTL_SRC "${CMAKE_CURRENT_SOURCE_DIR}/src/")


set(CLANG_ARGV "${CLANG_ARGV} -ferror-limit=100")
set(CLANG_ARGV "${CLANG_ARGV} -x c++")
set(CLANG_ARGV "${CLANG_ARGV} -std=c++11")


# set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/c++/10")
# set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/c++/10/parallel")
# set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/c++/10/tr1")
# set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/x86_64-linux-gnu")
# set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/x86_64-linux-gnu/c++/10/")
# set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/x86_64-linux-gnu/bits")
# set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/gcc-11.2.0/libstdc++-v3/include")
# set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/gcc-11.2.0/libstdc++-v3/include/parallel")
# set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/gcc-11.2.0/libstdc++-v3/include/tr1")
# set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/gcc-11.2.0/libstdc++-v3/include/std/")
# set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/gcc-11.2.0/gcc/ginclude/")
set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/usr_lib_gcc/x86_64-linux-gnu/9/include")
set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/usr_include/x86_64-linux-gnu")
set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/usr_include/x86_64-linux-gnu/c++/10")


set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/usr_include/c++/10")
set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/usr_include")
set(CLANG_ARGV "${CLANG_ARGV} -I${GNUSTL_SRC}/usr_local/include")

file(MAKE_DIRECTORY ${OUTDIR}/STL/GNU)

foreach(target IN LISTS TARGETLIST)

    file(TOUCH ${OUTDIR}/STL/GNU/${target}-${TIL_NAME}.log)
    # file(TOUCH ${OUTDIR}/STL/GNU/${target}-${TIL_NAME}.til)

    set(TARGET_CLANG_ARGV "${CLANG_ARGV} -target ${target}")
    # execute_process(
    #     COMMAND
    #     ${IDACLANG} ${IDACLANG_ARGS} --idaclang-tilname ${OUTDIR}/STL/MS/${target}-${TIL_NAME}.til ${TARGET_CLANG_ARGV} ${INPUT_FILE}
    # )
    message("${IDACLANG} ${IDACLANG_ARGS} --idaclang-tilname ${OUTDIR}/STL/GNU/${target}-${TIL_NAME}.til ${TARGET_CLANG_ARGV} ${INPUT_FILE} > ${OUTDIR}/STL/GNU/${target}-${TIL_NAME}.log")
    
endforeach()


