project(ExampleDoc)

cmake_minimum_required(VERSION 2.6)

# first we can indicate the documentation build as an option
# and set it to ON by default
option(BUILD_DOC "Build documentation" ON)

# check if Doxygen is installed
find_package(Doxygen
             REQUIRED dot)
if (DOXYGEN_FOUND)
    # set input and output files
    set(DOXYGEN_INPUT ${CMAKE_CURRENT_SOURCE_DIR}/docs)
    set(DOXYGEN_OUTPUT_DIR ${CMAKE_CURRENT_SOURCE_DIR}/Doc)
    message("Doxygen Output ${DOXYGEN_OUTPUT_DIR}")

    # create the output directory where the documentation will live
    file(MAKE_DIRECTORY ${DOXYGEN_OUTPUT_DIR})
    # request to configure the file
    configure_file(${CMAKE_CURRENT_SOURCE_DIR}/Doxyfile.in ${CMAKE_CURRENT_BINARY_DIR}/Doxyfile @ONLY)

    # note the option ALL which allows to build the docs together 
    # with the application
    add_custom_target(Doc
        COMMAND ${CMAKE_COMMAND} -E make_directory ${DOXYGEN_OUTPUT_DIR}
        COMMAND ${DOXYGEN_EXECUTABLE} ${CMAKE_CURRENT_BINARY_DIR}/Doxyfile
        WORKING_DIRECTORY ${DOXYGEN_OUTPUT_DIR}
        )
else (DOXYGEN_FOUND)
  message("Doxygen need to be installed to generate the doxygen documentation")
endif (DOXYGEN_FOUND)