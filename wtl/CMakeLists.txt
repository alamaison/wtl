# Copyright 2016 Alexander Lamaison. All rights reserved.
#
# This file is a part of the Windows Template Library.
# The use and distribution terms for this software are covered by the
# Common Public License 1.0 (http://opensource.org/licenses/cpl.php)
# which can be found in the file CPL.TXT at the root of this distribution.
# By using this software in any fashion, you are agreeing to be bound by
# the terms of this license. You must not remove this notice, or
# any other, from this software.

option(BUILD_SAMPLES "Build sample projects" ON)

set(LIBRARY_DIRECTORY Include)
set(INSTALL_DIRECTORY include)

set(LIBRARY_SOURCES
  ${LIBRARY_DIRECTORY}/atlapp.h
  ${LIBRARY_DIRECTORY}/atlcrack.h
  ${LIBRARY_DIRECTORY}/atlctrls.h
  ${LIBRARY_DIRECTORY}/atlctrlw.h
  ${LIBRARY_DIRECTORY}/atlctrlx.h
  ${LIBRARY_DIRECTORY}/atlddx.h
  ${LIBRARY_DIRECTORY}/atldlgs.h
  ${LIBRARY_DIRECTORY}/atldwm.h
  ${LIBRARY_DIRECTORY}/atlfind.h
  ${LIBRARY_DIRECTORY}/atlframe.h
  ${LIBRARY_DIRECTORY}/atlgdi.h
  ${LIBRARY_DIRECTORY}/atlmisc.h
  ${LIBRARY_DIRECTORY}/atlprint.h
  ${LIBRARY_DIRECTORY}/atlres.h
  ${LIBRARY_DIRECTORY}/atlresce.h
  ${LIBRARY_DIRECTORY}/atlribbon.h
  ${LIBRARY_DIRECTORY}/atlscrl.h
  ${LIBRARY_DIRECTORY}/atlsplit.h
  ${LIBRARY_DIRECTORY}/atltheme.h
  ${LIBRARY_DIRECTORY}/atluser.h
  ${LIBRARY_DIRECTORY}/atlwince.h
  ${LIBRARY_DIRECTORY}/atlwinx.h
  )

add_custom_target(wtl-src SOURCES ${LIBRARY_SOURCES})
install(FILES ${LIBRARY_SOURCES} DESTINATION ${INSTALL_DIRECTORY})

# Interface library for usage requirements
add_library(WTL INTERFACE)
target_include_directories(WTL INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/${LIBRARY_DIRECTORY}>
  $<INSTALL_INTERFACE:${INSTALL_DIRECTORY}>)
install(TARGETS WTL EXPORT WTLConfig)

set(CMAKE_SKIP_INSTALL_ALL_DEPENDENCY ON)

if(BUILD_SAMPLES)
  add_subdirectory(Samples)
endif()
