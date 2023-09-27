cmake_minimum_required(VERSION 3.10)

# set the project name and version
project(comp VERSION 1.0)

file(GLOB comp_SRC CONFIGURE_DEPENDS ".h" "*.cpp")
add_executable(comp ${comp_SRC})



target_include_directories(comp PUBLIC
"${PROJECT_BINARY_DIR}"
)

#specify the C++ standard
target_compile_features(comp PRIVATE cxx_std_20)





 set(CMAKE_CXX_STANDARD 20)
# set(CMAKE_CXX_STANDARD_REQUIRED True)


#packages

find_package(Threads REQUIRED)
   find_package(HDF5 REQUIRED)
   include_directories( ${HDF5_INCLUDE_DIRS})
   target_link_libraries (comp ${HDF5_LIBRARIES} Threads::Threads)

   find_package(h5cpp REQUIRED PATHS "/home/cll/src/hdf5/h5cpp/build/install/")
   include_directories( "/home/cll/src/hdf5/h5cpp/build/install/include/" )

   find_package(fmt REQUIRED PATHS "/lib/cmake/fmt/")
   include_directories( "/usr/local/include/fmt/")



#    target_link_libraries (comp hdf5)
#    target_link_libraries (comp h5cpp)

   
