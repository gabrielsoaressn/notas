# Aula 01
## O que é?
    É o responsável por fazer requisições das aplicações do usuário para o hardware.
## Objetivo do SO
    Seu objetivo é facilitar o caminho para o usuário utilizar sistemas computacionais e utilizar o hardware de forma mais eficiente
## Por que estudar?
*     Para exercitar uma infinidade de conceitos estudados na comptação
*     Porque entendendo um SO, é possível compreender as soluções que serão implementadas por sobre ele.

###     1. Gerenciamento de recursos
*   O sistema operacional se encarrega de escolher qual aplicação deve ter piroridade e recursos computacionais para ser executada primeiro e desempata situações conflitantes.
*   Compartilha coisas que todos os programas devem utilizar. Ex: Espaço de memória.
*   Controla a execução de programas para prevenir o uso indevido do computador
  
###     2. Disposições dos SOs
*   Todos os dispositivos acessam(competem para a execução de um ciclo) um controlador ou adaptador: controlador de discos, controlador usb, adaptador gráfico. Controladores e CPU se ligam em barramento à memória.
*   Controladores têm miniprocessadores e buffers. Eles utilizam esses buffers para dados temporários. Quando vai passar algo para a CPU, ele passa primeiro pelo buffer, depois passa.

###     3. Interrupções
*   Quando um controlador precisa passar alguma informação, ele envia uma mensagem para a CPU para sinalizar, por meio de uma interrupção, que está perdendo a informação do buffer , para que a CPU possa fazer uso daquela memória.
*  Os SOs funcionam baseados em interrupções
*  Quando ocorre uma interrupção, o SO precisa saber onde parou e desabilitar novas interrupções enquanto a corrente não termina
    OBS: Exceção ou Trap é o nome dado a interrupçção via software
#### Tratamento de Interrupções
*   O SO preserva o estado da CPU e armazena seus contadores e registradores.
*   Registra o tipo de interrupção que ocorreu
*   Segmentos do código determinam que ação deve ser tomada para cada tipo de interrupção
  
### 4. Estrutura de E/S
*   Síncrona(Polling): O controle retorna para o programa do usário somente quando terminar a operação. Só uma execução E/S por  vez(não é permitido paralelismo).
*   Assíncrona(Interrupção): O controle retorna para o programa do usuário antes do fim da execução da terefa. Uma interrupção é usada para informar o programa do usuário que a operação terminou. O programa do usuário pode usar a chamada de sistema para esperar esplicitamente que a operação E/S acabe
#### Estrutura de Acesso direto à memória(DMA)
*   Utilizada por dispositivos E/S rápidos, capazes de transmitir dados a velocidades próximas a memória principal
*   Direct Memory Acess(DMA): Controlador dedicado a tranferir dados entre a memória principal e outros controladores e vice-versa
    * O mecanismo de interrupções é utilizado somente para avisar à CPU que a transferência acabou ou que houve erros.
##### Funcionamento do DMA
O controlador do DMA assume o papel de _bus master_ e dirige todo o tráfego entre a memória e o controlador do periférico. Envolve 3 passos:
1. A CPU indica ao DMA a identidade do controlador, o tipo da operação, o endereço da memória por acessar e o número de bytes a transferir
2. O DMA incia a operação, arbitra o barramento e transfere os dados na direção apropriada. O próprio DMA fornece vários endereços de memória para todo o bloco de dados para ler ou escrever. É possível completar uma transferência de várias centenas de milhares de dados sem incomodar a CPU
3. Uma vez que a tranferência está terminada, o DMA interrompe a CPU. A CPU lê os registros do DMA para saber se a operação foi realizada com sucesso ou não. 

##### Dificuldade

*   A CPU e o DMA acessam simultaneamente a mesma região de memória. Isso gera um problema de contenção. Com a utilização de cache, a CPU evita utilizar a memória principal a maior parte do tempo, diminuindo a contenção
*   Em um sistema sem DMA, apenas o processador acessa a memória. Num sistema com DMA, no mínimo dois controladores acessam. Se o DMA estiver fazendo uma escrição na memória e este mesmo item está presente na cache do CPU, então esses valores ficam diferentes. Se o DMA está fazendo uma leitura na memória e o cache é _write-back_ então o DMA pode estar lendo um valor desatualizado(problema de incoerência)

##### Soluções
*   Fazer o tráfego do DMA passar pela cache(ineficiente)
*   Fazer o SO ou o hardware invalidar as linhas da cache que são afetadas pela escrita do DMA(cache flushing) e forçar o _wriite-back_ das linhas que são lidas pelo DMA 