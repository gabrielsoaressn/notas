### Recaptulando:
*   Polling
A CPU verifica ativamente alterações no estado do controlador e é responsável pela tranferência de dados;
*   Interrupt
A CPU é notificada sobre as alterações no estado do controlador e é responsável pela tranferência de dados;
*   DMA
A CPU é notificada sobre as alterações no esado do controlador de DMA e o DMA é responsável pela transferência de dados.

##   Sistemas multiproessadores
### Entendendo
* A maioria dos sistemas utiliza um único processador de propósito geral(de PDAs a _mainframes_)
  * Alguns sistemas possuem processador de propósito específico
*   Multiprocessadores tem aummentado em importância e uso:
    *   Também conhecidos como sistemas paralelos ou sistemas de alto acoplamento;
    *   Vantagens:
        1.  Maior vazão(throughput)
        2.  Economia de escala
        3.  Maior confiabilidade, degradação suave(limpa) ou tolerância a falhas.
    *   Dois tipos:
        1. Simétrico (todos são iguais e executam as mesmas funções)
        2. Assimétrico(tem o mecanismo mestre-escravo)  
##  Clusters
### Entendendo
*   Como multiprocessadores, porém com vários sistemas trabalhando juntos;
*   Geralmente compartilham armazenamento através de redes;
*   Fornece um serviço de alta disponibildade que sobrevive a falhas;
*   Clusters comumente são utilizados para **computação de alto desempenho**(HCP);
    *   As ações precisam ser projetadas para explorar o paralelismo.
## Estrutura do SO
###   Sistema de Batch(sistema de lote)
*   Obtém um grande número de jobs juntos, executa-os sequencialmente e gera dados para uma fila de impressão;
###   Multiprogramação
*   É necessária para garantir ouso eficiente dos recursos;
*   Um único usuário não consegue manter todos os disposotivos E/S ocupados ao mesmo tempo;
*   Organiza os _jobs_(códigos e dados) de maneira que a CPU sempre tenha algo a executar;
    *   Um subconjunto de todos os jobs do sistema é mantido em memória;
    *   um dos _jobs_ é selecionado para executar por um **escalonador de _jobs_**;
    *   Quando o _job_ precisar esperar por algo(E/S, por exemplo), o SO passa a executar outro _job_.
### Compartilhamento de tempo(multitarefas)
*   Rápida alternância da CPU entre vários _jobs_;
*   Fundamental para computação **interativa**;
*   Tempo de Respota tem que ser << 1s
    *   Cada usuário tem pelo menos um programa executando na memória: **processo**;
    *   Se vários _jobs_ estão prontos para serem executados ao mesmo tempo **escalomento de CPU**;
    *   Se os processos não cabem na memória, **swap** os move rapidamente para fora e para dentro da memória quando necessário;
    *   **Memória virtual**: permite que um processo possa ser executado sem estar totalmente carregado na memória principal.
  ## OBS:
  * O ambiente multitarefa precisa tomar o cuidado de utilizar os valores mais recentes, não importando onde eles estejam na hierarquia de armazenamento;
  * Um ambiente com múltiplos processadores precisa prover **coerência de cache** em hardware para garantir que todas as CPUs tenhasm os valores mais recentes em suas caches
  * Em ambientes distribuídos a situação é ainda mais complexa:
    * Podem haver várias cópias completas dos dados
  
### Proteção de um SO
*   Comunicação baseada em eventos;
    *   Interrupções geradas pelo hardware;
    *   _Traps_ geradas por softwares:
        *   Requisição de um serviço do sistema operacional;
        *   Divisão por zero, loops infinitos, processos modificando/acessando memória de outro processo ou do SO;
*   Operação em _dual-mode_ permite que o SO se proteja e proteja os outros componentes do sistema:
    *   Modo usuário e moro kernel
    *   Bit de modo fornecido pelo hardware
        *   Permite distinguir quando o sistema está executando o código do usuário ou do núcleo;
        *   Alagumas intruções são  designadas como privilegiadas e são executadas apenas no modo kernel;
        *   Uma chamada de sistema altera para o modo kernel e o retorno da chamada altera de volta para o modo usuário.
*   Timer para previnir loops infinitos/processos sobrecarregando os recursos
    *   Agenda a ocorrência de uma interrupção;
    *   Sistema operacional decrementa um contador;
    *   Quando chega a zero, ocorre a interrupção;
    *   Configurado antes de ativar o processo para reobter o controle ou encerrar um processo que exceda o tempo permitido.