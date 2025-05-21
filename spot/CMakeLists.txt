cmake_minimum_required(VERSION 2.8.12)
project(spot)

set(CMAKE_BUILD_TYPE Release)

find_package(catkin REQUIRED COMPONENTS
  )

include(ExternalProject)

execute_process(COMMAND
  git config --global http.sslVerify false)

ExternalProject_Add(
  spot
  URL https://www.lrde.epita.fr/dload/spot/spot-2.13.tar.gz
  GIT_TAG spot-2-13
  CONFIGURE_COMMAND <SOURCE_DIR>/configure --prefix ${CMAKE_INSTALL_PREFIX} --disable-python
  #BUILD_COMMAND make -j10
  #INSTALL_COMMAND make install -j10
  )
