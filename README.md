---
layout: post
title:  "Code Markdown to Bash"
---

# Introduction

A very, very simple transpiler from code-markdown to swipl (PROLOG).

Transpile
```
# _containment_

## _fb pipeline_
	allContains1
	printAllDeepContains
	printAllDirectContains



## _details_
### allContains1
	load fb
	load onSameDiagram
	load contain1
### printAllDeepContains
	load fb
	load onSameDiagram
	load contains2
### printAllDirectContains
	load fb
	load onSameDiagram
	load contains3
```
to
```
#!/bin/bash
# _containment_

clear
set -e
trap 'catch' ERR

catch () {
    echo '*** FATAL ERROR ***'
    exit 1
}

# _details_
allContains1 () {
	load fb
	load onSameDiagram
	load contain1

}
printAllDeepContains () {
	load fb
	load onSameDiagram
	load contains2

}
printAllDirectContains () {
	load fb
	load onSameDiagram
	load contains3

}

# _fb pipeline_
	allContains1
	printAllDeepContains
	printAllDirectContains
```

Note that the above input syntax is editable by emacs md-mode.

Emacs md-mode provides the `TAB` key to allow eliding layers.

## Preamble
The preamble traps errors and prints a FATAL
```

clear
set -e
trap 'catch' ERR

catch () {
    echo '*** FATAL ERROR ***'
    exit 1
}
``
Any sub-script that exits with a non-0 exit code, will be caught by the above.

# See also
[Code Markdown to Structured Pseudo-code](https://guitarvydas.github.io/2021/08/03/Code-Markdown-to-Structured-Pseudo-code.html)

[Glue Tool](https://guitarvydas.github.io/2021/04/11/Glue-Tool.html)
[Glue Manual](https://guitarvydas.github.io/2021/03/24/Glue-Manual.html)
[Blog](https://guitarvydas.github.io)
[References](https://guitarvydas.github.io/2021/01/14/References.html)

<script src="https://utteranc.es/client.js" 
        repo="guitarvydas/guitarvydas.github.io" 
        issue-term="pathname" 
        theme="github-light" 
        crossorigin="anonymous" 
        async> 
</script> 
