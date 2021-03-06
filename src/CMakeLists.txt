#   Copyright 2016 Comcast Cable Communications Management, LLC
#
#   Licensed under the Apache License, Version 2.0 (the "License");
#   you may not use this file except in compliance with the License.
#   You may obtain a copy of the License at
#
#       http://www.apache.org/licenses/LICENSE-2.0
#
#   Unless required by applicable law or agreed to in writing, software
#   distributed under the License is distributed on an "AS IS" BASIS,
#   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#   See the License for the specific language governing permissions and
#   limitations under the License.
set(PROJ_RESOLV_LIB ucresolv)

file(GLOB HEADERS ucresolv.h)
set(SOURCES res_query.c res_mkquery.c res_send.c)

add_library(${PROJ_RESOLV_LIB} STATIC ${HEADERS} ${SOURCES})
add_library(${PROJ_RESOLV_LIB}.shared SHARED ${HEADERS} ${SOURCES})
target_link_libraries(${PROJ_RESOLV_LIB} pthread)
set_target_properties(${PROJ_RESOLV_LIB}.shared PROPERTIES OUTPUT_NAME ${PROJ_RESOLV_LIB})

install (TARGETS ${PROJ_RESOLV_LIB} DESTINATION lib${LIB_SUFFIX})
install (TARGETS ${PROJ_RESOLV_LIB}.shared DESTINATION lib${LIB_SUFFIX})
install (FILES ucresolv.h DESTINATION include/${PROJ_RESOLV_LIB})
