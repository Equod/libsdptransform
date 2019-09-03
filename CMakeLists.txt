cmake_minimum_required(VERSION 3.0)

project(sdptransform VERSION 1.2.5)

add_subdirectory(test)
add_subdirectory(readme-helper)
add_subdirectory(third_party)

option(SDPTRANSFORM_USE_EXTERNAL_JSON "Use an external JSON library" OFF)

set(
	SOURCE_FILES
	src/grammar.cpp
	src/parser.cpp
	src/writer.cpp
)

set(
	HEADER_FILES
	include/sdptransform.hpp
)

add_library(sdptransform STATIC ${SOURCE_FILES} ${HEADER_FILES})
target_compile_features(sdptransform PUBLIC cxx_std_11)
target_include_directories(sdptransform PRIVATE include)

target_link_libraries(sdptransform PUBLIC nlohmann_json::nlohmann_json)

install(TARGETS sdptransform DESTINATION lib)
install(FILES ${HEADER_FILES} DESTINATION include/sdptransform)
