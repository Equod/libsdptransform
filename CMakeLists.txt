cmake_minimum_required(VERSION 3.13)

project(sdptransform VERSION 1.2.7)

add_subdirectory(test)
add_subdirectory(readme-helper)

add_library(${PROJECT_NAME}
        src/grammar.cpp
        src/parser.cpp
        src/writer.cpp
        include/sdptransform/sdptransform.hpp)

set_target_properties(${PROJECT_NAME}
        PROPERTIES CXX_STANDARD 17
        )

target_include_directories(${PROJECT_NAME}
        PUBLIC
            include
        PRIVATE
            include/sdptransform)

target_link_libraries(${PROJECT_NAME}
        PUBLIC
            nlohmann_json::nlohmann_json
)

#install(TARGETS sdptransform DESTINATION lib)
#install(FILES include/sdptransform/sdptransform.hpp DESTINATION include/sdptransform)
