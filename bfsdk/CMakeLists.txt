#
# Bareflank Hypervisor
# Copyright (C) 2019 Assured Information Security, Inc.
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA

cmake_minimum_required(VERSION 3.13)
project(bfsdk CXX ASM)

set(INTEL_X64 $<STREQUAL:${CMAKE_HOST_SYSTEM_PROCESSOR},x86_64>)

add_library(bfsdk
    $<${INTEL_X64}:src/arch/x64/threadcontext.S>
)

# -----------------------------------------------------------------------------
# installs
# -----------------------------------------------------------------------------

install(FILES include/bfehframelist.h DESTINATION include/bfsdk)
install(FILES include/bfexec.h DESTINATION include/bfsdk)
install(FILES include/bfstart.h DESTINATION include/bfsdk)
install(FILES include/bfsyscall.h DESTINATION include/bfsdk)
install(FILES include/bfthreadcontext.h DESTINATION include/bfsdk)
install(FILES include/bftypes.h DESTINATION include/bfsdk)
install(FILES include/bfweak.h DESTINATION include/bfsdk)

install(TARGETS bfsdk DESTINATION lib)
