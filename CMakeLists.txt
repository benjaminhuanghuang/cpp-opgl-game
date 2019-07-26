cmake_minimum_required(VERSION 3.7)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -stdlib=libc++")

project(cpp-opgl-game)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${PROJECT_SOURCE_DIR}/cmake/")

find_package(SDL2 REQUIRED)
find_package(SDL2_ttf REQUIRED)
find_package(SDL2_image REQUIRED)
find_package(OpenGL REQUIRED)

include_directories(${SDL2_INCLUDE_DIR}
                    ${SDL2_IMAGE_INCLUDE_DIR}
                    ${SDL2_TTF_INCLUDE_DIR} 
                    src)
                    
file(GLOB project_SRCS src/*.cpp) #src/*.h

add_executable(Main ${project_SRCS})

target_link_libraries(Main ${SDL2_LIBRARY}
                             ${SDL2_IMAGE_LIBRARY}
                             ${SDL2_TTF_LIBRARY})