add_library(imgui
	include/imconfig.h
	include/imgui.h
	include/imgui_freetype.h
	include/imgui_internal.h
	include/imgui_stdlib.h
	include/imstb_textedit.h
	src/imgui.cpp
	src/imgui_demo.cpp
	src/imgui_draw.cpp
	src/imgui_freetype.cpp
	src/imgui_tables.cpp
	src/imgui_widgets.cpp
	src/imstb_rectpack.h
	src/imstb_truetype.h
	src/imgui_stdlib.cpp
)

target_include_directories(imgui PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include")
target_include_directories(imgui PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}/src")
target_link_libraries(imgui PUBLIC plutosvg::plutosvg)

find_package(PkgConfig REQUIRED)
pkg_check_modules(FREETYPE REQUIRED IMPORTED_TARGET freetype2)

target_link_libraries(imgui PUBLIC PkgConfig::FREETYPE)
