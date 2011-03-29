# Copyright (C) 2011 LuaDist.
# Created by David Manura
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

project ( lcurses C )
cmake_minimum_required ( VERSION 2.6 )
include ( dist.cmake )

find_package ( Curses REQUIRED )
include_directories ( ${CURSES_INCLUDE_DIR} )
if ( CURSES_HAVE_NCURSES_H )
  set (HAVE_NCURSES_H true )
endif ()
configure_file ( config.h.cmake config.h )
include_directories ( ${CMAKE_CURRENT_BINARY_DIR} )

install_lua_module ( curses lcurses.c )
target_link_libraries ( curses ${CURSES_LIBRARIES} )
install_data ( AUTHORS COPYING NEWS README )
#install_test ( test.lua ) # missing tests
#add_lua_test ( test.lua )
