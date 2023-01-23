#target.symbol DataFormatsGeometryVector
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsGeometryVector SHARED 
  src/TrackingJacobians.cc
  src/print.cc
)

set_target_properties(DataFormatsGeometryVector PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsGeometryVector)

install( TARGETS DataFormatsGeometryVector DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsGeometryVector PUBLIC
ROOT::Core
DataFormatsMath
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)

cms_rootdict(DataFormatsGeometryVector src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsGeometryVector)
