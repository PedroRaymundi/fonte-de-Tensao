# Fonte de Tensão
O objetivo final desse projeto é criar uma fonte de tensão com uma entrada de 127V AC 
e saída variável entre 3V e 12V com corrente contínua e 100mA

## Materiais
Materiais|Especificações|Preço
---------|--------------|-----
Transformador|16V 1A|+-R$50
Potenciômetro|2K|+-R$1,04
Diodo (4x)|400V 3A|+-R$1,00
Capacitor|470uF 100V|+-R$3,13
Diodo Zener|13V (1W)|+-R$0,19
Resistor 1|220R (1W)|+-R$0,12
Resistor 2|820R (2W)|+-R$0,22
Transistor NPN|16V 1A|+-R$1,00

OBS: Alguns dos componentes podem ser encontrados por preços melhores e também podem sersubstituídos por outros a fim de manter uma corrente mais estável. A escolha de diversos dos componentes utilizados nesse projeto foram a disponibilidade. Por exemplo: o transformador de 16V não é tão adequado quanto um de 20V para cima, entretanto só havia esse transformador a venda localmente quando o projeto foi iniciado.

## Projeto
Passo a passo de como montar o projeto e resumo da função de cada componente:
* ###### Transformador:
    O transformador é conectado diretamente na tomada a fim de reduzir a corrente e a voltagem padrão da tomada para 16V e 1A. O objetivo disso é deixar mais fácil trabalhar com o sistema já que agora é possível utilizar componentes eletrônicos mais baratos que só precisam aguentar os 16V no lugar dos 127V. Além disso, também aproxima do resultado final desejado para o projeto e deixa o trabalho com o circuito mais seguro.
* ###### Diodos:
    Antes de conectar os diodos ao circuito é necessário fazer uma ponte de diodos. Para isso é preciso pegar os quadro diodos e juntá-los seguindo o exemplo das fotos abaixo. Isso é feito porque o diodo só permite a passagem da corrente em uma direção (no caso do projeto seria a direção da flecha e, nos diodos reais, é a direção que vai da parte preta para a faixa cinza no diodo) e, com essa ponte montada, podemos utilizar os dois sentidos da corrente alternada que vai sair do transformador. Por esse motivo, conectaremos as pontas 1 e 2 (olhar desenho abaixo) do diodo no transformador.

    <img src-"/Imagens/diodos_foto.jfif" width-"291">   ![ponte_de_diodo_projeto](/Imagens/diodos.png)


![circuito](/Imagens/Circuito.png)

Resistor 3|120R (2W)|+-R$0,22

## Soluções para problemas
Já em simulações é perceptível 2 problemas no projeto que podem ser facilmente solucionáveis:
* Existe uma pequena variação na voltagem e corrente final. Sendo essa o máximo de variação 0,728V e 8,498mA entre picos e vales de corrente;
* Uma quantidade de corrente considerável passa pelo diodo zener sem necessidade;

Consertar cada um dos problemas é relativamente simples. Para isso será necessário:
1. Para o primeiro problema:
    1. Um potenciômetro de 5K;
    2. Um resistor de 2.2K;
2. Para o segundo problema:
    1. Um transformador de aproximadamente 20V;
    2. Um resistor de 1.2K;

Dito isso, o ideal seria aplicar essas duas resoluções simultaneamente. Mas caso não seja possível aplicar apenas uma delas já é muito preferível do que manter como está.

###### Resolvendo o primeiro problema
Para diminuir essa variação de corrente e voltagem, é preciso simplesmente trocar o potenciômetro original (2K) pelo novo potenciômetro (5K). Além disso, o resistor que está em série com o potenciômetro (820R) deve ser trocado pelo novo (2,2K).

[simulação com a primeira solução](http://tinyurl.com/ycsxajha)

###### Resolvendo o segundo problema
Para parar a perda de corrente que passa pelo diodo zener basta trocar o transformador de 16V pelo de 20V e trocar o resistor de 220R pelo de 1,2K.

[simulação com a segunda solução](http://tinyurl.com/ycv6hq6u)

[simulação com as duas soluções](http://tinyurl.com/ybmaza7z)

## EAGLE

## Feito por:
* Pedro Henrique Raymundi, nUSP: 11795634
