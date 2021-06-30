# Preprocessor

## Overview

* a unique feature of C that isn't found on many other higher-level languages
* allows to develop a program easier, read and modify it easier, and port it to different comp. systems easily
* part of the compilation process that recognizes special statements
  * analyzes the statements before analyzing the program itself
  * an instruction to the compiler to do something before compiling source code
  * could be anywhere in the code, but usually at the top
* identified by a pound sign `#`, which must be the first non-space char of the line
* We can utilize this to
  * create constants and macros with `#define`
  * build library files with `#include`
  * make powerful programs with conditionals `#ifdef #endif #else #ifndef`
  * etc...
