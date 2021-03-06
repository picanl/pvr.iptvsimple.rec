project(pvr.iptvsimple.rec)

cmake_minimum_required(VERSION 2.6)

enable_language(CXX)

find_package(Kodi REQUIRED)
find_package(kodiplatform REQUIRED)
find_package(p8-platform REQUIRED)
find_package(ZLIB REQUIRED)

include_directories(${kodiplatform_INCLUDE_DIRS}
                    ${p8-platform_INCLUDE_DIRS}
                    ${KODI_INCLUDE_DIR}
                    ${ZLIB_INCLUDE_DIRS}
                    ${PROJECT_SOURCE_DIR}/lib)

set(DEPLIBS ${p8-platform_LIBRARIES}
            ${ZLIB_LIBRARIES})

message(STATUS "ZLIB_LIBRARIES: ${ZLIB_LIBRARIES}")

set(IPTV_SOURCES src/client.cpp
                 src/PVRIptvData.cpp
                 src/PVRRecorder.cpp
                 src/PVRUtils.cpp
                 src/PVRRecJob.cpp
                 src/PVRSchedulerThread.cpp
                 src/PVRRecorderThread.cpp
                 src/PVRPlayList.cpp)

build_addon(pvr.iptvsimple.rec IPTV DEPLIBS)

include(CPack)
