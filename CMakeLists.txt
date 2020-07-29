cmake_minimum_required(VERSION 3.13)

project(sdptransform VERSION 1.2.5)

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

add_library(${PROJECT_NAME} STATIC ${SOURCE_FILES} ${HEADER_FILES})

target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)
target_compile_features(${PROJECT_NAME} PUBLIC cxx_std_17)
target_link_libraries(sdptransform PUBLIC nlohmann_json::nlohmann_json)
install(TARGETS sdptransform DESTINATION lib)
install(FILES ${HEADER_FILES} DESTINATION include/sdptransform)
