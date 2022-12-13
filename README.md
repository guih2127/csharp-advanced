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