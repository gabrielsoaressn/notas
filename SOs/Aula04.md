# Processos de um SO

*   Um SO executa uma variedade de programas:
    *   Sistemas Batch: jobs
    *   Sistemas de compartilhamento de tempo: programas de usuário
*   Jobs e processos são sinônimos
*   Processo: um programa em execução
    *   Sua execução avança de forma sequencial
*   Um processo incui:
    *   Contador de programa: próxima instrução
    *   Pilha: dados temporários
    *   Seção de dados: variáveis globais
## Programa vs. Processo

*   Programa
    *   Pode ter várias instâncias em execução(diferentes processos)
    *   Algorítimo codificado
    *   Forma como o programador vê a tarefa a ser executada
*   Processo
    *   É único
    *   Código acompanhado de dados e estado
    *   Forma como o SO vê o programa e possibilita sua execução
##  Estados de um processo
*   Durante sua execução, um processo muda de estado inúmeras vezes
    *   novo: o processo está sendo criado
    *   executando: instruções do processo estão sendo executadas
    *   esperando: O porcesso aguarda que algum evento ocorra
    *   pronto: o processo aguarda ser escalonado para o processador
    *   finalizado: a execução do processo foi concluida
## Bloco de Controle de processo(PCB)

*   Informações associadas a cada processo
    *   Estado do processo
        *   Qual estado se encontra atualmente

    *   Contador de Programa
        *   Endereço da próxima instrução
    *   Registradores de CPU
        *   Necessários para continuar a execução após a interrupçao
    *   Informações para escalonamento da CPU
        *   Prioridade, ponteiro para a fila de escalonamento
    *   Informações para a gerência da memória
        *   Registradores base e limite, ponteiros para tabela de páginas e tabela de segmentos
    *   Informação para contabilidade
        *   Tempo de CPU, tempo total, tempo bloqueado, etc
    *   Estados das operações E/S
        *   Lista de dispositivos alocados ao processo, lista de dispositivos abertos.

## Filas de escalonamento de processos

*   Fila de jobs: conjunto de todos os processos do sistema
*   Fila de prontos: fila de todos os  processos aguardando o escalonamento da CPU
*   Fila de dispositivos: conjunto de processos aguardando um dispostivo E/S
*   Os processos migram entra as diferentes filas