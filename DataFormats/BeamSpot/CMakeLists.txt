#target.symbol DataFormatsBeamSpot
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsBeamSpot SHARED 
  src/BeamSpot.cc
)

set_target_properties(DataFormatsBeamSpot PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsBeamSpot)

install( TARGETS DataFormatsBeamSpot DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsBeamSpot PUBLIC
ROOT::Core
CLHEP::CLHEP
DataFormatsCLHEP
DataFormatsCommon
DataFormatsMath
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Smatrix
ROOT::Thread
ROOT::Tree
)

cms_rootdict(DataFormatsBeamSpot src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsBeamSpot)
