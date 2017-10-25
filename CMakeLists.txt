cmake_minimum_required(VERSION 3.0.0)
project(mavlinkcom_catkin)


find_package(catkin REQUIRED)

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES ${PROJECT_NAME}
#  CATKIN_DEPENDS other_catkin_pkg
#  DEPENDS system_lib
)


set(CMAKE_CXX_STANDARD 11)


include_directories(
 ./
 include
 common_utils
 ${catkin_INCLUDE_DIRS}
)

LIST(APPEND MAVLINK_SOURCES "./common_utils/FileSystem.cpp")
LIST(APPEND MAVLINK_SOURCES "./common_utils/ThreadUtils.cpp")
LIST(APPEND MAVLINK_SOURCES "./src/MavLinkConnection.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/MavLinkFtpClient.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/MavLinkLog.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/MavLinkMessageBase.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/MavLinkMessages.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/MavLinkNode.cpp") 	
LIST(APPEND MAVLINK_SOURCES "./src/MavLinkTcpServer.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/MavLinkVehicle.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/MavLinkVideoStream.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/Semaphore.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/impl/MavLinkConnectionImpl.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/impl/MavLinkFtpClientImpl.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/impl/MavLinkNodeImpl.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/impl/MavLinkTcpServerImpl.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/impl/MavLinkVehicleImpl.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/impl/MavLinkVideoStreamImpl.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/serial_com/SerialPort.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/serial_com/TcpClientPort.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/serial_com/UdpClientPort.cpp") 
LIST(APPEND MAVLINK_SOURCES "./src/serial_com/SocketInit.cpp")
LIST(APPEND MAVLINK_SOURCES "./src/serial_com/wifi.cpp")
LIST(APPEND MAVLINK_SOURCES "./src/impl/linux/MavLinkFindSerialPorts.cpp")

add_library(${PROJECT_NAME} STATIC ${MAVLINK_SOURCES})

target_link_libraries(${PROJECT_NAME} ${catkin_LIBRARIES})

