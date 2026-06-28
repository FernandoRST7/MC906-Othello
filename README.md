# Othello AI Agent

Este repositório contém a implementação de um agente de inteligência artificial para o jogo Othello, desenvolvido como trabalho prático para a disciplina **MC906 - Introdução à Inteligência Artificial** na UNICAMP (Abril/2026).

O projeto explora a comparação entre diferentes heurísticas e técnicas de busca para a tomada de decisão em um jogo de soma zero.

## Principais Funcionalidades

* **Algoritmo de Busca**: Implementação do **Minimax** integrado com poda **Alfa-Beta** para redução do espaço de estados.
* **Busca Iterativa**: Uso de *Iterative Deepening* para contornar limites de tempo (0.95s por jogada) e garantir uma decisão válida.
* **Ordenação de Jogadas**: Estratégia que pré-avalia movimentos para maximizar a eficiência da poda Alfa-Beta.
* **Heurísticas**:
    * **Greedy (Gulosa)**: Baseline baseada no saldo material (diferença de peças).
    * **Static (Posicional Estática)**: Baseada em uma matriz de pesos 8x8 que valoriza o controle territorial e cantos.
    * **Dynamic (Dinâmica)**: Combinação linear de saldo, mapa posicional e métrica de mobilidade, com pesos ajustados para o início, meio e fim de jogo.

## Resultados Experimentais

* **Poda Alfa-Beta**: Permitiu explorar profundidades maiores no mesmo intervalo de tempo, superando o Minimax puro (ex: 12.23 contra 9.00 camadas).
* **Desempenho**: A heurística **Static** obteve o melhor desempenho, derrotando a *Dynamic* em 79.2% das partidas e o *baseline (Greedy)* em 95.8%.
* **Complexidade**: O gargalo computacional reside na geração e verificação de novos movimentos, sendo que o *mid-game* apresenta a maior dificuldade de processamento.

## Como Executar

Requisitos básicos:

- **Python**: versão 3.8+ (recomendado 3.10+).
- **Dependências**: `pygame` e `numpy`.

Instalação rápida (recomendado usar um virtualenv):

```bash
python -m pip install --upgrade pip
pip install pygame numpy
# ou, se preferir, crie um requirements.txt e use:
# pip install -r requirements.txt
```

Executar o jogo (janela gráfica):

```bash
python main.py
```

- **Configuração da heurística**: edite a variável `HEURISTIC` em `main.py` e escolha `"dynamic"`, `"static"` ou `"greedy"`. O padrão é `"dynamic"`.
- **Tempo da IA**: o limite por jogada é controlado pela constante `AI_TIME_LIMIT_SECONDS` em `main.py` (padrão 0.95s).
- **Profundidade máxima**: controlada por `AI_MAX_DEPTH` em `main.py`.

Se quiser rodar sem interface (scripts de avaliação), verifique os arquivos em `evaluation/`.

## Equipe
Trabalho desenvolvido pelos alunos:
* Bruno Jambeiro Mesquita
* Lucas Rodrigues de Mendonça
* Fernando Rodrigues da Silva
* Thiago Augusto de Tulio Nascimento
* Victor Itiro Ogitsu