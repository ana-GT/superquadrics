##########################
# CMake file
##########################
cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

project(superquadrics_visualize)


# Required:
# PCL > 1.7 
# Eigen ( works with 3.2 )
# Boost (works with 1.48 - NO 1.46 )
find_package(PCL 1.7 REQUIRED io common segmentation sample_consensus surface visualization)
include_directories(${PCL_INCLUDE_DIRS} include/)
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})

# External library CERES
find_package (Ceres REQUIRED)
include_directories (${CERES_INCLUDES})


find_package(OpenMP)
if (OPENMP_FOUND)
    set (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
endif()

# Include files for framework_incs
set (framework_incs include/fit_superquadric_lm.h 
  include/fit_superquadric_ceres.h
  include/superquadric_formulas.h
  include/sample_superquadric.h
  include/sample_superquadric_uniform.h
  include/segmentation_utils.h
  include/tabletop_segmentation.h
  include/superquadric_detection.h
  include/superquadric_rigid_registration.h)
# Include file for framework_impls
set (framework_impls include/impl/fit_superquadric_lm.hpp
  include/impl/fit_superquadric_ceres.hpp
  include/impl/superquadric_formulas.hpp
  include/impl/sample_superquadric.hpp
  include/impl/sample_superquadric_uniform.hpp
  include/impl/segmentation_utils.hpp
  include/impl/tabletop_segmentation.hpp
  include/impl/superquadric_detection.hpp
  include/impl/superquadric_rigid_registration.hpp)
# Include file for framework_srcs
set (framework_srcs src/fit_superquadric_lm.cpp
  src/fit_superquadric_ceres.cpp
  src/sample_superquadric.cpp
  src/sample_superquadric_uniform.cpp
  src/segmentation_utils.cpp
  src/tabletop_segmentation.cpp
  src/superquadric_detection.cpp
  src/superquadric_rigid_registration.cpp)


# Superquadrics Framework
ADD_LIBRARY (superquadrics_framework ${framework_incs} ${framework_impls} ${framework_srcs})
TARGET_LINK_LIBRARIES (superquadrics_framework)
SET_TARGET_PROPERTIES( superquadrics_framework PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib
  ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib )
# Set libraries on which the rest of executables will depend
set (libs_to_link ${PCL_LIBRARIES} ${CERES_LIBRARIES} superquadrics_framework )


####################
# EXECUTABLES
####################
add_subdirectory( executables )
add_subdirectory( tests )
