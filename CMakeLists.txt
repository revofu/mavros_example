cmake_minimum_required(VERSION 3.0.2)
project(offb_node)

find_package(catkin REQUIRED COMPONENTS
        mavros
        roscpp
        )
find_package(Boost REQUIRED COMPONENTS system thread)

catkin_package(
        LIBRARIES ${PROJECT_NAME}
        CATKIN_DEPENDS roscpp mavros
        DEPENDS Boost
)

include_directories(
        include
        ${catkin_INCLUDE_DIRS}
)

add_executable(${PROJECT_NAME}
        src/offb_node.cpp
        )

target_link_libraries(${PROJECT_NAME}
        ${catkin_LIBRARIES}
        ${Boost_LIBRARIES}
        )
install(TARGETS ${PROJECT_NAME} DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})
