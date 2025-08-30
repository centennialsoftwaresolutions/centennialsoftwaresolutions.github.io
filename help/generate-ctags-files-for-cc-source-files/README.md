# Generate Ctags Files for C/C++ Source Files

![believe_poster](believe_poster.png)

**Post Description**

This post gives a summary of what each Exuberant Ctags flag means when generating more source code browsing info.

**Generate Tags**

```
ctags -R .
```

\-R says to look in all subdirectories.

The . matches all files.

**Generate Tags with Expanded Info**

```
ctags -R --c++-kinds=+p --fields=+iaS --extra=+q .
```

This adds **function prototypes** (**+p**) which are normally off. It also includes **inheritance information** (i), **access (or export) of class members** (**a**) and **signatures of routine (e.g. prototype or parameter list)** (**S**) in the tags info field (so you can read it). Finally it ensures classes are qualified: **class::member (+q)**.

**Short Flags Explanation**

```
$ ctags --help | grep kinds -A1
  --<LANG>-kinds=[+|-]kinds
       Enable/disable tag kinds for language <LANG>.
```

```
$ ctags --help | grep fields
  --fields=[+|-]flags
      Include selected extension fields (flags: "afmikKlnsStz") [fks].
```

```
$ ctags --help | grep extra
  --extra=[+|-]flags
      Include extra tag entries for selected information (flags: "fq").
```

**Expanded Flags Explanation**

−−<LANG>−kinds=\[+|−\]kinds

Specifies a list of language-specific kinds of tags (or kinds) to include in the output file for a particular language, where <LANG> is case-insensitive and is one of the built-in language names (see the −−list−languages option for a complete list). The parameter kinds is a group of one-letter flags designating kinds of tags (particular to the language) to either include or exclude from the output. The specific sets of flags recognized for each language, their meanings and defaults may be list using the −−list−kinds option. Each letter or group of letters may be preceded by either ’+’ to add it to, or ’−’ to remove it from, the default set. In the absence of any preceding ’+’ or ’−’ sign, only those kinds explicitly listed in kinds will be included in the output (i.e. overriding the default for the specified language).

As an example for the C language, in order to add prototypes and external variable declarations to the default set of tag kinds, but exclude macros, use −−c−kinds=+px−d; to include only tags for functions, use −−c−kinds=f.

Output of 'ctags --list-languages':

```
$ ctags --list-languages
Ant
Asm
Asp
Awk
Basic
BETA
C
C++
C#
Cobol
DosBatch
Eiffel
Erlang
Flex
Fortran
HTML
Java
JavaScript
Lisp
Lua
Make
MatLab
OCaml
Pascal
Perl
PHP
Python
REXX
Ruby
Scheme
Sh
SLang
SML
SQL
Tcl
Tex
Vera
Verilog
VHDL
Vim
YACC
```

```
$ ctags --list-kinds
Ant
    p  projects
    t  targets
Asm
    d  defines
    l  labels
    m  macros
    t  types (structs and records)
Asp
    d  constants
    c  classes
    f  functions
    s  subroutines
    v  variables
Awk
    f  functions
Basic
    c  constants
    f  functions
    l  labels
    t  types
    v  variables
    g  enumerations
BETA
    f  fragment definitions
    p  all patterns [off]
    s  slots (fragment uses)
    v  patterns (virtual or rebound)
C
    c  classes
    d  macro definitions
    e  enumerators (values inside an enumeration)
    f  function definitions
    g  enumeration names
    l  local variables [off]
    m  class, struct, and union members
    n  namespaces
    p  function prototypes [off]
    s  structure names
    t  typedefs
    u  union names
    v  variable definitions
    x  external and forward variable declarations [off]
C++
    c  classes
    d  macro definitions
    e  enumerators (values inside an enumeration)
    f  function definitions
    g  enumeration names
    l  local variables [off]
    m  class, struct, and union members
    n  namespaces
    p  function prototypes [off]
    s  structure names
    t  typedefs
    u  union names
    v  variable definitions
    x  external and forward variable declarations [off]
C#
    c  classes
    d  macro definitions
    e  enumerators (values inside an enumeration)
    E  events
    f  fields
    g  enumeration names
    i  interfaces
    l  local variables [off]
    m  methods
    n  namespaces
    p  properties
    s  structure names
    t  typedefs
Cobol
    d  data items
    f  file descriptions (FD, SD, RD)
    g  group items
    p  paragraphs
    P  program ids
    s  sections
DosBatch
    l  labels
    v  variables
Eiffel
    c  classes
    f  features
    l  local entities [off]
Erlang
    d  macro definitions
    f  functions
    m  modules
    r  record definitions
Flex
    f  functions
    c  classes
    m  methods
    p  properties
    v  global variables
    x  mxtags
Fortran
    b  block data
    c  common blocks
    e  entry points
    f  functions
    i  interface contents, generic names, and operators [off]
    k  type and structure components
    l  labels
    L  local, common block, and namelist variables [off]
    m  modules
    n  namelists
    p  programs
    s  subroutines
    t  derived types and structures
    v  program (global) and module variables
HTML
    a  named anchors
    f  JavaScript functions
Java
    c  classes
    e  enum constants
    f  fields
    g  enum types
    i  interfaces
    l  local variables [off]
    m  methods
    p  packages
JavaScript
    f  functions
    c  classes
    m  methods
    p  properties
    v  global variables
Lisp
    f  functions
Lua
    f  functions
Make
    m  macros
MatLab
    f  function
    f  function
    f  function
OCaml
    c  classes
    m  Object's method
    M  Module or functor
    v  Global variable
    t  Type name
    f  A function
    C  A constructor
    r  A 'structure' field
    e  An exception
Pascal
    f  functions
    p  procedures
Perl
    c  constants
    f  formats
    l  labels
    p  packages
    s  subroutines
    d  subroutine declarations [off]
PHP
    c  classes
    i  interfaces
    d  constant definitions
    f  functions
    v  variables
    v  variables
    j  javascript functions
    j  javascript functions
    j  javascript functions
Python
    c  classes
    f  functions
    m  class members
    v  variables
    i  imports
REXX
    s  subroutines
Ruby
    c  classes
    f  methods
    m  modules
    F  singleton methods
Scheme
    f  functions
    s  sets
Sh
    f  functions
SLang
    f  functions
    n  namespaces
SML
    e  exception declarations
    f  function definitions
    c  functor definitions
    s  signature declarations
    r  structure declarations
    t  type definitions
    v  value bindings
SQL
    c  cursors
    d  prototypes [off]
    f  functions
    F  record fields
    l  local variables [off]
    L  block label
    P  packages
    p  procedures
    r  records [off]
    s  subtypes
    t  tables
    T  triggers
    v  variables
    i  indexes
    e  events
    U  publications
    R  services
    D  domains
    V  views
    n  synonyms
    x  MobiLink Table Scripts
    y  MobiLink Conn Scripts
Tcl
    c  classes
    m  methods
    p  procedures
Tex
    c  chapters
    s  sections
    u  subsections
    b  subsubsections
    p  parts
    P  paragraphs
    G  subparagraphs
Vera
    c  classes
    d  macro definitions
    e  enumerators (values inside an enumeration)
    f  function definitions
    g  enumeration names
    l  local variables [off]
    m  class, struct, and union members
    p  programs
    P  function prototypes [off]
    t  tasks
    T  typedefs
    v  variable definitions
    x  external variable declarations [off]
Verilog
    c  constants (define, parameter, specparam)
    e  events
    f  functions
    m  modules
    n  net data types
    p  ports
    r  register data types
    t  tasks
VHDL
    c  constant declarations
    t  type definitions
    T  subtype definitions
    r  record names
    e  entity declarations
    C  component declarations [off]
    d  prototypes [off]
    f  function prototypes and declarations
    p  procedure prototypes and declarations
    P  package definitions
    l  local definitions [off]
Vim
    a  autocommand groups
    c  user-defined commands
    f  function definitions
    m  maps
    v  variable definitions
YACC
    l  labels
```

