cmake_minimum_required(VERSION 3.10)
project(cg_projeto0 VERSION 1.0)

# Define o padrão C++ e exige a versão escolhida
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Diretório de includes do projeto (local onde estão os headers, como glad.h)
include_directories(${CMAKE_SOURCE_DIR}/include)

# Encontra as dependências instaladas via package manager
find_package(glfw3 3.3 REQUIRED)
set(OpenGL_GL_PREFERENCE GLVND)
find_package(OpenGL REQUIRED)
# O GLM é uma biblioteca header-only; se estiver instalada no sistema, você pode
# incluir o diretório de includes ou adicioná-la manualmente se preferir.

# Lista de arquivos fonte do projeto (incluindo o glad.c, que é necessário para
# o GLAD funcionar)
set(SOURCES src/main.cpp src/glad.c)

# Cria o executável a partir dos arquivos fonte
add_executable(${PROJECT_NAME} ${SOURCES})

# Linka as bibliotecas necessárias (GLFW e OpenGL)
target_link_libraries(${PROJECT_NAME} glfw OpenGL::GL)
