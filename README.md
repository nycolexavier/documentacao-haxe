## Sumário

### 1. Introdução

#### 1.1 O que é Haxe?

#### 1.2 Sobre esse documento

##### 1.2.1 Autores e contribuidores

##### 1.2.2 Licença

#### Hello World

#### História

##### 1.1 O que é Haxe?

Consiste em uma linguagem de alto nível, open source e compilada. Ela permite a compilação de programas escritos usando uma sintaxe orientada a ECMAScript, para várias linguagens de destino. Empregando a forma correta, é possível manter uma única base de código que compila para várias plataformas.

Haxe tem uma tipagem forte, but the typing system can be subverted where required. Utilizando type information, o Haxe pode detectar erros em tempo de compilação que só seriam perceptíveis em tempo de execução na linguagem de destino. Além disso, as informações do type podem ser usadas pelo compilador para gerar código otimizado e robusto.

Atualmente, existem nove linguagems de destino suportados que permitem diferentes casos de uso:

| Nome       | Tipo de saída | Principais usos                        |
| ---------- | ------------- | -------------------------------------- |
| JavaScript | Sourcecode    | Browser, Desktop, Mobile, Server       |
| Neko       | Bytecode      | Desktop, Server, CLI                   |
| HashLink   | Bytecode      | Desktop, Mobile, Game consoles         |
| PHP        | Sourcecode    | Server                                 |
| Python     | Sourcecode    | Desktop, Server                        |
| Lua        | Sourcecode    | Desktop, Scripting                     |
| C++        | Sourcecode    | Desktop, Mobile, Server, Game consoles |
| Flash      | Bytecode      | Desktop, Mobile                        |
| Java       | Sourcecode    | Desktop, Mobile, Server                |
| JVM        | Bytecode      | Desktop, Mobile, Server                |
| C#         | Sourcecode    | Desktop, Mobile, Server                |

O restante desta seção fornece uma breve visão geral de como é a linguagem Haxe e como ele evoluiu desde seuinício, em 2005.

[Types]() Apresenta sete types no haxe e como eles interagem entre si. The discussion of types is continued in Type System, where features like unification, type parameters and type inference are explained.

[Class Fields]() trata da estrutura das classes no Haxe e, entre outros tópicos, trata de **propriedades**, **campos inline** e **funções genéricas**.

Em [Expressions](), vemos como realmente fazer com que os programas façam algo usando **expressões**.

Language Features conclui a referência da linguagem Haxe descrevendo alguns recursos em detalhes, como **correspondência de padrões**, **interpolação de string** e **eliminação de código morto**.

Nós vamos continuar com a referência do compilador Haxe, que trata do básico no uso do compilador antes de entrar nos recursos avançados do compilador. Finalmente, vamos nos aventurar na emocionante terra do **Haxe macros** no Macros para ver como algumas tarefas comuns podem ser bastante simplificadas.

No capítulo seguinte, _Standard Library_, nós vamos explorar _types_ e conceitos importantes da biblioteca padrão do haxe. Em seguida, aprenderemos sobre o gerenciador de pacotes do Haxe no Haxelib.

Haxe abstracts away many target differences, but sometimes it is important to interact with a target directly, which is the subject of Target Details.

#### 1.2 Sobre esse documento

Este documento é o manual oficial do Haxe 4. Como tal, não é um tutorial para iniciantes e não ensina programação. No entanto, os tópicos são grosseiramente projetados para serem lifos em ordem e há referências a tópicos "vistos anteriormente" e tópicos "ainda por vir". Em alguns casos, uma seção anterior faz uso das informações de uma seção anterior faz uso das informações de uma seção posterior se simplificar a explicação. Essas referências são vinculadas de acordo e geralmente não deve ser um problema ler com antecedência sobre outros tópicos.

