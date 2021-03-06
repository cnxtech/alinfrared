##
## Copyright (C) 2012 Aldebaran Robotics
##
## This program is free software; you can redistribute it and/or
## modify it under the terms of the GNU General Public License
## as published by the Free Software Foundation; either version 2
## of the License, or (at your option) any later version.
##
## This program is distributed in the hope that it will be useful,
## but WITHOUT ANY WARRANTY; without even the implied warranty of
## MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
## GNU General Public License for more details.
##
## You should have received a copy of the GNU General Public License
## along with this program; if not, write to the Free Software
## Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

cmake_minimum_required(VERSION 2.6.4 FATAL_ERROR)
project(ALInfrared)
find_package(qibuild)

option(WITH_LIRC "enable lirc support" ON)

if(NOT I_AM_A_ROBOT OR NOT WITH_LIRC)
    return()
endif()


set(INFRARED_SRCS
  src/alinfrared.h
  src/alinfrared.cpp
  src/infraredmain.cpp
)

qi_create_lib(infrared SHARED SUBFOLDER naoqi ${INFRARED_SRCS})
qi_use_lib(infrared ALCOMMON ALMATH LIRCCLIENT ALPROXIES)