−−fields=\[+|−\]flags

Specifies the available extension fields which are to be included in the entries of the tag file (see TAG FILE FORMAT, below, for more information). The parameter flags is a set of one-letter flags, each representing one type of extension field to include, with the following meanings (disabled by default unless indicated):

a - Access (or export) of class members

f - File-restricted scoping \[enabled\]

i - Inheritance information

k - Kind of tag as a single letter \[enabled\]

K - Kind of tag as full name

l - Language of source file containing tag

m - Implementation information

n - Line number of tag definition

s - Scope of tag definition \[enabled\]

S - Signature of routine (e.g. prototype or parameter list)

z - Include the "kind:" key in kind field

t - Type and name of a variable or typedef as "typeref:" field \[enabled\]

Each letter or group of letters may be preceded by either ’+’ to add it to the default set, or ’−’ to exclude it. In the absence of any preceding ’+’ or ’−’ sign, only those kinds explicitly listed in flags will be included in the output (i.e. overriding the default set). This option is ignored if the option −−format=1 has been specified. The default value of this option is fkst.

−−extra=\[+|−\]flags

Specifies whether to include extra tag entries for certain kinds of information. The parameter flags is a set of one-letter flags, each representing one kind of extra tag entry to include in the tag file. If flags is preceded by by either the ’+’ or ’−’ character, the effect of each flag is added to, or removed from, those currently enabled; otherwise the flags replace any current settings. The meaning of each flag is as follows:

f - Include an entry for the base file name of every source file (e.g. "example.c"), which addresses the first line of the file.

q - Include an extra class-qualified tag entry for each tag which is a member of a class (for languages for which this information is extracted; currently C++, Eiffel, and Java). The actual form of the qualified tag depends upon the language from which the tag was derived (using a form that is most natural for how qualified calls are specified in the language). For C++, it is in the form "class::member"; for Eiffel and Java, it is in the form "class.member". This may allow easier location of a specific tags when multiple occurrences of a tag name occur in the tag file. Note, however, that this could potentially more than double the size of the tag file.

**Version Detail**

```
$ ctags --version
Exuberant Ctags 5.8, Copyright (C) 1996-2009 Darren Hiebert
  Compiled: Jul  9 2009, 17:05:35
  Addresses: , http://ctags.sourceforge.net
  Optional compiled features: +win32, +regex, +internal-sort
```

**References**

-   Find how to generate ctags with more symbols [by Hong (@xuhdev)](http://www.topbug.net/blog/2012/03/17/generate-ctags-files-for-c-slash-c-plus-plus-source-files-and-all-of-their-included-header-files/)
    
-   Escape <> in pre tags @ [link](http://www.freeformatter.com/html-escape.html#ad-output).
    
-   Documentation for Exhuberate Tags @ [link](http://ctags.sourceforge.net/ctags.html).
    
-   Cat poster from Amazon.com. Click [here](http://www.amazon.com/Kitten-Hang-There-Poster-34in/dp/B0154G6DFU) to buy.