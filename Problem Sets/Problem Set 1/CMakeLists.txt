############################################################################
# <summary> CMakeLists.txt for OpenCV and CUDA. </summary>
# <date>    2012-02-07          </date>
# <author>  Quan Tran Minh. edit by Johannes Kast, Michael Sarahan </author>
# <email>   quantm@unist.ac.kr  kast.jo@googlemail.com msarahan@gmail.com</email>
############################################################################

# collect source files
cmake_minimum_required(VERSION 2.8)
project(HW1)
file( GLOB  hdr *.hpp *.h )
file( GLOB  cu  *.cu)
SET (HW1_files main.cpp reference_calc.cpp compare.cpp)


find_package( OpenCV REQUIRED )
message(STATUS "OpenCV library status:")
message(STATUS "    version: ${OpenCV_VERSION}")
message(STATUS "    libraries: ${OpenCV_LIBS}")
message(STATUS "    include path: ${OpenCV_INCLUDE_DIRS}")
include_directories( ${OpenCV_INCLUDE_DIRS} )

find_package(CUDA 7.5 REQUIRED)
include_directories ( ${CUDA_TOOLKIT_ROOT_DIR}/samples/common/inc/ )
message("CUDA_VERSION: " ${CUDA_VERSION} )
message("CUDA_CUDA_LIBRARY: " ${CUDA_CUDA_LIBRARY} )
message("CUDA_CUDART_LIBRARY: " ${CUDA_CUDART_LIBRARY} )
message("CUDA_NVCC_FLAGS: " ${CUDA_NVCC_FLAGS} )
message("CUDA_INCLUDE_DIRS: " ${CUDA_INCLUDE_DIRS} )
message("CUDA_CUBLAS_LIBRARIES: " ${CUDA_CUBLAS_LIBRARIES} )
message("CUDA_TOOLKIT_ROOT_DIR: " ${CUDA_TOOLKIT_ROOT_DIR} )


CUDA_ADD_EXECUTABLE(HW1 ${HW1_files} ${hdr} ${cu})
target_link_libraries( HW1 ${OpenCV_LIBS} )
