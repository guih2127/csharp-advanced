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
  
É interessante utilizar o transient na maioria das vezes, já que eles tem tempo de vida curto, além disso, não precisamos nos preocupar com cenários multithread e memory-leaks.
Se quisermos manter o estado do serviço em uma requisição, devemos utilizar o scoped.
Por último, o Singleton deve ser utilizado com cuidado. Em um caso onde o nosso repositório é populado com um .json inicialmente, ele pode ser útil já que ele não vai ficar reiniciando a lista em cada uma das requisições.
Mais sobre injeção de dependência aqui: https://code-maze.com/dependency-injection-lifetimes-aspnet-core/

### SOLID
O SOLID é um conjunto de cinco princípios considerados como boas práticas de programação, ajudando a reduzir o acoplamento de código e facilitando na refatoração, sendo eles:

1 - Single Responsability Principle -> Trata-se de classes e metódos possuírem apenas UMA responsabilidade. Isso ajuda a desaclopar o código, além de facilitar os testes unitários da aplicação.

2 - Open Closed Principle -> Diz que as classes devem estar abertas para extensão e fechadas para modificação. Ou seja, devemos extender o comportamento de uma classe através de heranças, interfaces e composições, mas não devemos permitir a abertura da classe para fazer pequenas alterações.
Por exemplo, se tivermos uma classe DebitoConta(), que possui um metódo Debitar() que recebe um tipoConta; fazendo um IF para cada tipo de conta, talvez não seja a melhor implementação. O ideal seria criar uma classe abstrata DebitoConta e, a partir disso, criar classes que sobrescrevam o metodo Debitar().
Esse requisito facilita no desacoplamento e também na adição de novos requisitos e funcionalidades, diminuindo chances de introduzir bugs na aplicação.

3 - Liskov Substitution Principle -> Diz que as classes/tipos base devem poder ser substituídos por qualquer uma das suas subclasses. A criadora deste princípio ponderava sobre os cuidados necessários para utilizar herança.
Alguns exemplos de violação deste princípio são: Sobrescrever/implementar um metódo que não faz nada, lançar uma exceção inesperada ou retornar valores de tipos diferentes da classe base.
Esse princípio nos permite utilizar o polimorfismo com mais confiança. Podemos chamar nossas classes derivadas referindo-se à classe base sem preocupações com resultados inesperados.

4 - Interface Segregation Principle -> Esse princípio nos diz que várias interfaces específicas são melhores que apenas uma ou poucas interfaces maiores. Módulos devem possuir poucos comportamentos e serem enxutos. Interfaces com muitos comportamentos se tornam mais difícil de evoluir.
Podemos saber que estamos violando este princípio se tivermos uma classe que segue uma interface e, essa classe, por sua vez, não precisa implementar um dos metódos dela. Nesse caso, seria melhor termos uma interface específica para essa classe.

5 - Dependency Inversion Principle -> Esse princípio consiste em dois conceitos: Módulos de alto nível não devem depender de módulos de baixo nível e abstrações não devem depender de detalhes. Detalhes devem depender de abstrações.
Para implementar esse padrão utilizando .NET, podemos utilizar a Injeção de dependência, fazendo com que módulos de baixo nível tenham um contrato (interface) e os módulos de nível mais alto tenham apenas que utilizar essa interface para utilizar seus metódos. Essa ténica remove a dependência entre entidades.

Mais sobre SOLID aqui: https://medium.com/beelabacademy/princ%C3%ADpios-de-s-o-l-i-d-em-c-guia-pr%C3%A1tico-cbb1e6584284