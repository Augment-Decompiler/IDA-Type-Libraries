
# <arch><sub>-<vendor>-<sys>-<abi>
list(APPEND TARGETLIST 
    x86_64-pc-windows 
    i386-pc-windows 
    arm-pc-windows
    )

set(TIL_NAME "msstl")
set(TIL_DESC "\"Microsoft STL headers for windows\"")

set(IDACLANG_ARGS "${IDACLANG_ARGS} --idaclang-log-all")
set(IDACLANG_ARGS "${IDACLANG_ARGS} --idaclang-tildesc ${TIL_DESC}")

set(INPUT_FILE "${CMAKE_CURRENT_SOURCE_DIR}/msstl.h")
set(MSSTL_SRC "${CMAKE_CURRENT_SOURCE_DIR}/src/STL")

set(CLANG_ARGV "${CLANG_ARGV} -ferror-limit=100")
set(CLANG_ARGV "${CLANG_ARGV} -x c++")
set(CLANG_ARGV "${CLANG_ARGV} -I${MSSTL_SRC}/stl/inc")


execute_process(
    COMMAND mkdir ${OUTDIR}
    COMMAND mkdir ${OUTDIR}/STL/
    COMMAND mkdir ${OUTDIR}/STL/MS
)

foreach(target IN LISTS TARGETLIST)
    set(TARGET_CLANG_ARGV "${CLANG_ARGV} -target ${target}")
    execute_process(
        COMMAND
        ${IDACLANG} ${IDACLANG_ARGS} --idaclang-tilname ${OUTDIR}/STL/MS/${target}-${TIL_NAME}.til ${TARGET_CLANG_ARGV} ${INPUT_FILE}
    )
    message("${IDACLANG} ${IDACLANG_ARGS} --idaclang-tilname ${OUTDIR}/STL/MS/${target}-${TIL_NAME}.til ${TARGET_CLANG_ARGV} ${INPUT_FILE} > ${OUTDIR}/STL/MS/${target}-${TIL_NAME}.log")
    
endforeach()