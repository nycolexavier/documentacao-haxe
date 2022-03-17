## Sumário

### 1. Introdução

#### 1.1 O que é Haxe?

#### 1.2 Sobre esse documento

##### 1.2.1 Autores e contribuidores

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
