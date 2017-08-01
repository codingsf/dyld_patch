cmake_minimum_required(VERSION 3.8)
project(dyld_patch)
enable_language(C ASM)

set(CMAKE_CXX_STANDARD 11)

set(SOURCE_FILES main.cpp code/dyldLock.cpp
        code/dyldLock.h
        code/dyldLibSystemGlue.cpp
        #code/dyldAPIIsInLibSystem.cpp
        code/threadLocalVariables.cpp
        code/dyld_process_info.cpp
        code/dyld_process_info_notify.cpp
        code/start_glue.h
        code/vproc_priv.h
        code/dyld.h
        code/dyld-interposing.h
        code/dyld_gdb.h
        code/dyld_images.h
        code/dyld_priv.h
        code/dyld_process_info.h
        code/dyld_cache_format.h
        code/ImageLoader.h
        code/dyld_process_info_internal.h
        code/dyldLibSystemInterface.h
        code/dyldAPIs.cpp
        code/ImageLoaderMachO.cpp
        code/ImageLoaderMachO.h
        code/ImageLoaderMachOCompressed.cpp
        code/ImageLoaderMachOCompressed.h
        code/ImageLoaderMachOClassic.cpp
        code/ImageLoaderMachOClassic.h
        code/codesign.h
        code/dyld.cpp code/csr.h
        code/cpu_capabilities.h
        code/dyldSyscallInterface.h
        code/private.h
        code/_simple.h
        code/glue.cpp
        code/reason.h
        code/dyld_stub_binder.s
        code/start_glue.s
        code/threadLocalHelpers.s
        code/dyld_gdb.cpp
        code/ImageLoader.cpp
        code/dyldStartup.s
        code/ldysyms.h
        code/dyldInitialization.cpp)



link_libraries(/usr/lib/libSystem.B.dylib)
#SET(CMAKE_ASM_FLAGS "${CFLAGS} -x assembler-with-cpp")
#set_source_files_properties(code/dyld_stub_binder.s code/start_glue.s code/threadLocalHelpers.s PROPERTIES COMPILE_FLAGS "-x assembler-with-cpp")
#add_executable(dyld_patch ${SOURCE_FILES} code/dyld_stub_binder.s code/start_glue.s code/threadLocalHelpers.s )
add_executable(dyld_patch ${SOURCE_FILES})