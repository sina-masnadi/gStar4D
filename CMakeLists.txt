cmake_minimum_required(VERSION 3.16)
#set(CMAKE_CUDA_HOST_COMPILER "/usr/bin/gcc-6")
#set(CMAKE_CUDA_FLAGS "${CMAKE_CUDA_FLAGS} -ccbin /usr/bin/gcc")
project(gstar4d CUDA)
#set(CMAKE_BUILD_TYPE Release)
set(INCLUDE_INSTALL_DIR ${CMAKE_INSTALL_PREFIX}/include)
#set(
#        CUDA_NVCC_FLAGS
#        ${CUDA_NVCC_FLAGS}; -gencode arch=compute_61,code=sm_61
#)
set(CMAKE_CXX_STANDARD 11)


include_directories(
        GDelaunay/Common
        GDelaunay/GDelaunay
        GDelaunay/Main
        GDelaunay/PBA
)
#set(GSTAR4D_HEADER_FILES
#        GDelaunay/Common/Config.h
#        GDelaunay/Common/CudaWrapper.h
#        GDelaunay/Common/DtRandom.cuh
#        GDelaunay/Common/Geometry.cuh
#        GDelaunay/Common/PerfTimer.cuh
#        GDelaunay/Common/STLWrapper.h
#        GDelaunay/Common/ThrustWrapper.h
#        GDelaunay/GDelaunay/GDelaunay.cuh
#        GDelaunay/GDelaunay/GDelCommon.h
#        GDelaunay/GDelaunay/GDelData.cuh
#        GDelaunay/GDelaunay/GDelHost.h
#        GDelaunay/GDelaunay/GDelKernels.cuh
#        GDelaunay/GDelaunay/GDelPredDevice.cuh
#        GDelaunay/GDelaunay/GDelShewchukDevice.cuh
##        GDelaunay/Main/Application.h
#        GDelaunay/PBA/pba3D.h
#        GDelaunay/PBA/pba3DKernel.h
#        GDelaunay/PBA/Pba.h
#        )
set(GSTAR4D_SOURCE_FILES
        GDelaunay/Common/predicates.c
        GDelaunay/Common/Config.h
        GDelaunay/Common/CudaWrapper.h
        GDelaunay/Common/DtRandom.cu
        GDelaunay/Common/DtRandom.cuh
        GDelaunay/Common/Geometry.cu
        GDelaunay/Common/Geometry.cuh
        GDelaunay/Common/PerfTimer.cuh
        GDelaunay/Common/STLWrapper.h
        GDelaunay/Common/ThrustWrapper.h
        GDelaunay/GDelaunay/GDelaunay.cu
        GDelaunay/GDelaunay/GDelaunay.cuh
        GDelaunay/GDelaunay/GDelCommon.cu
        GDelaunay/GDelaunay/GDelCommon.h
        GDelaunay/GDelaunay/GDelData.cu
        GDelaunay/GDelaunay/GDelData.cuh
        GDelaunay/GDelaunay/GDelHost.cu
        GDelaunay/GDelaunay/GDelHost.h
        GDelaunay/GDelaunay/GDelKernels.cu
        GDelaunay/GDelaunay/GDelKernels.cuh
        GDelaunay/GDelaunay/GDelPredDevice.cuh
        GDelaunay/GDelaunay/GDelPredKernels.cu
        GDelaunay/GDelaunay/GDelShewchukDevice.cuh
        GDelaunay/Main/Application.cu
        GDelaunay/Main/Application.cuh
        GDelaunay/Main/Main.cu
        GDelaunay/PBA/pba3D.h
        GDelaunay/PBA/pba3DHost.cu
        GDelaunay/PBA/pba3DKernel.h
        GDelaunay/PBA/Pba.cu
        GDelaunay/PBA/Pba.h
        )

add_executable(
        gstar4d
        ${GSTAR4D_SOURCE_FILES}
)

set_target_properties(
        gstar4d
        PROPERTIES
        CUDA_SEPARABLE_COMPILATION ON)

install(TARGETS gstar4d DESTINATION bin)
install(FILES ${GSTAR4D_SOURCE_FILES} DESTINATION ${INCLUDE_INSTALL_DIR}/libgstar4d)
