#target.symbol SimDataFormatsGeneratorProducts
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${FMT_INCLUDE_DIR}
${HEPMC_INCLUDE_DIR}
${CMSMD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
${XZ_INCLUDE_DIR}
/usr/include
)



add_library(SimDataFormatsGeneratorProducts SHARED 
  src/GenEventInfoProduct.cc
  src/GenFilterInfo.cc
  src/GenLumiInfoHeader.cc
  src/GenLumiInfoProduct.cc
  src/GenRunInfoProduct.cc
  src/HepMCProduct.cc
  src/LHEEventProduct.cc
  src/LHERunInfoProduct.cc
  src/LHEXMLStringProduct.cc
  src/hepmc_rootio.cc
)

set_target_properties(SimDataFormatsGeneratorProducts PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsGeneratorProducts)

install( TARGETS SimDataFormatsGeneratorProducts DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_include_directories(SimDataFormatsGeneratorProducts PUBLIC ${HEPMC_INCLUDE_DIR})
target_link_libraries(SimDataFormatsGeneratorProducts PUBLIC
ROOT::Core
${HEPMC_HepMC_LIBRARY}
DataFormatsCommon
FWCoreMessageLogger
FWCoreUtilities
ROOT::Core
ROOT::Hist
ROOT::MathCore
ROOT::Matrix
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
lzma
)

#the build rule deals with auto_ptr which is deprecated
target_compile_options(SimDataFormatsGeneratorProducts PRIVATE "-Wno-deprecated-declarations")
cms_rootdict(SimDataFormatsGeneratorProducts src/classes.h src/classes_def.xml)
add_rootdict_rules(SimDataFormatsGeneratorProducts)
