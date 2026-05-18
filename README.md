# Implementação de AGM - TDE4

Integrantes do grupo:
- Gustavo Lazzari
- Mateus Roese
- Matheus Yamamoto
- Victor Ryuki

Projeto referente à matéria *Resolução de Problemas com Grafos* que estende o analisador de contatos Enron com a implementação da **Árvore Geradora Mínima (AGM)** utilizando o algoritmo de Prim. O programa constrói um grafo a partir do dataset de e-mails da Enron e determina a subárvore de conexões mais relevantes a partir de um vértice de origem, priorizando as arestas de menor peso.

## 1. Como executar

Antes de executar, certifique-se de que a pasta `Amostra Enron` com os e-mails está presente no mesmo diretório que o `main.py`.

```zsh
python main.py
```

## 2. Estrutura do Repositório

```
.
├── aresta.py      # Classe Aresta, armazena o destino e o peso de uma aresta
├── vertice.py     # Classe Vertice, armazena id, rótulo e lista de adjacências
├── grafo.py       # Classe Grafo, implementa todas as operações sobre o grafo (carregamento, análise, buscas, Dijkstra adaptado e algoritmo de Prim)
├── main.py        # Script principal que carrega os dados e executa a geração da Árvore Geradora Mínima
└── README.md      
```

## 3. Operações disponíveis

- `adicionar_mensagem(remetente, destinatario)` - adiciona ou incrementa o peso da aresta entre dois endereços de e-mail
- `obter_vertices()` - retorna o número total de vértices (indivíduos únicos) no grafo
- `obter_arestas()` - retorna o número total de arestas (relações de envio) no grafo
- `top_20_grau_saida()` - retorna os 20 indivíduos com maior grau de saída (mais e-mails enviados) e os valores correspondentes
- `top_20_grau_entrada()` - retorna os 20 indivíduos com maior grau de entrada (mais e-mails recebidos) e os valores correspondentes
- `buscar_caminho_dfs(origem, destino)` - percorre o grafo em profundidade e retorna o caminho entre dois vértices como lista de nós visitados
- `buscar_caminho_bfs(origem, destino)` - percorre o grafo em largura e retorna o caminho entre dois vértices como lista de nós visitados
- `nos_distancia_d(no, d)` - retorna todos os nós que estão a exatamente `d` arestas de distância de um nó `n`
- `caminho_critico_dijkstra(origem, destino)` - calcula o caminho crítico usando Dijkstra adaptado com o inverso do peso das arestas, retornando o custo e a rota
- `arvore_geradora_minima_prim(email_raiz)` - calcula a Árvore Geradora Mínima a partir de um vértice de origem usando o algoritmo de Prim, retornando o custo total e a lista de arestas que compõem a árvore

## 4. Exemplo de uso

Saída do programa `main.py`, que lê os e-mails da pasta `Amostra Enron` e executa a geração da Árvore Geradora Mínima:

```
ANALISADOR DE CONTATOS ENRON
[*] Lendo e-mails da pasta: 'Amostra Enron'...
[*] Processo concluído! 30109 e-mails lidos.

============================================================
TESTANDO ROTAS ENTRE: jeff.dasovich@enron.com -> richard.shapiro@enron.com
============================================================

Árvore Geradora Mínima (Algoritmo de Prim) a partir de jeff.dasovich@enron.com:
Custo Total da Árvore: 1021
Arestas que compõem a Árvore (Origem -> Destino [Peso]):
  jeff.dasovich@enron.com -> richard.shapiro@enron.com [Peso: 204]
  jeff.dasovich@enron.com -> james.steffes@enron.com [Peso: 189]
  jeff.dasovich@enron.com -> steven.kean@enron.com [Peso: 175]
  jeff.dasovich@enron.com -> ray.alvarez@enron.com [Peso: 163]
  jeff.dasovich@enron.com -> susan.mara@enron.com [Peso: 156]
  jeff.dasovich@enron.com -> paul.kaufman@enron.com [Peso: 134]
  ...
  ... e mais 1375 conexões.

============================================================
```
