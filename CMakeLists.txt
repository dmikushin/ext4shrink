cmake_minimum_required(VERSION 3.1)

project(ext4shrink LANGUAGES NONE)

include(GNUInstallDirs)

install(PROGRAMS ${PROJECT_NAME} DESTINATION ${CMAKE_INSTALL_SBINDIR})
