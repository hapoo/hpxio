# Copyright (c) 2015 Alireza Kheirkhahan
# Copyright (c) 2014 Shuangyang Yang
#
# Distributed under the Boost Software License, Version 1.0. (See accompanying
# file LICENSE_1_0.txt or copy at http://www.boost.org/LICENSE_1_0.txt)

###############################################################################
# Local File System
###############################################################################
set(ROOT "${hpxio_SOURCE_DIR}/hpxio")

if(HPX_DEFAULT_BUILD_TARGETS)
  add_hpx_component(local_file
    FOLDER "Core/Components"
    HEADER_ROOT ${ROOT}
    SOURCES local_file.cpp
    ESSENTIAL)
else()
  add_hpx_component(local_file
    FOLDER "Core/Components"
    HEADER_ROOT ${ROOT}
    SOURCES local_file.cpp
    )
endif()


################################################################################
# OrangeFS
################################################################################
find_package(OrangeFS)

if(ORANGEFS_FOUND)
  # add OrangeFS header files directory
  include_directories(${ORANGEFS_INCLUDE_DIR})

  if(HPX_DEFAULT_BUILD_TARGETS)
    add_hpx_component(orangefs_file
      FOLDER "Core/Components"
      HEADER_ROOT ${ROOT}
      SOURCES orangefs_file.cpp
      DEPENDENCIES ${ORANGEFS_LIBRARY}
      ESSENTIAL)
  else()
    add_hpx_component(orangefs_file
      FOLDER "Core/Components"
      HEADER_ROOT ${ROOT}
      SOURCES orangefs_file.cpp
      DEPENDENCIES ${ORANGEFS_LIBRARY}
      )
  endif()

endif()

