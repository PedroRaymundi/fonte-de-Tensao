# Fonte de Tensão
O objetivo final desse projeto é criar uma fonte de tensão com uma entrada de 127V AC 
e saída variável entre 3V e 12V com corrente contínua e 100mA

## Materiais
Materiais|Especificações|Preço
---------|--------------|-----
Transformador|16V 1A|+-R$50
Potenciômetro|2KΩ|+-R$1,04
Diodo (4x)|400V 3A|+-R$1,00
Capacitor|470uF 100V|+-R$3,13
Diodo Zener|13V (1W)|+-R$0,19
Resistor 1|220Ω (1W)|+-R$0,12
Resistor 2|820Ω (2W)|+-R$0,22
Transistor NPN|16V 1A|+-R$1,00

OBS: Alguns dos componentes podem ser encontrados por preços melhores e também podem ser substituídos por outros a fim de manter uma corrente mais estável. A escolha de diversos dos componentes utilizados nesse projeto foram a disponibilidade. Por exemplo: o transformador de 16V não é tão adequado quanto um de 20V para cima, entretanto só havia esse transformador a venda localmente quando o projeto foi iniciado.

## Projeto
Passo a passo de como montar o projeto e resumo da função de cada componente:
* #### Transformador:
    O transformador é conectado diretamente na tomada a fim de reduzir a corrente e a voltagem padrão da tomada para 16V e 1A. O objetivo disso é deixar mais fácil trabalhar com o sistema já que agora é possível utilizar componentes eletrônicos mais baratos que só precisam aguentar os 16V no lugar dos 127V. Além disso, também aproxima do resultado final desejado para o projeto e deixa o trabalho com o circuito mais seguro.
* #### Diodos:
    Antes de conectar os diodos ao circuito é necessário fazer uma ponte de diodos. Para isso é preciso pegar os quadro diodos e juntá-los seguindo o exemplo das fotos abaixo. Isso é feito porque o diodo só permite a passagem da corrente em uma direção (no caso do projeto seria a direção da flecha e, nos diodos reais, é a direção que vai da parte preta para a faixa cinza no diodo) e, com essa ponte montada, podemos utilizar os dois sentidos da corrente alternada que vai sair do transformador. Por esse motivo, conectaremos as pontas 1 e 2 (olhar desenho abaixo) do diodo no transformador.

    ![ponte_de_diodo_foto](/Imagens/diodos_foto.png)   ![ponte_de_diodo_projeto](/Imagens/diodos.png)
* #### Capacitor:
    O capacitor serve para suprir a corrente energética enquanto a corrente da tomada está na inversão de fase e assim ajuda o circuito a manter uma corrente mais linear em todos os períodos. A partir desse momento é preciso tomar cuidado com a parte positiva e negativa do circuito, já que a ponte de diodos faz com que a corrente sempre saia do ponto 3 para o ponto 4. Por isso, é preciso conectar a parte positiva do capacitor em paralelo com a saída 3 e a parte negativa do capacitor com o ponto 4.
* #### Resistor 220Ω e diodo zener:
    O diodo zener serve apenas para limitar a voltagem (nesse caso em 13V), portanto, não há necessidade de passar muita corrente por ele, por esse motivo o resistor de 220Ω é colocado em série ao zener.
* #### Resitor 820Ω e potenciômetro:
    Para regular a voltagem entre 3V e 12V é usado o potenciômetro em série com o resistor de 820Ω, o resistor serve para limitar a voltagem mínima em 3V. Esse sistema é conectado entre o resistor de 220Ω e o diodo zener, seguindo o esquema a seguir:

    ![potenciometro_projeto](/Imagens/potenciometro.png)
* #### Transistor NPN:
    Para o transistor funcionar ele precisa de aproximadamente 0,7V do circuito, transformando assim os 13V (que haviam sido regulados pelo zener) em 12,3V, deixando quase que exatamente o que era pedido para o projeto. O seu funcionamento gira em torno justamente dessa necessidade de haver uma dirferança entre as voltagens, ou seja, o transistor interrompe a energia quando a voltagem começa a subir para além do que passa em sua base, e após isso acontecer, a voltagem diminui até ficar menor do que a que passa pela base, ligando novamente o transistor e voltando a passar a voltagem previamente regulada.

    ![transistor_projeto](/Imagens/transistor.png)

* #### Resultado final:
    ![circuito](/Imagens/Circuito.png)
    OBS: o resistor de 120Ω 

    [projeto final](http://tinyurl.com/ycepgu2t)

## Soluções para problemas
Já em simulações é perceptível 2 problemas no projeto que podem ser facilmente solucionáveis:
* Existe uma pequena variação na voltagem e corrente final. Sendo a variação máxima 0,728V e 8,498mA entre picos e vales de corrente;
* Uma quantidade de corrente considerável passa pelo diodo zener sem necessidade;

Consertar cada um dos problemas é relativamente simples. Para isso será necessário:
1. Para o primeiro problema:
    1. Um potenciômetro de 5K;
    2. Um resistor de 2.2K;
2. Para o segundo problema:
    1. Um transformador de aproximadamente 20V;
    2. Um resistor de 1.2K;

Dito isso, o ideal seria aplicar essas duas resoluções simultaneamente. Mas caso não seja possível aplicar apenas uma delas já é muito preferível do que manter como está.

#### Resolvendo o primeiro problema
Para diminuir essa variação de corrente e voltagem, é preciso simplesmente trocar o potenciômetro original (2K) pelo novo potenciômetro (5K). Além disso, o resistor que está em série com o potenciômetro (820Ω) deve ser trocado pelo novo (2,2K).

[simulação com a primeira solução](http://tinyurl.com/ycsxajha)

#### Resolvendo o segundo problema
Para parar a perda de corrente que passa pelo diodo zener basta trocar o transformador de 16V pelo de 20V e trocar o resistor de 220Ω pelo de 1,2K.

[simulação com a segunda solução](http://tinyurl.com/ycv6hq6u)

[simulação com as duas soluções](http://tinyurl.com/ybmaza7z)

## EAGLE
### Projeto esquemático
![projeto_esquematico](/Imagens/projetoesquematico.png)

### Projeto PCB
![projeto_pcb](/Imagens/projetopcb.png)

## Feito por:
* Pedro Henrique Raymundi, nUSP: 11795634
[video com o projeto finalizado](https://youtu.be/qeKwLvBPG0Y)
