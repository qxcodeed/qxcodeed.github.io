---
layout: page
title:  "Matrizes"
categories: ed
exclude: true
---
# Matrizes

![](/pages/matrizes/figura.png)

## Assista o vídeo

<iframe width="560" height="315" src="https://www.youtube.com/embed/Slds2NRYLGo" frameborder="0" allowfullscreen></iframe>

## Atividades

- Transforme o algoritmo da queimada em um algoritmo de pintura.
    - Deixe o usuário clicar em um ponto.
    - Verifique qual a cor desse ponto.
    - Pinte todos os pontos vizinhos da mesma cor do ponto inicial de vermelho.

---
- Construir os metodos de pegar vizinhos para 4 e 8 vizinhos.

```c++
//vizinhos das 4 direções
vector<Par> get_vizinhos(Par par);

//vizinhos das 8 direções
vector<Par> get_all_vizinhos(Par par);
```
---
- Utilize o retorna da recursão para contar quantar árvores queimaram.

```c++
int contar_queimados(matriz<char>& mat, Par pos);
```

---
- Construir os metodos de embaralhar.

```c++
//retorna uma cópia de vet embaralhado.
vector<int> embaralhar(vector<int> vet);
```

---

- Preencher uma imagem recursivamente aleatoriamente mostrando o nivel da recursao.
    - Utilize a opção de pintar a matriz de inteiros para acompanhar o nível da recursão.

```c++
int nlin = 30;
int ncol = 50;
matriz<char> matc(nlin, ncol, 'y');//cria uma matriz de char
matriz<int>  mati(nlin, ncol, 0);//cria uma matriz de int

mat_draw(matc);//pinta as cores
mat_draw(mati);//pinta os números
ed_show();//mostra o estado
```
---
- Peça dois pontos para o usuário e mostre o caminho que leva de um ponto à outro.

```c++
//dado inicio e fim, pos guarda a posição corrente
void procurar_caminho(matriz<char>& mat, Par inicio, Par fim, Par pos);
```

---
- Faça a função contarVizinhosAbertos.
    - Um vizinho aberto é um espaço que já foi furado ou espaço fora da matriz.

```c++
int contarVizAbertos(matriz<char>& mat, Par pos);
```
---
- Faça o algoritmo de construir o labirinto perfeito usando recursão.

```c++
void create_lab(matriz<char>& mat, Par pos){
    verifique se por esta dentro da matriz
    verifique se pos eh parede
    verifique se pos pode ser furado
        so pode ser furado se so tiver no maximo 1 vizinho aberto
        se puder furar, fure
        se nao, retorne
    pegue todos os vizinhos
    embaralhe
    chame a recursao para cada vizinho
}
```
---
- Faça o código de construção do labirinto usando pilha.

```c++
void create_lab_pilha(matriz<char>& mat){
    inicie uma pilha de pares
    fure o primeiro elemento e coloque na pilha

    enquanto a pilha nao estiver fazia faca{
        topo eh o par do topo da pilha
        pegue os vizinhos de topo que podem ser furados
            voce soh pode pegar os vizinhos que tem no maximo um lado aberto
        se existe pelo menos um vizinho valido pra furar
            selecione aleatoriamente um desses vizinhos
            fure e empilhe
        se nao existe
            desempilhe o topo
    }
}
```
---
- Resolver o labirinto usando pilha.
    - Utilize a mesma lógica da pilha para encontrar o caminho entre dois pontos dentro do lab.

---
- Faça o algoritmo de floodfill utilizando lista.

---
- Faça o algoritmo de pathfindind usando o floodfill.