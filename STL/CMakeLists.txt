if (STL_GNU_BUILD)
    add_subdirectory(GNU)
endif()

if (STL_MS_BUILD)
    add_subdirectory(microsoft)
endif()

if (STL_LLVM_BUILD)
    add_subdirectory(LLVM)
endif()