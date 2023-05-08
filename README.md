Download Link: https://assignmentchef.com/product/solved-uu-com-4003-compiler-design-assignment-1
<br>
You should extend MiniJava’s syntax to allow the following (all of which are legal in full Java too):

<ul>

 <li>double is a legal (base) type.</li>

 <li>A floating-point literal constant is a legal expression.</li>

 <li>An array of a base type, e.g., int[], boolean[][][], and in general <em>type</em>[] where <em>type</em> is an arbitrary base type. (Base types are ints, booleans, doubles, and arrays of base types. Only class types are not base types; this restriction is included only because otherwise the language becomes too hard to parse! The AST and the rest of the compiler should not depend on this restriction against arrays of class types, however.)</li>

 <li>A one-level array allocation expression, e.g., new int[10], new boolean[20][][], and in general new <em>type</em>[<em>expr</em>]<em>dims</em> where <em>type</em> is an arbitrary non-array base type, <em>expr </em>is an arbitrary expression, and <em>dims</em> is a possibly-empty sequence of []’s, is a legal expression.</li>

 <li>An array dereference, e.g., <em>a</em>[<em>i</em>], <em>b</em>[<em>i</em>][<em>j</em>][<em>k</em>], and in general <em>expr1</em>[<em>expr2</em>] where <em>expr1</em> is an arbitrary atomic expression and <em>expr2 </em>is an arbitrary expression, is a legal expression. An array dereference is also legal on the left-hand side of an assignment statement. (Atomic expressions exclude unary and binary operator expressions and array allocation expressions.)</li>

 <li>An array length expression, e.g., <em>a</em>.length and in general <em>expr</em>.length where <em>expr</em> is an arbitrary atomic expression, is a legal expression. length is a reserved word in MiniJava (unlike Java).</li>

 <li>An or expression (using the || infix operator) is a legal expression.</li>

 <li>if statements do not require else clauses.</li>

 <li>For loops of the restricted form for (<em>i</em> = <em>expr1</em>; <em>expr2</em>; <em>i</em> = <em>expr3</em>) <em>stmt</em> are allowed, where <em>expr1</em>, <em>expr2</em>, and <em>expr3 </em>are arbitrary expressions, <em>i</em> is an arbitrary variable, and <em>stmt</em> is an arbitrary statement.</li>

 <li>break statements are allowed. (You do not need to check in the syntax that break statements only appear inside of loops; semantic checking will enforce this.)</li>

 <li>A class variable declaration may be preceded by the static reserved word to declare a static class variable.</li>

</ul>

You should follow the precedence and associativity rules of regular Java for these extensions.  It’s OK to use CUP’s predecence declarations to achieve this.

It’s OK to have one shift/reduce conflict in your CUP grammar, for the “dangling else” problem.  Add the “-expect 1” option before the minijava.cup argument in the Makefile to build Parser/parser.java if you decide to accept this shift/reduce conflict.  (FYI, in making the sample solution, it was not possible to find a way to revise the CUP grammar specification to avoid this conflict.)

You should add new AST classes and/or modify existing AST classes so that you can represent the new MiniJava constructs.  You should define the appropriate toString operations on these classes so that they can be pretty-printed in a form that is syntactically legal and produces the same AST if it is parsed in again. (<strong>Note:</strong> Pay attention to this requirement, as it will be used during grading to check the correctness of your parse.)  The other operations required of AST nodes, e.g. typechecking, evaluating, and lowering, you should implement by throwing UnimplementedError exceptions.

You only need to get the parser to work (and keep the extended scanner working). <strong>You do not need to do anything to enforce typechecking rules or other semanticanalysis constraints on the input program.</strong>

Do the following:

<ol>

 <li>Extend the specification of MiniJava’s syntactic structure to describe the extended language, in the same style. (You can assume precedence and associativity is specified separately, and it is OK to define a grammar that is ambiguous with respect to the “dangling else” problem.)</li>

 <li>Add and/or modify classes in the AST subdirectory to represent the extended language.</li>

 <li>Extend Parser/minijava.cup to parse the extended language and construct the abstract syntax tree representing the parsed program.</li>

 <li>Develop test cases that demonstrate that your extended parser and AST classes work, both in cases that should now be syntactically legal and in cases that should still be syntactically illegal. (Since the parser quits at the first error, you’ll likely need several illegal test case files to test the different illegal cases.) You do not need to check for lexical errors, just syntactic errors. The SamplePrograms directory contains some files that should parse after you make your changes; some of the files should parse successfully with the initial version of the MiniJava compiler.</li>

</ol>

You can put them in a zip file or in folder, choose the more convenient for you.

You can use the -parse -printAST options to the MiniJava compiler to just run the parsing phase and print out the AST that it builds.  See the test_parser target in the Makefile for an example, and feel free to make your own target(s) to make running the tests you like easier and more mechanical.


