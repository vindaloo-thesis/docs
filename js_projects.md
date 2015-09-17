Haskell to JavaScript projects
======================================
Here, we present the state of the field when it comes to turning Haskell into JavaScript - a short summary of notable projects and their approaches. JavaScript is the one high-level language of major interest today and looking at how making Haskell code run inside a web browser provides insight in how it can be porte dto the EVM.

JMacro
------
**Approach:** EDSL

Haste
-----
**Approach:** Cross-compilation via STG using GHC
**Steps:** Haskell -[GHC]-> STG -[Haste]-> AST -[Haste.link]-> AST -[Haste.prettyprint]-> JavaScript code]

GHCJS
-----
**Approach:** Cross-compilation via STG using GHC. 
**Steps:** Haskell -[GHC]-> STG -[GHCJS]-> JS

Goes directly to JS code from STG without intermediate symbolic representation. Build pocess and workflow not really documented. Code footprint big (100s of kb for trivial example).

UHC backend
-----------
**Approach:** Cross-compilation via UHC core through a UHC backend
**Steps:** Haskell -[UHC]-> Essential Haskell -[UHC]-> UHC Core -[JS backend]-> JavaScript

Code footprint huge (couple of MB for trivial program). Slow.

Fay
---
**Approach:** Subset of Haskell that compiles to JavaScript.
**Steps:** Fay -[GHC.Typechecking]-> Fay -[haskell-src-exts.Parsing/Lexing]-> Annotated Haskell AST -[Desugaring]-> AST -[haskell-names.Annotate] -> Further annotated AST -[Code generation]-> JavaScript AST -[Printing]-> JavaScript code