Usuamos muito código fonte Haxe para ilustrar assuntos teóricos de forma prática. Esses exemplos de código geralmente são programas completos que vêm com um função principal e podem ser compilados como estão. No entando, às vezes apenas mais relevantes são mostradas. o código-fonte se parece com isso:

```
    Haxe code here
```

Ocasionalmente, demonstramos como o código de destino é gerado, geralemnte mostramos o código em JavaScript.

Além disso, definimos um conjunto de termos neste documento. Predominantemente, isso é feito ao introduzir um novo tipo ou quando é um termo específico para Haxe. Para evitar confusão, não definimos todos os novos aspectos que introduzimos, por exemplo, "o que é uma class". Uma definição se parece com isso:

[Definição: Nome da definição]()

Descrição da definição

Em alguns lugares, este documento tem **caixas de curiosidades**. Isso inclui informações básicas, como por que certas decisões foram tomadas durante o desenvolvimento do Haxe ou como um recurso específico mudou durante o desenvolvimento do Haxe. Essas informações geralmente não são leituras essenciais e podem ser ignoradas, se desejado:

[Curiosidades: Sobre curiosidades]()

Essa é a curiosidade.

###### 1.2.1 Autores e contribuidores

A maior parte do conteúdo do conteúdo deste documento foi escrito por Simon Krajewski enquanto trabalhava para a Fundação Haxe. Gostaríamos de agradecer a essas pessoas por suas contribuições:

- Dan Korostelev: Conteúdo adicional e edição
- Caleb Harper: Conteúdo adicional e edição
- Josefiene Pertosa: Edição
- Miha Lunar: Edição
- Nicolas Cannasse: Criador do Haxe

###### 1.2.2 Licença

