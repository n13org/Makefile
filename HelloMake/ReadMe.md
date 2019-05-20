# Hello Makefile

## Table of Content
[Simple print a text](#simple-print-a-text)  
[Combine two targets in the default target](#combine-two-targets-in-the-default-target)  
[Use of variables](#use-of-variables)  

## Makefile tips and tricks - description
The default target ```my-default-targets``` shows a hello-message.

When a line in the makefile target is prefixed with ```@``` the command itself will not be echoed.

Long command can be wrapped with ``` \ ```. That mean a command 
```
my-default-targets: hello goodbye
```
Can be also written as
```
my-default-targets: hello \
                    goodbye
```

## Simple print a text
Content of the Makefile
```
my-default-targets: hello

hello-with-echo: 
	echo "Hello, to the world of make (should be seen twice)"

hello: 
	@echo "Hello, to the world of make (should be seen once)"
```

Use default target
```bash
$ make
Hello, to the world of make (should be seen once)
```

Use target hello with @-prefix
```bash
$ make hello
Hello, to the world of make (should be seen once)
```

Use target hello without @-prefix

```bash
$ make hello-with-echo
echo "Hello, to the world of make (should be seen twice)
"Hello, to the world of make (should be seen twice)
```

## Combine two targets in the default target
Content of the Makefile
```
my-default-targets: hello \
                    goodbye

hello-with-echo: 
	echo "Hello, to the world of make (should be seen twice)"

hello: 
	@echo "Hello, to the world of make (should be seen once)"
	
.PHONY: goodbye
goodbye: 
	@echo "Bye bye, see you next time!"	
```

Use default target
```bash
$ make
Hello, to the world of make (should be seen once)
Bye bye, see you next time!
```

## Use of variables
Global variables can be used outside targets. Just use the notation ```name=value```. Text with sapces have to be quated.

Content of the Makefile
```
VARIABLE_AS_TEXT="Content of variable"
BUILD_DATE=$(shell date +%Y%m%d-%H:%M:%S)
PWD=$(shell ../_scripts/bash/get-pwd.sh)

my-default-targets: hello \
                    goodbye

hello-with-echo: 
	echo "Hello, to the world of make (should be seen twice)"

hello: 
	@echo "Hello, to the world of make (should be seen once)"
	
hello-variable: 
	@echo "/ ######################### #"
	@echo "* Variable as text          : $(VARIABLE_AS_TEXT)"
	@echo "* Variable as shell command : $(BUILD_DATE)"
	@echo "* Variable as shell script  : $(PWD)"
	@echo "\ ######################### #"
	
.PHONY: goodbye
goodbye: 
	@echo "Bye bye, see you next time!"
```	

Use 'make hello-variable'
```bash
/ ######################### #
* Variable as text          : Content of variable
* Variable as shell command : 20190520-06:40:19
* Variable as shell script  : /d/n13.org/Makefile/HelloMake
\ ######################### #
```