# Copyright (c) 2024 LuckkMaker
# All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

add_library(omni-cherryusb INTERFACE)

include(cherryusb.cmake)

#message(STATUS "cherryusb_incs: ${cherryusb_incs}")
#message(STATUS "cherryusb_srcs: ${cherryusb_srcs}")

set(CHERRYUSB_CFG_SOURCE_FILE ${CMAKE_CURRENT_LIST_DIR}/usb_config.in)
set(CHERRYUSB_CFG_TARGET_FILE ${OMNI_USB_CFG_DIR}/usb_config.h)
omni_add_configure_file(${CHERRYUSB_CFG_SOURCE_FILE} ${CHERRYUSB_CFG_TARGET_FILE})

target_include_directories(omni-cherryusb INTERFACE
    ${cherryusb_incs}
)

target_sources(omni-cherryusb INTERFACE
    ${cherryusb_srcs}
)
