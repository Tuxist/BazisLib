project(BazisLib)
cmake_minimum_required(VERSION 3.0)

if (WIN32)
    if(DEFINED ENV{DDKROOT})
        cmake_path(SET DDKROOT $ENV{DDKROOT})
    endif()

    file( GLOB bzCoreSrcs
        "bzscore/*.cpp"
        "bzscore/WinKernel/*.cpp"
        "bzscore/Win32/*.cpp"
        "bzscore/KEXT/*.cpp"
    )

    add_library(BazisCore STATIC ${bzCoreSrcs})

    target_include_directories(BazisCore PUBLIC
        ${DDKROOT}/inc
        ${DDKROOT}/inc/dkk
        ${CMAKE_SOURCE_DIR}/bzcore
    )

    target_compile_definitions(BazisCore PUBLIC SECURITY_KERNEL)

endif()
