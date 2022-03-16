## Sumário

### 1. Introdução

#### 1.1 O que é Haxe?

#### Sobre esse documento

#### Hello World

#### História

##### 1.1 O que é Haxe?

###### Consiste em uma linguagem de alto nível, open source e compilada. Ela permite a compilação de programas escritos usando uma sintaxe orientada a ECMAScript, para várias linguagens de destino. Empregando a forma correta, é possível manter uma única base de código que compila para várias plataformas.

###### Haxe tem uma tipagem forte, but the typing system can be subverted where required. Utilizando type information, o Haxe pode detectar erros em tempo de compilação que só seriam perceptíveis em tempo de execução na linguagem de destino. Além disso, as informações do type podem ser usadas pelo compilador para gerar código otimizado e robusto.

###### Atualmente, existem nove linguagems de destino suportados que permitem diferentes casos de uso:

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

###### O restante desta seção fornece uma breve visão geral de como é a linguagem Haxe e como ele evoluiu desde seuinício, em 2005.

###### [Types]() Apresenta sete types no haxe e como eles interagem entre si. The discussion of types is continued in Type System, where features like unification, type parameters and type inference are explained.

##### [Class Fields]() trata da estrutura das classes no Haxe e, entre outros tópicos, trata de **propriedades**, **campos inline** e **funções genéricas**.

###### Em [Expressions](), vemos como realmente fazer com que os programas façam algo usando **expressões**.

###### Language Features conclui a referência da linguagem Haxe descrevendo alguns recursos em detalhes, como **correspondência de padrões**, **interpolação de string** e **eliminação de código morto**.

###### Nós vamos continuar com a referência do compilador Haxe, que trata do básico no uso do compilador antes de entrar nos recursos avançados do compilador. Finalmente, vamos nos aventurar na emocionante terra do **Haxe macros** no Macros para ver como algumas tarefas comuns podem ser bastante simplificadas.

###### No capítulo seguinte, *Standard Library*, nós vamos explorar *types* e conceitos importantes da biblioteca padrão do haxe. Em seguida, aprenderemos sobre o gerenciador de pacotes do Haxe no Haxelib.

###### Haxe abstracts away many target differences, but sometimes it is important to interact with a target directly, which is the subject of Target Details.