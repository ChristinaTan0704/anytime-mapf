project(balance)
list(APPEND CMAKE_PREFIX_PATH "../json")
cmake_minimum_required (VERSION 3.16)
set (CMAKE_CXX_STANDARD 14)

IF(NOT CMAKE_BUILD_TYPE)
    SET(CMAKE_BUILD_TYPE "RELEASE")
ENDIF()

include_directories("inc" "inc/CBS" "inc/PIBT")
file(GLOB SOURCES "src/*.cpp" "src/CBS/*.cpp" "src/PIBT/*.cpp")
add_executable(balance ${SOURCES})
set(Boost_USE_MULTITHREADED False)
# Find Boost
find_package(Boost REQUIRED COMPONENTS program_options system filesystem)

# Find Eigen3 for PIBT
find_package (Eigen3 3.3 REQUIRED NO_MODULE)
find_package(nlohmann_json REQUIRED)
include_directories( ${Boost_INCLUDE_DIRS} )
target_link_libraries(balance ${Boost_LIBRARIES} Eigen3::Eigen nlohmann_json::nlohmann_json)
