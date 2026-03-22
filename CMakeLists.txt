cmake_minimum_required(VERSION 3.10)
project(bgdl_plugin C CXX)

# Define que queremos compilar uma biblioteca compartilhada (SHARED)
add_library(bgdl_plugin SHARED bgdl_plugin.cpp)

# Conecta as bibliotecas do sistema do Vita que o script do PKGj usa
target_link_libraries(bgdl_plugin 
    SceKernel_stub 
    taihen_stub
)

# A MÁGICA: Converte o output padrão em um arquivo .suprx do Vita!
vita_create_suprx(bgdl_plugin.suprx bgdl_plugin)
