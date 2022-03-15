cmake_minimum_required(VERSION 3.5)
project(IDA-Type-Libraries VERSION 1.0)

set (IDACLANG "E:/IDA_Pro_v7.5_Portable/idaclang.exe")
set (OUTDIR "${PROJECT_SOURCE_DIR}/out")

OPTION(STL_GNU_BUILD
       "Build IDA type libraries for GNU stl" ON)

OPTION(STL_MS_BUILD
       "Build IDA type libraries for Microsoft stl" OFF)

OPTION(STL_LLVM_BUILD
       "Build IDA type libraries for LLVM stl" OFF)

add_subdirectory(STL)
