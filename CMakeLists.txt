cmake_minimum_required(VERSION 3.12)

project(tiny-aes C)

add_library(${PROJECT_NAME} "")
target_sources(${PROJECT_NAME}
    PRIVATE
        ${CMAKE_CURRENT_LIST_DIR}/aes.c
    INTERFACE
        ${CMAKE_CURRENT_LIST_DIR}/aes.h
        ${CMAKE_CURRENT_LIST_DIR}/aes.hpp
)
install(TARGETS ${PROJECT_NAME}
	CONFIGURATIONS Release
	RUNTIME
	  DESTINATION Release/lib)
install(TARGETS ${PROJECT_NAME}
	CONFIGURATIONS Debug
	RUNTIME
	  DESTINATION Debug/lib)


target_include_directories(${PROJECT_NAME}
    INTERFACE
        ${CMAKE_CURRENT_LIST_DIR}
)
