# Implementação do Algoritmo de Karatsuba

## Descrição do Projeto

Este projeto implementa o **Algoritmo de Karatsuba**, uma técnica de multiplicação eficiente para números inteiros grandes. O algoritmo foi desenvolvido por Anatolii Alexeevitch Karatsuba em 1960 e é amplamente utilizado devido à sua capacidade de reduzir a complexidade da multiplicação tradicional, especialmente quando lidamos com números de tamanho considerável.

O algoritmo de Karatsuba tem uma complexidade assintótica de **O(n^log₂3) ≈ O(n^1.585)**, o que o torna mais eficiente do que a multiplicação convencional com complexidade **O(n²)**. Isso é particularmente útil em áreas como a criptografia e o processamento de grandes números em algoritmos matemáticos.

## Como o Algoritmo Funciona

A ideia central do algoritmo de Karatsuba é dividir a multiplicação de dois números grandes em multiplicações menores e mais simples, reduzindo o número de multiplicações necessárias.

### Etapas do Algoritmo:

1. **Divisão dos Números**: O número original é dividido em duas partes aproximadamente iguais. Por exemplo, para multiplicar os números `x` e `y`, a ideia é dividir ambos em duas partes: uma parte "alta" e uma parte "baixa".
   
2. **Cálculos Recursivos**:
   - **z0**: Multiplica as partes baixas dos números.
   - **z1**: Multiplica a soma das partes baixas e altas de ambos os números.
   - **z2**: Multiplica as partes altas dos números.
   
3. **Combinação dos Resultados**: Com base nos três cálculos (z0, z1, z2), o resultado final da multiplicação é obtido combinando-os de maneira eficiente.

### Exemplo de Divisão e Combinação

Suponha que queremos multiplicar dois números `x` e `y`, onde:

- `x = high1 * 10^m + low1`
- `y = high2 * 10^m + low2`

A multiplicação é dividida em três partes:

- `z0 = low1 * low2`
- `z1 = (low1 + high1) * (low2 + high2)`
- `z2 = high1 * high2`

O resultado final será:

\[
x * y = (z2 * 10^{2m}) + ((z1 - z2 - z0) * 10^m) + z0
\]

### Código de Implementação:

```python
def karatsuba(x, y): 
    """
    Implementação do algoritmo de Karatsuba para multiplicação eficiente de números inteiros.
    """
    # Caso base: números pequenos multiplicados diretamente
    if x < 10 or y < 10:
        return x * y
    
    # Determinar o tamanho dos números
    n = max(len(str(x)), len(str(y)))
    m = n // 2
    
    # Dividir os números em partes
    high1, low1 = divmod(x, 10**m)
    high2, low2 = divmod(y, 10**m)
    
    # Recursivamente calcular três produtos menores
    z0 = karatsuba(low1, low2)
    z1 = karatsuba((low1 + high1), (low2 + high2))
    z2 = karatsuba(high1, high2)
    
    # Combinar os resultados
    return (z2 * 10**(2*m)) + ((z1 - z2 - z0) * 10**m) + z0

# Solicitar valores do usuário
a = int(input("Digite o primeiro número: "))
b = int(input("Digite o segundo número: "))

# Calcular o resultado usando Karatsuba
resultado = karatsuba(a, b)

# Exibir o resultado
print(f"Resultado da multiplicação de {a} e {b} usando Karatsuba: {resultado}")
```

## Como Executar o Projeto

1. Certifique-se de ter o Python instalado (versão 3.6 ou superior).
2. Clone este repositório:
   ```sh
   git clone https://github.com/gabrielfaria13/FPAAProjeto1.git
   ```
3. Entre no diretório do projeto:
   ```sh
   cd FPAAProjeto1
   ```
4. Execute o script:
   ```sh
   python main.py
   ```

## Exemplo de Execução

### Exemplo 1:

Ao rodar o programa, você será solicitado a digitar dois números para multiplicação. Por exemplo:

```yaml
Digite o primeiro número: 1234
Digite o segundo número: 5678
```
O programa então calculará e exibirá o resultado:
```yaml
Resultado da multiplicação de 1234 e 5678 usando Karatsuba: 7006652
```
Explicação do Exemplo:
O número 1234 é dividido em high1 = 12 e low1 = 34.

O número 5678 é dividido em high2 = 56 e low2 = 78.

```yaml
z0 = low1 * low2 = 34 * 78 = 2652
z1 = (low1 + high1) * (low2 + high2) = (34 + 12) * (78 + 56) = 46 * 134 = 6164
z2 = high1 * high2 = 12 * 56 = 672
```
Finalmente, o resultado é calculado como:

```yaml
1234 * 5678 = (672 * 10^4) + ((6164 - 672 - 2652) * 10^2) + 2652
1234 * 5678 = 7006652
```
Este é o mesmo resultado exibido no terminal.

## Explicação Detalhada do Algoritmo


### Passo 1: Divisão dos Números

Primeiro, o número é dividido em duas partes de acordo com o número de dígitos:

- `x = high1 * 10^m + low1`
- `y = high2 * 10^m + low2`

Onde `m` é aproximadamente a metade do número de dígitos de `x` ou `y`.

### Passo 2: Cálculos Recursivos

Para os números divididos, o algoritmo realiza três multiplicações recursivas:

- **z0**: Multiplicação das partes baixas dos dois números: `z0 = low1 * low2`
- **z1**: Multiplicação da soma das partes baixas e altas dos dois números: `z1 = (low1 + high1) * (low2 + high2)`
- **z2**: Multiplicação das partes altas: `z2 = high1 * high2`

### Passo 3: Combinação dos Resultados

Com as três multiplicações menores (`z0`, `z1`, `z2`), o produto final é obtido com a fórmula:

\[
x * y = (z2 * 10^{2m}) + ((z1 - z2 - z0) * 10^m) + z0
\]

## Complexidade Assintótica

O algoritmo de Karatsuba tem uma complexidade temporal de **O(n^log₂3) ≈ O(n^1.585)**, onde `n` é o número de dígitos dos números de entrada. Em comparação com a multiplicação convencional, que tem complexidade **O(n²)**, o algoritmo de Karatsuba é consideravelmente mais rápido para números grandes.

## Análise Técnica

### Complexidade Ciclomática

A complexidade ciclomática mede a complexidade do fluxo de controle do algoritmo, levando em consideração a quantidade de decisões e ramificações. Para o algoritmo de Karatsuba, a complexidade ciclomática pode ser calculada usando a fórmula:

\[
M = E - N + 2P
\]

Onde:
- **E** é o número de arestas no grafo de controle.
- **N** é o número de nós no grafo de controle.
- **P** é o número de componentes conexos (para um único programa, **P = 1**).

### Casos de Complexidade

- **Melhor Caso**: Quando os números são pequenos e a multiplicação direta é aplicada.
- **Caso Médio**: Quando os números têm tamanho semelhante, o algoritmo tem desempenho ótimo.
- **Pior Caso**: Quando os números são de tamanhos muito diferentes, a divisão pode ser desbalanceada, mas ainda assim o algoritmo é mais eficiente do que a multiplicação direta.

## Diagrama

Aqui está o diagrama do fluxo do algoritmo de Karatsuba:

![image](https://github.com/user-attachments/assets/2b3dd5d8-f0e2-4f3a-8754-4e3b7bda1223)

