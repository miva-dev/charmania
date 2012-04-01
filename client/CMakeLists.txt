find_package(Qt4 REQUIRED)

file(
    GLOB_RECURSE
    source_files
    src/*.cpp
	src/*.h
)

file(
    GLOB_RECURSE
    common_files
    "${CHARMANIA_SOURCE_DIR}/common/src/*.cpp"
)

file(
    GLOB
    qobject_files
    src/graphic/*.h
)

qt_wrap_cpp(
    client
    source_files
    ${qobject_files}
)

include_directories(
    "${CHARMANIA_SOURCE_DIR}/common/src"
    src
)

include(
    ${QT_USE_FILE}
)

add_definitions(
    ${QT_DEFINITIONS}
)

add_executable(
    client
    ${source_files}
    ${common_files}
)

target_link_libraries(
    client
    ${QT_LIBRARIES}
)
