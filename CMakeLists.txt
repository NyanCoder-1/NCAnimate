# Copyright (C) 2023 Victor Nikolaev
#
# This file is part of NCAnimate.
#
# NCAnimate is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# NCAnimate is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with NCAnimate. If not, see <https://www.gnu.org/licenses/>.

cmake_minimum_required(VERSION 3.5)
project(ncanimate)

#specify c++ standard
if (ENABLE_CXX_20)
    set(CMAKE_CXX_STANDARD 20)
endif()

set(SOURCE_FILES
    src/main.cpp
)

# Find GTK
find_package(PkgConfig REQUIRED)
pkg_check_modules(GTK REQUIRED gtk4)

# Add executable
add_executable(ncanimate ${SOURCE_FILES})

# Add GTK include directories
target_include_directories(ncanimate PRIVATE ${GTK_INCLUDE_DIRS})

# Link against GTK
target_link_libraries(ncanimate PRIVATE ${GTK_LIBRARIES})
