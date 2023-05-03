Programs are files that contain a bunch of text written by you, the programmer. That text is parsed by a special program called a _compiler_, which transforms it into an _abstract syntax tree (AST)_, a data structure that ignores things like whitespace, comments. The compiler then converts that AST to a lower-level representation called _bytecode_. You can feed that bytecode into another program called a _runtime_ to evaluate it and get a result.
*In short, the steps are:*
1. Program is parsed into an AST.
2. AST is compiled to bytecode.
3. Bytecode is evaluated by the runtime.

## The process of compiling TypeScript
![[Pasted image 20230503165015.png]]
Steps 1–3 are done by *TSC*, and steps 4–6 are done by the *JavaScript runtime* that lives in your browser, NodeJS, or whatever JavaScript engine you’re using.
*JavaScript compilers and runtimes* tend to be smushed into a single program called an _engine_; as a programmer, this is what you’ll normally interact with. It’s how V8 (the engine powering NodeJS, Chrome, and Opera), SpiderMonkey (Firefox), JSCore (Safari), and Chakra (Edge) work, and it’s what gives JavaScript the appearance of being an _interpreted_ language.

## Type System
A *set of rules* that a typechecker uses to assign types to your program.

There are generally *two kinds of type systems*: type systems in which you have to tell the compiler what type everything is with explicit syntax, and type systems that infer the types of things for you automatically.

![[Screenshot 2023-05-03 at 5.05.06 PM.png]]
*Dynamic type binding* means that JavaScript needs to actually run your program to know the types of things in it.

## tsconfig vs eslintrc
The `tsconfig.json` file is used by the TypeScript compiler to generate JavaScript code, while the ESLint configuration file is used by the ESLint tool to analyze and improve the quality of the JavaScript or TypeScript code.