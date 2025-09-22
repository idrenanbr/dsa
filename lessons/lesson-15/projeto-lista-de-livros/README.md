/******************************************************************************

Welcome to GDB Online.
  GDB online is an online compiler and debugger tool for C, C++, Python, PHP, Ruby, 
  C#, OCaml, VB, Perl, Swift, Prolog, Javascript, Pascal, COBOL, HTML, CSS, JS
  Code, Compile, Run and Debug online from anywhere in world.

*******************************************************************************/
#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    int valor;
    struct No *ant;   // ponteiro para anterior
    struct No *prox;  // ponteiro para próximo
} No;

void inserirInicio(No **head, int valor) {
    No *novo = malloc(sizeof(No));
    novo->valor = valor;
    novo->ant = NULL;
    novo->prox = *head;
    if (*head != NULL) (*head)->ant = novo;
    *head = novo;
}

void inserirFim(No **head, int valor) {
    No *novo = malloc(sizeof(No));
    novo->valor = valor;
    novo->prox = NULL;

    if (*head == NULL) {
        novo->ant = NULL;
        *head = novo;
        return;
    }
    No *tmp = *head;
    while (tmp->prox != NULL) tmp = tmp->prox;
    tmp->prox = novo;
    novo->ant = tmp;
}

void imprimir(No *head) {
    No *tmp = head;
    while (tmp != NULL) {
        printf("%d <-> ", tmp->valor);
        tmp = tmp->prox;
    }
    printf("NULL\n");
}

void imprimirReverso(No *head) {
    if (head == NULL) return;
    No *tmp = head;
    while (tmp->prox != NULL) tmp = tmp->prox; // vai até o último
    while (tmp != NULL) {
        printf("%d <-> ", tmp->valor);
        tmp = tmp->ant;
    }
    printf("NULL\n");
}

int main()
{
    No *lista = NULL;
    inserirFim(&lista, 70);
    inserirInicio(&lista, 10);
    imprimir(lista);

    return 0;
}
