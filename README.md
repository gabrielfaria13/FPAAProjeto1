# Implementação do Algoritmo de Karatsuba

## Descrição do Projeto

Este projeto implementa o algoritmo de Karatsuba, uma técnica eficiente para multiplicação de números inteiros grandes. O método reduz a complexidade da multiplicação direta, tornando-se útil para cálculos de alta performance.

### Como o algoritmo funciona

1. Divide os números de entrada em duas partes.
2. Calcula três multiplicações menores recursivamente.
3. Combina os resultados para obter o produto final.

## Como Executar o Projeto

1. Certifique-se de ter o Python instalado (versão 3.6 ou superior).
2. Clone este repositório:
   ```sh
   git clone <URL_DO_REPOSITORIO>
   ```
3. Entre no diretório do projeto:
   ```sh
   cd FPAAProjeto1
   ```
4. Execute o script:
   ```sh
   python main.py
   ```

### Explicação do Algoritmo

O algoritmo de Karatsuba divide dois números grandes em partes menores para realizar multiplicações mais eficientes. A ideia principal é evitar a multiplicação direta de dois números grandes ao quebrá-los em partes menores e realizar três multiplicações menores em vez de quatro.

1. **Divisão**: O número é dividido em duas partes aproximadamente iguais.
2. **Recursão**: São realizadas três multiplicações menores:
   - `z0 = low1 * low2`
   - `z1 = (low1 + high1) * (low2 + high2)`
   - `z2 = high1 * high2`
3. **Combinação**: O resultado final é obtido a partir das multiplicações menores:
   - `(z2 * 10^(2*m)) + ((z1 - z2 - z0) * 10^m) + z0`

Essa abordagem reduz a complexidade para **O(n^log₂3) ≈ O(n^1.585)**, tornando-se mais eficiente que a multiplicação convencional O(n²) para números grandes.

## Análise Técnica

### Complexidade Ciclomática

A complexidade ciclomática pode ser calculada pela fórmula: **M = E - N + 2P**

- **E (arestas)**: Número de transições entre blocos de código.
- **N (nós)**: Quantidade de blocos de decisão e execução.
- **P**: Número de componentes conexos (1 para um único programa).

O fluxo do algoritmo pode ser representado graficamente e analisado com ferramentas como draw\.io ou Lucidchart.

### Complexidade Assintótica

O algoritmo de Karatsuba tem uma complexidade temporal de **O(n^log₂3) ≈ O(n^1.585)**, sendo mais eficiente que a multiplicação tradicional **O(n²)** para números grandes.

### Melhor, Médio e Pior Caso

- **Melhor caso:** Números pequenos onde a multiplicação direta é aplicada.
- **Caso médio:** Números grandes de mesmo tamanho.
- **Pior caso:** Números de tamanhos muito diferentes, levando a divisões desbalanceadas.

## Diagrama

![image](https://github.com/user-attachments/assets/2b3dd5d8-f0e2-4f3a-8754-4e3b7bda1223)



#





