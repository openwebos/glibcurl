# @@@LICENSE
#
#      Copyright (c) 2010-2012 Hewlett-Packard Development Company, L.P.
#
# Permission to use, copy, modify, and distribute this software for any
# purpose with or without fee is hereby granted, provided that the above
# copyright notice and this permission notice appear in all copies.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT OF THIRD PARTY RIGHTS.
# IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM,
# DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR
# OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE
# USE OR OTHER DEALINGS IN THE SOFTWARE.
#
# Except as contained in this notice, the name of a copyright holder shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization of the
# copyright holder.
#
# LICENSE@@@

#
# glibcurl/CMakeLists.txt
#

cmake_minimum_required(VERSION 2.8.7)

project (glibcurl CXX)

include(webOS/webOS)
webos_modules_init(1 0 0 QUALIFIER RC2)
webos_upstream_from_repo(0.7.3 0)

include(FindPkgConfig)

pkg_check_modules(GLIB2 REQUIRED glib-2.0)
include_directories(${GLIB2_INCLUDE_DIRS})
webos_add_compiler_flags(ALL ${GLIB2_CFLAGS_OTHER})

pkg_check_modules(LIBCURL REQUIRED libcurl)
include_directories(${LIBCURL_INCLUDE_DIRS})
webos_add_compiler_flags(ALL ${LIBCURL_CFLAGS_OTHER})

webos_build_pkgconfig()

include_directories(include/public)
webos_add_compiler_flags(ALL -Wall)
webos_add_linker_options(ALL --version-script=${CMAKE_SOURCE_DIR}/src/glibcurlExports.map)
webos_add_linker_options(ALL --no-undefined)

add_library(glibcurl SHARED src/glibcurl.cpp)
target_link_libraries(glibcurl ${GLIB2_LDFLAGS} ${LIBCURL_LDFLAGS} rt)

webos_build_library()
