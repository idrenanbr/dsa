# Aula 15

# 🎯 Objetivos
- Modelar um Livro como struct (id, título, autor, ano, status).
- Implementar uma lista duplamente encadeada para armazenar livros.
- Criar operações: inserir, listar, buscar, remover, emprestar/devolver.
- Exercitar ponteiros, alocação dinâmica e modularização básica.

# 🧱 Modelo de dados

typedef struct {
    int  id;
    char titulo[64];
    char autor[64];
    int  ano;
    int  emprestado; // 0 = disponível, 1 = emprestado
} Livro;

typedef struct No {
    Livro       dado;
    struct No  *ant;
    struct No  *prox;
} No;

typedef struct {
    No *ini;  // cabeça
    No *fim;  // cauda
    int tam;
} Lista;
