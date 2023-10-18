cmake_minimum_required(VERSION 3.2)
project(AXon_user)

set(CMAKE_CXX_STANDARD 17)

# ***************************************
# OpenCV


find_package( OpenCV REQUIRED )
include_directories( ${OpenCV_INCLUDE_DIRS} )

# ***************************************

# ***************************************
# OpenNI

include_directories(/usr/include/openni2)


# ***************************************


add_executable(AXon main.cpp Viewer.cpp Viewer.h AXonLink.h OniSampleUtilities.h)
target_link_libraries( AXon  ${OpenCV_LIBS} ${OPENNI2_LIBRARY})