---
layout: post
title:  "Ordenação"
category: 'sort'
introduction: Selection, Bubble, Insertion, Merge e Quick.
description:
image: '/assets/ordenacao/figura.png'
tags:
- ordenação
- recursão
---


# Módulo de ordenação

Existem duas pastas aqui. Ambos são projetos do qtcreator para serem rodados no linux. 
A pasta projeto\_c é para quem vai implementar ordenação em c puro.
A pasta projeto\_cpp é para quem vai implementar em c++.

## Assista o vídeo.

<iframe width="560" height="315" src="https://www.youtube.com/embed/D_3RdjAMKco" frameborder="0" allowfullscreen></iframe>

## Atividades do módulo.

1. Implementar um embaralhador de vetor.
2. Criar um vetor crescente e embaralhe.
3. Implementar o minimum de forma que em cada laco ele encontre o mínimo e o máximo.
4. Implementar o bubble sort
5. Implementar o selection sort.
5. Implementar o quick sort
6. Implementar o merge sort
7. Implementar o bucket sort

## Funções da biblioteca

```c
//pinta o vetor vet, de tamanho qtd.
//pos é um vetor com os elementos a serem marcados.
//colors uma string com a cor de cada um dos elementos a serem marcados.
void view_show(int *vet, int qtd, int * pos, const char * colors,);

//para a visualização ser em gráfico de barras.
void view_set_bar();

//para a visualização ser em gráfico de pontos.
void view_set_dot();

//pinta uma faixa amarela abaixo dos índices de begin até end.
void view_set_faixa(int begin, int end);

//precisa ser o último comando da main para manter o player aberto.
void view_lock();
```