cmake_minimum_required(VERSION 3.6)
project(TgBotTest)

set(CMAKE_CXX_STANDARD 11)

set(SOURCE_FILES main.cpp)

add_executable(TgBotTest ${SOURCE_FILES})

find_package(Threads REQUIRED)
find_package(OpenSSL REQUIRED)
find_package(Boost COMPONENTS system iostreams REQUIRED)
include_directories(tgbot-cpp/include ${OPENSSL_INCLUDE_DIR} ${Boost_INCLUDE_DIR})

find_library(TGBOTCPP TgBot tgbot-cpp/lib)
target_link_libraries(${PROJECT_NAME} ${TGBOTCPP} ${CMAKE_THREAD_LIBS_INIT} ${OPENSSL_LIBRARIES} ${Boost_LIBRARIES} ws2_32)

