# Copyright (C) 2013 LuaDist.
# Created by Peter Kapec
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

project( libnoise CXX )
cmake_minimum_required ( VERSION 2.8 )
include( cmake/dist.cmake )

# Determine install host
if ( WIN32 AND NOT CYGWIN )
	if( MSVC )
		add_definitions( -D_CRT_SECURE_NO_DEPRECATE )
		set( DEF_FILE src/win32/libnoise.def )
		set( DLL_RC_FILE src/noise.rc )
	endif()
endif()

# Build Libraries
include_directories( src src/model src/module )
file( GLOB_RECURSE SRC "src/model/*.cpp" )
file( GLOB_RECURSE SRC2 "src/module/*.cpp" )

file( GLOB HEADERS "src/*.h" )
set( HEADERS_MODEL "src/model" )
set( HEADERS_MODULE "src/module" )

add_library( noise  src/latlon.cpp src/noisegen.cpp ${SRC} ${SRC2})

# Install
install_library( noise )
install_header( ${HEADERS} ${HEADERS_MODEL} ${HEADERS_MODULE} )
install_doc( COPYING.txt doc/readme.txt doc/html doc/htmldata doc/img )