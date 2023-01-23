#target.symbol DataFormatsCTPPSReco
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsCTPPSReco SHARED 
  src/CTPPSDiamondLocalTrack.cc
  src/CTPPSPixelLocalTrack.cc
  src/CTPPSTimingLocalTrack.cc
  src/TotemRPLocalTrack.cc
  src/TotemRPUVPattern.cc
)

set_target_properties(DataFormatsCTPPSReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsCTPPSReco)

install( TARGETS DataFormatsCTPPSReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsCTPPSReco PUBLIC
ROOT::Core
DataFormatsCTPPSDigi
DataFormatsCommon
DataFormatsGeometrySurface
DataFormatsMath
ROOT::Core
ROOT::GenVector
ROOT::Hist
ROOT::MathCore
ROOT::MathMore
ROOT::Matrix
ROOT::Net
ROOT::Physics
ROOT::RIO
ROOT::Smatrix
ROOT::Thread
ROOT::Tree
)

cms_rootdict(DataFormatsCTPPSReco src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsCTPPSReco)
