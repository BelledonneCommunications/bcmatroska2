############################################################################
# CMakeLists.txt
# Copyright (C) 2016  Belledonne Communications, Grenoble France
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

add_library(bcmatroska2-ebml-objects OBJECT
	ebmlmain.c
	ebmlelement.c
	ebmlmaster.c
	ebmlbinary.c
	ebmlstring.c
	ebmlnumber.c
	ebmlcrc.c
	ebmldate.c
	ebmlvoid.c
)
set_target_properties(bcmatroska2-ebml-objects PROPERTIES POSITION_INDEPENDENT_CODE TRUE)

install(DIRECTORY ebml
	DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
)
