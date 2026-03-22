cmake_minimum_required(VERSION 3.10)
project(bgdl_plugin C CXX)

# Carrega o dicionário de comandos do PS Vita (aqui mora o vita_create_suprx)
include("$ENV{VITASDK}/share/vita.cmake")

# Define que queremos compilar uma biblioteca dinâmica
add_library(bgdl_plugin SHARED bgdl_plugin.cpp)

# Conecta as bibliotecas do sistema do Vita
target_link_libraries(bgdl_plugin 
    SceKernel_stub 
    taihen_stub
)

# Converte o arquivo compilado no formato final de plugin do Vita
vita_create_suprx(bgdl_plugin.suprx bgdl_plugin)
