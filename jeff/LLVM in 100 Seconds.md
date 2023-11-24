LLVM, a toolkit used to build and optimize compilers, makes building a programming language from scratch challenging. Humans desire to write code in a nice, simple syntax, while machines need to run it on various architectures.

LLVM standardizes the complex process of turning source code into machine code. Created in 2003 by grad student Chris Lattner at the University of Illinois, LLVM is the magic behind Clang for C and C++, as well as languages like Rust, Swift, Julia, and many others.

Most importantly, it represents high-level source code in a language-agnostic code called Intermediate Representation (IR). This means vastly different languages like CUDA and Ruby produce the same IR, allowing them to share tools for analysis and optimization before conversion to machine code for a specific chip architecture.

A compiler can be broken down into three parts. The front end parses the source code text and converts it into IR. The middle end analyzes and optimizes this generated code, and finally, the back end converts the IR into native machine code.

To build your programming language, install LLVM, then create a C file. Envision the programming language syntax of your dreams to make that high-level code work. You'll first need to write a lexer to scan the raw source code and break it into a collection of tokens like literals, identifiers, keywords, operators, and so on.

Next, define an abstract syntax tree to represent the actual structure of the code and how different tokens relate to each other. This is accomplished by giving each node its own class. Third, you need a parser to loop over each token and build out the abstract syntax tree. If you made it this far, congratulations because the hard part is over.

Now, import a bunch of LLVM primitives to generate the intermediate representation. Each type in the abstract syntax tree is given a method called 'cogen,' which always returns an LLVM value object used to represent a single assignment register (a variable for the compiler that can only be assigned once).

What's interesting about these IR primitives is that, unlike assembly, they're independent of any particular machine architecture. That dramatically simplifies things for language developers, who no longer need to match the output to a processor's instruction set.

Now that the front end can generate IR, the 'opt' tool is used to analyze and optimize the generated code. It makes multiple passes over the IR and does things like dead code elimination and scalar replacement of aggregates.

Finally, that brings us to the back end, where we write a module that takes IR as an input and emits object code that can run on any architecture. Congratulations! You've just built your own custom programming language and compiler in 100 seconds. Hit the like button and subscribe if you want to see more short videos like this. Thanks for watching, and I will see you in the next one.