O Manual Haxe da [Fundação Haxe](https://haxe.org/foundation/) está sob licença da [Creative Commons Attribuition 4.0 Internation License](https://creativecommons.org/licenses/by/4.0/).

Baseado em um trabalho que está em [github.com/HaxeFoundation/HaxeManual](https://github.com/HaxeFoundation/HaxeManual).

#### 1.3 Hello World

O código a seguir imprime "Hello World" após ser compilado e executado:

```
/**
    Comentários de várias linhas para a documentação.
**/

class Main {
    static public function main():Void {
        // Comentário de uma única linha
        trace("Hello World");
    }
}

```

Isso pode ser testado salvando o código acima em um arquivo chamado `Main.hx` e invocando o compilador Haxe assim: `haxe --main Main --interp`. Ele gera a seguinte saída: `Main.hx:3 Hello world`. Há várias coisas para aprender com isso:

- Os programas Haxe são salvos em arquivos com extensão `.hx`.
- O compilador Haxe é uma ferramenta de linha de comando que pode ser invocada com parâmetros como `main Main` e `--interp`.
- Os programas Haxe têm classes (`Main`, upper-case), que possuem funções (`Main`, lower-case).
- O nome do arquivo que contém uma classe Haxe é o mesmo que o nome da própria classe (nesse caso `Main.hx`).

**Conteúdo Relacionado**

- [Tutoriais para iniciantes e exemplos](https://code.haxe.org/category/beginner/) no Haxe Code Cookbook.

#### 1.4 História

O projeto Haxe foi iniciado em 22 de outubro de 2005 pelo desenvolvedor francês **Nicolas Cannasse** como um sucessor do popular compilador ActionScript 2 de código aberto **MTASC** (Motion-Twin Action Script Compiler) e da linguagem inter **MTypes**, que experimentou a aplicação do tipo inferência para uma linguagem orientada a objetos. A paixão de longa data de Nicolas pelo design de linguagens de programação e o surgimento de novas oportunidades para misturar diferentes tecnologias como parte de seu trabalho de desenvolvedor de jogos na **Motion-Twin** levaram à criação de um linguagem totalmente nova.

Sendo escrito `haXe` naquela época, sua versão beta foi lançada em fevereiro de 2006 com os primeiros alvos suportados sendo AVM-bytecode e a própria máquina virtual `Neko` de Nicolas.

Nicolas Cannasse, que continua líder do projeto Haxe até hoje, continou a desenvolver o Haxe com uma visão clara, levando ao lançamento do Haxe 1.0 em maio de 2006. Este primeiro grande lançamento veio com suporte para geração de código JavaScript e já tinha algumas dos recursos que definem o Haxe hoje, com inferência de tipos e subtipagem estrutural.

O Haxe 1 teve vários lançamentos menores ao longo de dois anos, adicionando o destinho Flash AVM2 junto com a ferramenta **haxelib**-tool em agosto de 2006 e o destino ActionScript 3 em março de 2007. Durante esse período, houve um forte foco na melhoria da estabilidade, o que resultou em vários lançamentos de correção de bugs menores.

O Haxe 2.0 foi lançado em julho de 2008 e incluiu PHP target, cortesia de **Franco Ponticelli**. Um esforço semelhante de **Hugh Sanderson** levou à adição do destino C++ em julho de 2009 com o lançamento do Haxe 2.04.

Assim como no Haxe 1, o que se seguiu foram vários meses de lançamentos de estabilidade. Em janeiro de 2011, o Haxe 2.07 foi lançado com o suporte de **macros**. Naquela época, **Bruno Garcia** se juntou à equipe como mantenedor do JavaScript target, que viu grandes melhorias nas versões 2.08 e 2.09 subsequentes.

Após o lançamento de 2.09, **Simon Krajewski** se juntou à equipe e começou o trabalho para Haxe 3. Além disso, Java e o C# de **Cauê Waneck's** chegaram às compilações do Haxe. Foi então decidido fazer um lançamento final do Haxe 2, que aconteceu em julho de 2012 com o lançamento do Haxe 2.10.

No final de 2012, o Haxe 3 foi invertido e a equipe do Haxe Compiler, agora apoiada pela recém-criada **Haxe Foundation**, concentrou-se nesta próxima versão principal. Haxe 3 foi posteriormente lançado em maio de 2013.

### 2. Types

The Haxe Compiler employs a rich type system which helps detect type-related errors in a program at compile-time. Um erro de tipo é uma operação inválida em um determinado tipo, como dividir por uma String, tentar acessar um campo de Integer ou chamar uma função com poucos (ou muitos) argumentos.

Em algumas linguagens, essa segurança adicional tem um preço porque os programadores são forçados a atribuir tipos explicitamente a construções sintáticas:

```
    var myButton:MySpecialButton = new MySpecialButton(); // As3
```

```
    MySpecialButton* myButton = new MySpecialButton(); // C++ 
```

Anotações de tipo explícito não são necessárias no Haxe porque o compilador pode **inferir** o tipo:

```
    var myButton = new MySpecialButton(); // Haxe
```

Exploraremos a inferência de tipos em detalhes posteriormente em [Inferência de tipos](). Por agora, basta dizer que a variável `myButton` no código acima é conhecida por ser uma **instância da classe** ``MySpecialButton`.

O sistema de tipos Haxe conhece sete grupos de tipos:

- **Instância de classe**: um objeto de uma determinada classe ou interface
- **Enum instance**: um valor de uma enumeração Haxe
- **Structure**: an anonymous structure, i.e. a collection of named fields
- **Função**: um tipo composto de vários argumentos e um retorno
- **Dynamic**: um tipo coringa compatível com qualquer outro tipo
- **Abstract**: um tipo de tempo de compilação que é representado por um tipo diferente em tempo de execução
- **Monomorph**: um tipo desconhecido que mais tarde pode se tornar um tipo diferente

Descreveremos cada um desses grupos de tipos e como eles se relacionam nos capítulos seguintes.

[Definiçaõ: Tipo de Composto]()
*Um tipo composto é um tipo que possui subtipos. Isso inclui qualquer tipo com parâmetros de tipo e o tipo de função*.