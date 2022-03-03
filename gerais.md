# Agenda
## Cadeiras
### Computação Gráfica SU/QA (8h)
### Circuitos Lógicos II SU/QA (14h)

### Engenharia de Software SU/QA (16h)
#### para casa
-   ler o slide da aula 03, no google drive e fazer anotações.
-   fazer o exercício em grupo.
### Eletricidade II T/QI (8h)

### Calculo Numérico - T/QI (10h)
<meet.google.com/qwz-fsxa-bsv>

### Sistemas Operacionais T/QI(14h) 
<meet.google.com/ujq-ukvs-hxp>
#### para casa
reler as anotações.

### Análise e Projeto de Algorítmos T/QI(16h)

## Bootcamp GFT Java
#### Lembretes:
* Uma variável double pode receber uma int e uma int só recebe uma double por meio de casting.
* Herença múltipla é quando uma classe herda de várias. Isso não acontece em java.
* Upcast em herança é transformar uma classe filha em uma classe mãe e downcast é justamente o contrário.(O downcast não é muito desejável).
```
Cachorro cachorro = new Animal();             //up
Animal cachorro = (Cachorro)new Animal();     //down
```
*   Polimorfismo tem que apresentar comportamento diferente e sobrescrita pode mostrar, mas não é obrigatório
*   Dependência é um método que utiliza um objeto como parâmetro.
*   Inteface em java é algo como uma classe que só tem a assinatura dos métodos que serão implementados nas classes que apresentarem o "implements" sobre a interface.
  
 ```
interface MinhaInterface
{
    ...
}

class MinhaClasse implements Minhainterface
{
    ...
}
```
*   Métodos estáticos são criados para que não precise-se utilizar objetos para utilizar aqueles métodos.