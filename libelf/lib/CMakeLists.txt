
project(libelf C)

if(NOT TARGET libelf)
	
	file(GLOB_RECURSE SOURCES "${PROJECT_SOURCE_DIR}/*.c")
	add_library(libelf SHARED ${SOURCES})
	set_target_properties(libelf PROPERTIES OUTPUT_NAME "retdec-libelf")
	target_include_directories(libelf SYSTEM PUBLIC ${PROJECT_SOURCE_DIR})
	if(MSVC)
		set_target_properties(libelf PROPERTIES WINDOWS_EXPORT_ALL_SYMBOLS TRUE)
	endif()
	install(TARGETS libelf 
		LIBRARY DESTINATION lib
		RUNTIME DESTINATION bin
	)
	# On Windows, DLLs need to be in unit-tests directory as well.
	if(MSVC)
		install(TARGETS libelf
			RUNTIME DESTINATION bin/unit-tests
		)
	endif()

endif()