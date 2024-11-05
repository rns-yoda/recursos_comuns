# Dicionário de dados
### Referência: 
[Sistema de biblioteca digital](https://github.com/rns-yoda/analise-sistemas/blob/main/aulas/anexos/diagramaclasse_biblioteca.md) com suas principais entidades e relacionamentos.

## Implementando o DD. no sistema de referência
Esse dicionário inclui detalhes adicionais sobre os atributos, incluindo tamanhos e restrições, além de uma breve descrição dos métodos.
## 


| **Entidade**      | **Atributo**           | **Tipo de Dados** | **Tamanho** | **Obrigatório** | **Descrição**                                                                                 | **Restrições**                                   |
|-------------------|------------------------|-------------------|-------------|-----------------|-----------------------------------------------------------------------------------------------|-------------------------------------------------|
| **Pessoa**        | `id`                   | `numérico`        | -           | Sim             | Identificador único para a pessoa.                                                            | Deve ser único.                                 |
|                   | `nome`                 | `texto`           | 100         | Sim             | Nome completo da pessoa.                                                                      | Não pode estar vazio, máximo 100 caracteres.    |
|                   | `bi`                   | `texto`           | 14          | Sim             | Número de Bilhete de Identidade (BI) da pessoa.                                               | Deve ter 14 caracteres, deve ser único.         |
| **Usuario**       | `email`                | `texto`           | 150         | Sim             | Endereço de email do usuário.                                                                 | Deve ser um endereço de email válido e único.   |
|                   | `senha`                | `texto`           | 64          | Sim             | Senha do usuário para autenticação no sistema (hash criptografado).                           | Deve ser armazenada em hash, mínimo 8 caracteres. |
| **Bibliotecario** | `categoria`            | `texto`           | 50          | Sim             | Categoria do bibliotecário, indicando o nível de atuação ou responsabilidades.                | Deve ser um valor válido.                       |
| **Livro**         | `isbn`                 | `numérico`        | 13          | Sim             | Código ISBN que identifica unicamente o livro.                                                | Deve ser único, 13 dígitos.                     |
|                   | `titulo`               | `texto`           | 255         | Sim             | Título do livro.                                                                              | Não pode estar vazio, máximo 255 caracteres.    |
|                   | `autor`                | `texto`           | 100         | Sim             | Nome do autor do livro.                                                                       | Não pode estar vazio, máximo 100 caracteres.    |
|                   | `anoPublicacao`        | `numérico`        | 4           | Sim             | Ano de publicação do livro.                                                                   | Deve ser um ano válido (por exemplo, >= 1900).  |
|                   | `editora`              | `texto`           | 100         | Não             | Nome da editora que publicou o livro.                                                         | Máximo 100 caracteres.                          |
|                   | `disponivel`           | `boleano`         | -           | Sim             | Estado de disponibilidade do livro para empréstimo (`true` para disponível).                  | -                                               |
| **Emprestimo**    | `id`                   | `numérico`        | -           | Sim             | Identificador único para o empréstimo.                                                        | Deve ser único.                                 |
|                   | `dataEmprestimo`       | `data/hora`       | -           | Sim             | Data em que o empréstimo foi realizado.                                                       | Não pode ser no futuro.                         |
|                   | `dataDevolucao`        | `data/hora`       | -           | Não             | Data de devolução do livro, se houver.                                                        | -                                               |
|                   | `status`               | `texto`           | 20          | Sim             | Status atual do empréstimo, como "ativo", "renovado" ou "finalizado".                         | Não pode estar vazio, deve ser um dos estados válidos. |
| **Categoria**     | `id`                   | `numérico`        | -           | Sim             | Identificador único da categoria.                                                             | Deve ser único.                                 |
|                   | `nome`                 | `texto`           | 50          | Sim             | Nome da categoria do livro, como "Literatura", "Ciência", etc.                                | Não pode estar vazio, deve ser único.           |
|                   | `descricao`            | `texto`           | 255         | Não             | Descrição detalhada da categoria.                                                             | Máximo 255 caracteres.                          |


### Descrição dos Métodos

| **Entidade**      | **Método**               | **Descrição**                                                                                                 |
|-------------------|--------------------------|---------------------------------------------------------------------------------------------------------------|
| **Pessoa**        | `cadastrar()`            | Realiza o cadastro de uma nova pessoa no sistema, verificando se os dados estão completos e válidos.         |
|                   | `actualizarDados()`      | Atualiza os dados da pessoa no sistema, como nome ou BI.                                                      |
| **Usuario**       | `fazerLogin()`           | Verifica as credenciais do usuário (email e senha) e concede acesso ao sistema se forem válidas.              |
| **Bibliotecario** | `gerenciarEmprestimos()` | Controla e organiza os empréstimos feitos na biblioteca, incluindo novos empréstimos e devoluções.            |
|                   | `gerarRelatorio()`       | Gera um relatório das atividades, como número de empréstimos ou livros devolvidos em um determinado período.  |
| **Livro**         | `emprestar()`            | Marca o livro como emprestado, atualizando o status de disponibilidade.                                       |
|                   | `devolver()`             | Marca o livro como devolvido, atualizando o status para disponível.                                           |
|                   | `atualizarStatus()`      | Altera o estado de disponibilidade do livro, usado em ações como "emprestar" ou "devolver".                   |
| **Emprestimo**    | `calcularMulta()`        | Calcula uma multa com base nos dias de atraso para devolução do livro.                                        |
|                   | `renovar()`              | Renova o prazo de devolução do empréstimo, permitindo ao usuário mais tempo para devolver o livro.            |
|                   | `finalizar()`            | Finaliza o empréstimo, indicando que o livro foi devolvido e encerrando o registro.                           |
| **Categoria**     | `adicionarLivro()`       | Adiciona um livro a uma categoria específica, permitindo organizar o acervo.                                  |
|                   | `removerLivro()`         | Remove um livro da categoria, mantendo a organização do acervo da biblioteca.                                 |

 

### Notas sobre Restrições

- As restrições garantem a integridade dos dados e ajudam a prevenir erros durante o processamento.
- As regras de negócio específicas, como as condições para validar e gerenciar os empréstimos, também devem ser implementadas nas funções associadas.

Esse formato proporciona uma visão clara e concisa das entidades, seus atributos, suas restrições e suas responsabilidades dentro do sistema, facilitando tanto a implementação quanto a manutenção.
