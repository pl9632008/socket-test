cmake_minimum_required(VERSION 3.0)
project(mvtest)
find_package(OpenCV REQUIRED)
set(SRC src/main.cpp)

include_directories(include  ${OpenCV_INCLUDE_DIRS} include/mavlink2.0  /usr/local/include)
link_directories(/usr/local/lib)

add_executable(a ${SRC})

find_library(ser serial lib)

target_link_libraries(a ${OpenCV_LIBS} ${ser}  pthread uv)


add_executable(b src/server.cpp)
target_link_libraries(b ${OpenCV_LIBS} ${ser}  pthread uv)



add_executable(c src/ftpclient.cpp)
target_link_libraries(c curl)