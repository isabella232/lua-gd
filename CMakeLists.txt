# Copyright (C) 2007-2011 LuaDist.
# Submitted by David Manura, Peter Kapec
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

PROJECT(lua-gd C)
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
INCLUDE(dist.cmake)

# Find GD
FIND_PACKAGE(GD REQUIRED)

# GD features
FOREACH(GD_FEATURE ${GD_FEATURES})
	ADD_DEFINITIONS(-D${GD_FEATURE})
ENDFOREACH()

# Build
ADD_LUA_MODULE(gd luagd.c)
TARGET_LINK_LIBRARIES(gd ${GD_LIBRARY})

# Install all files and documentation
INSTALL (TARGETS gd DESTINATION ${INSTALL_CMOD})
INSTALL (FILES README COPYING DESTINATION ${INSTALL_DATA})
INSTALL (DIRECTORY demos/ DESTINATION ${INSTALL_EXAMPLE})
INSTALL (DIRECTORY doc/ DESTINATION ${INSTALL_DOC})

