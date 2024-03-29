############################################################################
# CMakeLists.txt
# Copyright (C) 2018-2023  Belledonne Communications, Grenoble France
#
############################################################################
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.
#
############################################################################

if(NOT CPACK_PACKAGE_NAME)
	string(TOLOWER "${PROJECT_NAME}" LOWERCASE_PROJECT_NAME)
	set(CPACK_PACKAGE_NAME "${LOWERCASE_PROJECT_NAME}")
ENDIF()

set(CPACK_PACKAGE_VERSION_MAJOR ${PROJECT_VERSION_MAJOR})
set(CPACK_PACKAGE_VERSION_MINOR ${PROJECT_VERSION_MINOR})
set(CPACK_PACKAGE_VERSION_PATCH ${PROJECT_VERSION_PATCH})

set(CPACK_PACKAGE_FILE_NAME ${CPACK_PACKAGE_NAME}-${PROJECT_VERSION})

set(CPACK_SOURCE_GENERATOR "TGZ")
set(CPACK_SOURCE_IGNORE_FILES
	"${CMAKE_BINARY_DIR}"
	"^${PROJECT_SOURCE_DIR}/.git*"
)

message("-- Package file name is ${CPACK_PACKAGE_FILE_NAME}")

set(CPACK_SOURCE_PACKAGE_FILE_NAME ${CPACK_PACKAGE_FILE_NAME})

if(UNIX AND NOT APPLE AND NOT ANDROID)
	configure_file("rpm/bcmatroska2.spec.cmake" "${PROJECT_SOURCE_DIR}/bcmatroska2.spec" @ONLY)
endif()

include(CPack)
