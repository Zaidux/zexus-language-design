# Zexus v1.0 Implementation Plan

This document outlines the plan and roadmap for building the first working interpreter for the Zexus language.

## 1. Host Language
The initial Proof-of-Concept (PoC) interpreter will be written in **Python 3**. This language is chosen for its simplicity and rapid development capabilities.

## 2. Interpreter Architecture
The interpreter will be built with three core components:
1.  **Lexer:** Scans the source code of a `.zx` file and converts it into a stream of tokens.
2.  **Parser:** Takes the tokens and builds a structured representation of the code (an Abstract Syntax Tree) that confirms the code follows Zexus's grammar rules.
3.  **Evaluator:** Traverses the tree created by the parser and executes the code's logic.

## 3. Proof-of-Concept (PoC) Scope
The first working version of the interpreter will only support a minimal set of features to prove the concept is viable.

**PoC Scope:**
* Variable declarations using `let`.
* Basic arithmetic expressions (`+`, `-`, `*`, `/`).
* The `print` command.
* Single-line comments using `#`.

## 4. Initial Project Roadmap

* **Milestone 1:** Implement the Lexer, Parser, and Evaluator to fully support the PoC scope.
* **Milestone 2:** Add support for `if/else` conditional statements.
* **Milestone 3:** Add support for boolean logic (`true`, `false`, `==`, `!=`, `>`, `<`).
* **Milestone 4:** Implement the `List` data structure and `for each` loops.
* **Milestone 5:** Begin implementation of `action` definitions and calls.
