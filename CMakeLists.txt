cmake_minimum_required(VERSION 2.8)
project(nanoflann_colcon)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_CURRENT_LIST_DIR}/cmake")

include(ExternalProject)
externalproject_add(nanoflann_src
  GIT_REPOSITORY https://github.com/jlblancoc/nanoflann.git
  GIT_TAG v1.4.1 
  CONFIGURE_COMMAND cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX} ../nanoflann_src
  BUILD_COMMAND make
  INSTALL_COMMAND make install
)

install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION "include/${PROJECT_NAME}"
  FILES_MATCHING PATTERN "*.hpp"
)