#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Estrutura para armazenar informações do paciente
struct Paciente {
    char nome[100];
    int idade;
    char sexo[10];
    char historico_medico[500];
};

// Função para adicionar um novo paciente
void adicionarPaciente(struct Paciente pacientes[], int *totalPacientes) {
    struct Paciente novoPaciente;

    printf("Nome: ");
    scanf("%s", novoPaciente.nome);
    printf("Idade: ");
    scanf("%d", &novoPaciente.idade);
    printf("Sexo: ");
    scanf("%s", novoPaciente.sexo);
    printf("Histórico Médico: ");
    scanf("%s", novoPaciente.historico_medico);

    pacientes[*totalPacientes] = novoPaciente;
    (*totalPacientes)++;
}

// Função para listar todos os pacientes
void listarPacientes(struct Paciente pacientes[], int totalPacientes) {
    for (int i = 0; i < totalPacientes; i++) {
        printf("Paciente %d:\n", i + 1);
        printf("Nome: %s\n", pacientes[i].nome);
        printf("Idade: %d\n", pacientes[i].idade);
        printf("Sexo: %s\n", pacientes[i].sexo);
        printf("Histórico Médico: %s\n", pacientes[i].historico_medico);
    }
}

int main() {
    struct Paciente pacientes[100];
    int totalPacientes = 0;
    int opcao;

    do {
        printf("\nProntuário Eletrônico\n");
        printf("1. Adicionar Paciente\n");
        printf("2. Listar Pacientes\n");
        printf("3. Sair\n");
        printf("Escolha uma opção: ");
        scanf("%d", &opcao);

        switch (opcao) {
            case 1:
                adicionarPaciente(pacientes, &totalPacientes);
                break;
            case 2:
                listarPacientes(pacientes, totalPacientes);
                break;
            case 3:
                printf("Encerrando o programa.\n");
                break;
            default:
                printf("Opção inválida. Tente novamente.\n");
        }
    } while (opcao != 3);

    return 0;
}
