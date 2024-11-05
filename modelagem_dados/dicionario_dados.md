# Dicionário de dados
### Referência: 
Sistema de biblioteca digital com suas principais entidades e relacionamentos.

## Implementando o DD. no sistema de referência
Esse dicionário inclui detalhes adicionais sobre os atributos, incluindo tamanhos e restrições, além de uma breve descrição dos métodos.
## 

| **Entidade**      | **Atributo**           | **Tipo de Dados** | **Tamanho** | **Obrigatório** | **Descrição**                                                                                 | **Restrições**                                   |
|-------------------|------------------------|-------------------|-------------|-----------------|-----------------------------------------------------------------------------------------------|-------------------------------------------------|
| **Pessoa**        | `id`                   | `int`             | -           | Sim             | Identificador único para a pessoa.                                                            | Deve ser único.                                 |
|                   | `nome`                 | `string`          | 100         | Sim             | Nome completo da pessoa.                                                                      | Não pode estar vazio, máximo 100 caracteres.    |
|                   | `bi`                   | `string`          | 14          | Sim             | Número de Bilhete de Identidade (BI) da pessoa.                                               | Deve ter 14 caracteres, deve ser único.         |
|                   | `cadastrar()`          | `método`          | -           | -               | Método para cadastrar uma nova pessoa no sistema.                                             | -                                               |
|                   | `actualizarDados()`    | `método`          | -           | -               | Método para atualizar os dados da pessoa.                                                    | -                                               |
| **Usuario**       | `email`                | `string`          | 150         | Sim             | Endereço de email do usuário.                                                                 | Deve ser um endereço de email válido e único.   |
|                   | `senha`                | `string`          | 64          | Sim             | Senha do usuário para autenticação no sistema (hash criptografado).                           | Deve ser armazenada em hash, mínimo 8 caracteres. |
|                   | `fazerLogin()`         | `método`          | -           | -               | Método para o usuário realizar o login.                                                       | -                                               |
| **Bibliotecario** | `categoria`            | `string`          | 50          | Sim             | Categoria do bibliotecário, indicando o nível de atuação ou responsabilidades.                | Deve ser um valor válido.                       |
|                   | `gerenciarEmprestimos()`| `método`         | -           | -               | Método para o bibliotecário gerenciar empréstimos.                                            | -                                               |
|                   | `gerarRelatorio()`     | `método`          | -           | -               | Método para o bibliotecário gerar relatórios de atividades.                                   | -                                               |
| **Livro**         | `isbn`                 | `int`             | 13          | Sim             | Código ISBN que identifica unicamente o livro.                                                | Deve ser único, 13 dígitos.                     |
|                   | `titulo`               | `string`          | 255         | Sim             | Título do livro.                                                                              | Não pode estar vazio, máximo 255 caracteres.    |
|                   | `autor`                | `string`          | 100         | Sim             | Nome do autor do livro.                                                                       | Não pode estar vazio, máximo 100 caracteres.    |
|                   | `anoPublicacao`        | `int`             | 4           | Sim             | Ano de publicação do livro.                                                                   | Deve ser um ano válido (por exemplo, >= 1900).  |
|                   | `editora`              | `string`          | 100         | Não             | Nome da editora que publicou o livro.                                                         | Máximo 100 caracteres.                          |
|                   | `disponivel`           | `bool`            | -           | Sim             | Estado de disponibilidade do livro para empréstimo (`true` para disponível).                  | -                                               |
|                   | `emprestar()`          | `método`          | -           | -               | Método para realizar o empréstimo de um livro.                                                | -                                               |
|                   | `devolver()`           | `método`          | -           | -               | Método para devolver um livro emprestado.                                                     | -                                               |
|                   | `atualizarStatus()`    | `método`          | -           | -               | Método para atualizar o status de disponibilidade do livro.                                   | -                                               |
| **Emprestimo**    | `id`                   | `int`             | -           | Sim             | Identificador único para o empréstimo.                                                        | Deve ser único.                                 |
|                   | `dataEmprestimo`       | `DateTime`        | -           | Sim             | Data em que o empréstimo foi realizado.                                                       | Não pode ser no futuro.                         |
|                   | `dataDevolucao`        | `DateTime`        | -           | Não             | Data de devolução do livro, se houver.                                                        | -                                               |
|                   | `status`               | `string`          | 20          | Sim             | Status atual do empréstimo, como "ativo", "renovado" ou "finalizado".                         | Não pode estar vazio, deve ser um dos estados válidos. |
|                   | `calcularMulta()`      | `método`          | -           | -               | Método para calcular a multa em caso de devolução atrasada.                                   | -                                               |
|                   | `renovar()`            | `método`          | -           | -               | Método para renovar a data de devolução do empréstimo.                                        | -                                               |
|                   | `finalizar()`          | `método`          | -           | -               | Método para finalizar o empréstimo, indicando a devolução do livro.                           | -                                               |
| **Categoria**     | `id`                   | `int`             | -           | Sim             | Identificador único da categoria.                                                             | Deve ser único.                                 |
|                   | `nome`                 | `string`          | 50          | Sim             | Nome da categoria do livro, como "Literatura", "Ciência", etc.                                | Não pode estar vazio, deve ser único.           |
|                   | `descricao`            | `string`          | 255         | Não             | Descrição detalhada da categoria.                                                             | Máximo 255 caracteres.                          |
|                   | `adicionarLivro()`     | `método`          | -           | -               | Método para adicionar um livro à categoria.                                                   | -                                               |
|                   | `removerLivro()`       | `método`          | -           | -               | Método para remover um livro da categoria.                                                    | -                                               |

### Notas sobre Restrições

- As restrições garantem a integridade dos dados e ajudam a prevenir erros durante o processamento.
- As regras de negócio específicas, como as condições para validar e gerenciar os empréstimos, também devem ser implementadas nas funções associadas.

Esse formato proporciona uma visão clara e concisa das entidades, seus atributos, suas restrições e suas responsabilidades dentro do sistema, facilitando tanto a implementação quanto a manutenção.