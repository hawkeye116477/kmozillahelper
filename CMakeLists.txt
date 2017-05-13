cmake_minimum_required(VERSION 2.8.12)

project( kwaterfoxhelper )

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

find_package(ECM 1.0.0 REQUIRED NO_MODULE)

set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${ECM_KDE_MODULE_DIR})

include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDECompilerSettings)
include(FeatureSummary)

find_package(KF5 REQUIRED COMPONENTS Notifications KIO WindowSystem I18n)

add_executable(kwaterfoxhelper main.cpp)

target_link_libraries(kwaterfoxhelper KF5::I18n KF5::KIOWidgets KF5::Notifications KF5::WindowSystem)

install(TARGETS kwaterfoxhelper DESTINATION /opt/waterfox/)
install(FILES kwaterfoxhelper.notifyrc DESTINATION ${KNOTIFYRC_INSTALL_DIR})
