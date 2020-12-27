CMAKE_MINIMUM_REQUIRED (VERSION 3.9)

set(THIS_PROJECT_NAME imgui)

project(${THIS_PROJECT_NAME})

message(STATUS "THIS_PROJECT_NAME:        ${THIS_PROJECT_NAME}")

set(root ${CMAKE_CURRENT_SOURCE_DIR})
set(HEADERS imgui.h
            imconfig.h
            imgui_internal.h
            backends/imgui_impl_metal.h
            backends/imgui_impl_osx.h)
set(STB_HEADERS imstb_rectpack.h
                imstb_textedit.h
                imstb_truetype.h)
set(SOURCE imgui.cpp
           imgui_demo.cpp
           imgui_draw.cpp
           imgui_tables.cpp
           imgui_widgets.cpp
           backends/imgui_impl_metal.mm
           backends/imgui_impl_osx.mm)

add_library(${THIS_PROJECT_NAME} ${STB_HEADERS}
                                 ${HEADERS}
                                 ${SOURCE})
                                 
target_include_directories(${THIS_PROJECT_NAME} PUBLIC ${root})

target_link_libraries(${THIS_PROJECT_NAME} "-framework Metal -framework AppKit")

source_group( "Source Files" FILES ${SOURCE} )
source_group( "Header Files" FILES ${HEADERS})
source_group( "STB Headers"  FILES ${STB_HEADERS})
