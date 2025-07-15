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
set(AES_PUBLIC_HEADERS aes.h aes.hpp)
set_target_properties(${PROJECT_NAME} 
	PROPERTIES 
	  PUBLIC_HEADER "${AES_PUBLIC_HEADERS}")
target_include_directories(${PROJECT_NAME}
    INTERFACE
        ${CMAKE_CURRENT_LIST_DIR}
)
install(TARGETS ${PROJECT_NAME}
	CONFIGURATIONS Release
	LIBRARY
	  DESTINATION lib
	PUBLIC_HEADER
	  DESTINATION include)

