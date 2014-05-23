
# Sample superquadric VTK
add_executable (sample_superquadric_vtk MACOSX_BUNDLE main_sample_superquadric_vtk.cpp)
target_link_libraries (sample_superquadric_vtk ${PCL_LIBRARIES})
set_target_properties( sample_superquadric_vtk PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin
  ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin )

# Sample superquadric
add_executable (sample_superquadric main_sample_superquadric.cpp)
target_link_libraries (sample_superquadric ${libs_to_link})
set_target_properties( sample_superquadric PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin
  ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin )


# Fit superquadric to samples
add_executable (fit_superquadric_to_samples MACOSX_BUNDLE main_fit_superquadric_to_samples.cpp)
target_link_libraries (fit_superquadric_to_samples ${PCL_LIBRARIES} superquadrics_framework)
set_target_properties( fit_superquadric_to_samples PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin
  ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin )


# Split and merge superquadric
add_executable (split_and_merge MACOSX_BUNDLE main_split_and_merge.cpp)
target_link_libraries (split_and_merge ${libs_to_link})
set_target_properties( split_and_merge PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin
  ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin )


# Fit superquadric with CERES
add_executable (fit_superquadric_ceres main_fit_superquadric_ceres.cpp)
target_link_libraries (fit_superquadric_ceres ${libs_to_link})
set_target_properties( fit_superquadric_ceres PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin
  ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin )


# Table top segmentation
add_executable (tabletop_segmentation MACOSX_BUNDLE main_tabletop_segmentation.cpp)
target_link_libraries (tabletop_segmentation ${libs_to_link})
set_target_properties( tabletop_segmentation PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin
  ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin )


# Segmentation with n pointclouds?
add_executable (segmentation_n_fitting_pipeline MACOSX_BUNDLE main_segmentation_n_fitting_pipeline.cpp)
target_link_libraries (segmentation_n_fitting_pipeline ${libs_to_link})
set_target_properties( segmentation_n_fitting_pipeline PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin
  ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin )


# Segmentation with n detection
add_executable (segmentation_n_detection MACOSX_BUNDLE main_segmentation_n_detection.cpp)
target_link_libraries (segmentation_n_detection ${libs_to_link})
set_target_properties( segmentation_n_detection PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin
  ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin )




