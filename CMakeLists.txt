cmake_minimum_required(VERSION 2.8.3)
project(asr_sick_lms_400)

#use c++ 11
add_definitions(-std=gnu++0x)

find_package(catkin REQUIRED COMPONENTS
  roscpp
)

include_directories(include 
    ${catkin_INCLUDE_DIRS} 
    ${CMAKE_CURRENT_BINARY_DIR}
    )

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES asr_sick_lms_400)
  



add_library(asr_sick_lms_400
    src/sick_lms400.cpp
  )
 
target_link_libraries(asr_sick_lms_400
    ${catkin_LIBRARIES}
    ${ROS_LIBRARIES}
)
 
add_dependencies(asr_sick_lms_400
	${catkin_EXPORTED_TARGETS}
)


install(TARGETS asr_sick_lms_400
ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY include/${PROJECT_NAME}/
   DESTINATION ${CATKIN_GLOBAL_INCLUDE_DESTINATION}
   FILES_MATCHING PATTERN ".h" 
)