# Conceitos .NET

### Coleções
Coleções servem para manipular dados. A plataforma .NET nos proporciona várias delas, e é interessante saber qual escolher em uma determinada situação. Por exemplo, se precisarmos de uma coleção performática e que não necessite de ordenação, podemos utilizar um Dictionary, pois ele tem pesquisa e manipulação extremamente eficientes, com complexidade O(1) para essas operaçoes.
Mais sobre coleções aqui: https://www.macoratti.net/12/12/c_col1.htm

### Programação Assíncrona
Na maioria das linguagens imperativas, incluindo o C#, a execução dos metódos é contínua. Ou seja, uma vez que uma thread de controle comece a executar um metódo, ela ficará ocupada com essa tarefa até que a execução do metódo seja concluída.
Muitas vezes esse sincronismo é um problema, pois as vezes a thread fica ocupada sem fazer nada, apenas esperando "algo" acontecer, seja esse algo um download, um cálculo, etc, tornando a experiência do usuário ruim.
Ao utilizarmos programação assíncrona, com async await, criamos uma outra thread, desbloqueando a thread principal e à permitindo executar outras operações.
A utilização de código assíncrono faz sentido em cenários de grande volumes de dados ou complexidade de processamento quanto o tempo impacta o desenvolvimento.
Mais sobre programação assíncrona aqui: https://imasters.com.br/back-end/c-programacao-assincrona-async-e-await

### Generics
Generics possibilitam a criação de classes e metódos que adiam a especificação de um ou mais tipos até que a classe ou metódo seja declarado e instanciado pelo código do cliente. Ao usar um parâmetro com o tipo genérico T, podemos garantir uma maior reutilização do código. Quando uma classe genérica é instanciada com um tipo, T sempre será daquele tipo. Por exemplo, se uma classe GenericList<T> for instanciada com new GenericList<int>(), todas as ocorrências de T serão substituídas por int.
Mais sobre generics aqui: https://learn.microsoft.com/pt-br/dotnet/csharp/fundamentals/types/generics

### Injeção de dependência
A injeção de dependência é um recurso que permite a injeção das dependências do lado de fora da classe, onde a classe que a dependência está sendo injetada só precisa saber do contrato (interface ou classe abstrata), tornando a classe independente de seus objetos.
Ela ajuda também a escrever testes unitários, visto que apenas uma classe específica precisa ser testada, e as dependências podem ser substituídas por uma classe simulada, que contém dados de teste. Além disso, ela ajuda a deixar o código menos acoplado.
Para definir o mapeamento das interfaces para suas classes concretas, devemos utilizar um conteiner de injeção de dependências e, dentro dele, temos três opções para mapear os tipos:

- Singleton: Um objeto do serviço será criado para todas as requisições.
- Escope: Um objeto do serviço será criado para cada requisição.
- Transient: Um objeto do serviço será criado toda vez que o objeto for requisitado.
- 
É interessante utilizar o transient na maioria das vezes, já que eles tem tempo de vida curto, além disso, não precisamos nos preocupar com cenários multithread e memory-leaks.
Se quisermos manter o estado do serviço em uma requisição, devemos utilizar o scoped.
Por último, o Singleton deve ser utilizado com cuidado. Em um caso onde o nosso repositório é populado com um .json inicialmente, ele pode ser útil já que ele não vai ficar reiniciando a lista em cada uma das requisições.
Mais sobre injeção de dependência aqui: https://code-maze.com/dependency-injection-lifetimes-aspnet-core/

### SOLID
