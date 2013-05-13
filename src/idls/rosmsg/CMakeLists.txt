# Copyright: (C) 2013 iCub Facility
# Authors: Paul Fitzpatrick
# CopyPolicy: Released under the terms of the LGPLv2.1 or later, see LGPL.TXT

get_property(YARP_TREE_INCLUDE_DIRS TARGET YARP_OS PROPERTY INCLUDE_DIRS)
include_directories(${YARP_TREE_INCLUDE_DIRS})

include_directories(src)
add_executable(yarpidl_rosmsg src/main.cpp src/RosType.cpp src/RosTypeCodeGenYarp.cpp src/RosType.h src/RosTypeCodeGenYarp.h)

target_link_libraries(yarpidl_rosmsg YARP_init)

option(TEST_yarpidl_rosmsg "Test ROS msg based IDL" OFF)
if (TEST_yarpidl_rosmsg)
  add_subdirectory(tests)
endif ()