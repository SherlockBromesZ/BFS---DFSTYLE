# Breadth-First Search (BFS)

O algoritmo de busca em largura (BFS) é um método para percorrer ou pesquisar em uma estrutura de dados de grafo. Ele começa em um vértice de origem e explora todos os vértices vizinhos na camada atual antes de passar para a próxima camada. Este algoritmo é comumente usado para encontrar o caminho mais curto em grafos não ponderados e também é útil em muitas outras aplicações, como a detecção de ciclos em grafos.

## Passo a Passo

Vamos explicar o funcionamento do algoritmo BFS usando um exemplo simples de um grafo não direcionado. Considere o seguinte grafo:

```
4 4
0 1
1 2
2 3
3 0
```

1. **Construção do Grafo:** O grafo possui 4 vértices numerados de 0 a 3 e 4 arestas que formam um ciclo simples.

2. **Execução do Algoritmo BFS:**

    - Começamos a busca a partir do vértice 0.
    - Vamos usar uma fila para manter os vértices a serem visitados.
    - Inicializamos uma lista de visitados, onde todos os vértices estão inicialmente marcados como não visitados.
    - Visitamos o vértice 0 e o marcamos como visitado.
    - Colocamos o vértice 0 na fila.
    - Começamos a explorar os vizinhos de 0.
    - Imprimimos o vértice visitado.
    - Continuamos esse processo até não houver mais vértices na fila.
    - A ordem de visitação será: 0 -> 1 -> 3 -> 2.

## Código Completo (C++)

```cpp
#include<bits/stdc++.h>
using namespace std;

void bfs(int inicio, vector<vector<int>> &grafo, vector<bool> &visitado){
    visitado[inicio] = true;
    queue<int> fila;
    fila.push(inicio);
    
    while(!fila.empty()){
        int atual = fila.front();
        fila.pop();
        
        cout << atual << " ";
        
        for(int visinho : grafo[atual]){
            if(!visitado[visinho]){
                fila.push(visinho);
                visitado[visinho] = true;
            }
        }
    }
}

int main()
{
    int n, m; cin >> n >> m;
    
    vector<vector<int>> grafo(n);
    
    for(int i = 0; i < m; i++){
        int u, v;
        cin >> u >> v;
        grafo[u].push_back(v);
        grafo[v].push_back(u);
    }
    
    vector<bool> visitado(n, false);
    
    bfs(0, grafo, visitado);
    
    return 0;
}
```
