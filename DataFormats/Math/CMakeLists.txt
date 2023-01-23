#target.symbol DataFormatsMath
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsMath SHARED 
  src/ExtVec.cc
  src/FastMath.cc
  src/SSEVec.cc
  src/libminifloat.cc
)

set_target_properties(DataFormatsMath PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsMath)

install( TARGETS DataFormatsMath DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_include_directories(DataFormatsMath PUBLIC ${EIGEN_INCLUDE_DIR}/eigen3)
target_link_libraries(DataFormatsMath PUBLIC
ROOT::Core
DataFormatsCommon
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)

cms_rootdict(DataFormatsMath src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsMath)
