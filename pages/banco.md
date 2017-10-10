---
layout: page
title:  "Simulação de Fila de Banco"
categories: ed
exclude: true
---

![](/pages/banco/figura.png)

## DESCRIÇÃO

[Repositório com o código do Projeto](https://github.com/qxcodeed/simulacao_banco)

Neste trabalho, nós simularemos uma fila de banco. O nosso banco tem clientes que estão sendo atendidos no caixa e clientes em espera na fila. Cada cliente tem um nível de paciência (quantidade de tempo que ele pode esperar na fila) e uma quantidade de documentos a serem processados no caixa.

Você deve manter uma laço. Cada iteração representa um minuto passado no banco. A cada iteração: 

* Chega um número aleatório de clientes no banco que entram no fim da fila.
* Se houverem caixas livres, os clientes da frente da fila devem ocupá-los.
    * Os clientes na *fila* devem ter sua paciência decrementada em uma unidade.
*  Se a paciência de um cliente na fila chegar a zero, ele deve sair da fila (o cliente desistiu de esperar). 
* Para os clientes no caixa, cada iteração deve diminuir um na quantridade de documentos.
    * Se o número de documentos de um cliente no caixa chegar a zero ele deve sair do banco (deixar o caixa).

Cada novo cliente que chega no banco deve ter seus atributos gerados aleatoriamente. Existem 3 variáveis na simulação, o valor da *paciência*, a quantidade de *documentos* e a quantidade de *clientes* que chega por iteração.

Os valores devem ser gerados entre o mínimo e máximo de cada atributo aleatório. Se paciência é de [1 - 10] então cada cliente tem entre 1 e 10 de paciência. Se clientes é de [0 - 3] então chegam de 0 a 3 clientes por interação.

Ao início de cada simulação você decide o número de caixas [1 - 10], que deve permanecer o mesmo até o fim da simulação. 

## ESTRUTURAS
A estrutura que representa o cliente é a seguinte:
```c++
    struct Cliente
    {
        int paciencia;
        int documentos;

        Cliente(int paciencia, int documentos)
        {
            this->paciencia = paciencia;
            this->documentos = documentos;
        }
    };
```

As variáveis globais estão no arquivo globais.h. Elas guiam a simulação
e definem parâmetros para a parte gráfica.

```c++
//Cada dia possui 6 horas de trabalho
//60 minutos x 6 horas = 360 minutos
//cada minuto eh um turno.
const int TURNOS_DIA = 360;

//A paciencia maxima pode ser alterada.
//Ela é usada para criar o efeito de cores
//na visualização da simulação.
const int MAX_PACIENCIA = 20;

//A quantidade máxima de caixas não pode ser alterada.
const int MAX_CAIXAS = 10;

//Esse valor determina o quanto o banco por caixa por dia de trabalho
const int CUSTO_CAIXA_DIA = 100;

//numero de simulacoes de teste para cada caixa
const int N_EXEC_TESTE = 100;
```


## VISUALIZAÇÃO
Se você quiser ver a simumalação deverá passar duas estruturas por parâmetro à função que gera a visualização.

A estrutura que deve ser usada na simulação para representar os clientes no caixa, será um vector.
```c++
    std::vector<Cliente*> 
```
Para representar os clientes na fila, você deve usar uma lista encadeada.
```c++
    std::list<Cliente*>
```
Observe que o mesmo cliente criado(alocado) no inicio da simulação deve ser transferido entre os containers(vector e list) e desalocado apenas ao sair do banco.

Para visualizar a simulação graficamente, você pode usar a classe Pintor.
Crie um objeto Pintor no inicio do método main:
```c++
    Pintor pintor;
```
e chame o método desenhar passando o vetor de clientes no caixa e a lista de clientes na fila.
```c++
    pintor.desenhar(caixa, fila);
```

No projeto já existe uma função chamada simulação que mostra o banco pra você.

## VALOR ÓTIMO
Agora que sua simulação está funcionando vamos para a parte divertida. O dono do banco lhe contratou para descobrir qual a quantidade ideal de caixas que devem ser colocados na agência para que o banco tenha o maior lucro possível. Observe que poucos caixas fazem a fila crescer e os clientes desistirem e muitos caixas implicam numa folha de pagamento mais alta.

Considere que cada documento processado rende ao banco R$ 1,00. Considere também o custo de um caixa para o banco é de R$ 100 por dia. Encontre para cada situação pedida (*paciencia, documentos, clientes*) a quantidade de caixas que o banco deve colocar que lhe dê maior lucro em um dia (o expediente do banco é de 6 hrs por dia, o que dão 360 iterações na nossa simulação).

Faça a simulação para cada quantidade de caixas várias vezes e descubra qual a quantidade que dá o maior rendimento ao banco. Abaixo, algumas simulações que você pode executar e comparar com o valor esperado.

No arquivo de simulação existe uma função executar_testes(). Ela chama a função otimizar_lucro(...) que você deve implementar e compara se o valor da sua otimização gera o resultado esperado.
### ALGUMAS SAÍDAS ESPERADAS

#### Simulação 01

* Numero de clientes chegando: 0 - 1
* Paciência dos clientes: 1 - 60
* Documentos por cliente: 1 - 10
* Qtd. ideal de caixas: 4

#### Simulação 02

* Numero de clientes chegando: 0 - 2
* Paciência dos clientes: 1 - 20
* Documentos por cliente: 1 - 10
* Qtd. ideal de caixas: 8

#### Simulação 03

* Numero de clientes chegando: 0 - 5
* Paciência dos clientes: 1 - 25
* Documentos por cliente: 1 - 10
* Qtd. ideal de caixas: 10

#### Simulação 04

* Numero de clientes chegando: 0 - 4
* Paciência dos clientes: 1 - 5
* Documentos por cliente: 1 - 2
* Qtd. ideal de caixas: 6 - 7

Verifique se não há vazamento de memória. Instale o valgrind, vá no QtCreator, Analyze, Valgring Memory Analyzer. Ele vai verificar os vazamentos de memória.

Bom trabalho e se não conseguir fazer algo, procure ajuda e continue tentando.
