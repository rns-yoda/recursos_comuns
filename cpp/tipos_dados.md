# Tipos de Dados em C++

Em C++, os **tipos de dados** são fundamentais para definir a natureza dos valores que uma variável pode armazenar. Eles especificam a quantidade de memória que será alocada e os tipos de operações que podem ser realizadas. Os tipos de dados em C++ são divididos principalmente em categorias básicas, compostas, derivadas e vazias, conforme detalhado abaixo.

### 1. **Tipos de Dados Básicos**
Os tipos de dados básicos são usados para representar valores numéricos e caracteres.

| Tipo     | Descrição                    | Tamanho Médio      | Exemplo           |
|----------|------------------------------|--------------------|-------------------|
| `int`    | Número inteiro               | 2 ou 4 bytes      | `int idade = 20;`|
| `float`  | Número de ponto flutuante (precisão simples) | 4 bytes   | `float peso = 70.5;` |
| `double` | Número de ponto flutuante (precisão dupla) | 8 bytes    | `double pi = 3.1415;` |
| `char`   | Caractere                    | 1 byte            | `char letra = 'A';` |
| `bool`   | Valor booleano (verdadeiro/falso) | 1 byte      | `bool ativo = true;` |

### 2. **Modificadores de Tipo**
Modificadores podem ser usados para alterar o tamanho e o intervalo de tipos de dados numéricos.

| Modificador | Usado com           | Descrição                          | Exemplo                 |
|-------------|----------------------|------------------------------------|-------------------------|
| `signed`    | `int`, `char`       | Inclui números negativos           | `signed int x = -5;`    |
| `unsigned`  | `int`, `char`       | Somente números positivos          | `unsigned int y = 10;`  |
| `short`     | `int`               | Reduz o tamanho do tipo            | `short int z = 1000;`   |
| `long`      | `int`, `double`     | Aumenta o tamanho do tipo          | `long int w = 1000000;` |

### 3. **Tipos de Dados Compostos**
Esses tipos permitem armazenar múltiplos valores de diferentes ou mesmo tipos.

| Tipo     | Descrição                       | Exemplo                        |
|----------|---------------------------------|--------------------------------|
| `array`  | Conjunto de elementos do mesmo tipo | `int notas[5] = {90, 85, 88, 70, 95};` |
| `struct` | Agrupamento de variáveis de diferentes tipos | `struct Pessoa { int idade; char nome[50]; };` |
| `union`  | Armazena diferentes tipos em um único espaço de memória | `union Dados { int i; float f; };` |
| `enum`   | Tipo enumerado para definir constantes nomeadas | `enum Cor { VERMELHO, VERDE, AZUL };` |

### 4. **Tipos de Dados Derivados**
Esses tipos derivam dos tipos básicos para criar novos comportamentos.

| Tipo         | Descrição                         | Exemplo                            |
|--------------|-----------------------------------|------------------------------------|
| `pointer`    | Armazena o endereço de memória de outra variável | `int *ptr = &idade;`               |
| `reference`  | Referência a outra variável       | `int &ref = idade;`                |
| `function`   | Tipo de dado para definir funções | `int soma(int a, int b) { return a + b; }` |

### 5. **Tipo de Dados Vazio**
Usado para indicar ausência de valor ou para definir funções sem retorno.

| Tipo   | Descrição                               | Exemplo                        |
|--------|-----------------------------------------|--------------------------------|
| `void` | Indica ausência de tipo/retorno         | `void mostraMensagem() { cout << "Olá!"; }` |

### Exemplo com Diversos Tipos de Dados

```cpp
#include <iostream>
using namespace std;

struct Pessoa {
    int idade;
    char nome[50];
};

int main() {
    int inteiro = 10;
    float decimal = 3.14;
    bool logico = true;
    char letra = 'C';

    // Array
    int numeros[3] = {1, 2, 3};

    // Struct
    Pessoa p1;
    p1.idade = 30;
    strcpy(p1.nome, "Carlos");

    cout << "Inteiro: " << inteiro << endl;
    cout << "Decimal: " << decimal << endl;
    cout << "Lógico: " << logico << endl;
    cout << "Letra: " << letra << endl;
    cout << "Array[0]: " << numeros[0] << endl;
    cout << "Pessoa: " << p1.nome << " tem " << p1.idade << " anos" << endl;

    return 0;
}
```

### Resumo
Os tipos de dados em C++ permitem definir variáveis com diferentes tamanhos e funcionalidades, oferecendo flexibilidade para lidar com várias operações e estruturas. Entender esses tipos ajuda a gerenciar a memória e a garantir a integridade dos dados em um programa.


### Nota
Para mais detalhes sobre tipos de dados em C++, consulte a documentação oficial em [cppreference.com](https://en.cppreference.com/w/cpp/language/types). 
