# Hello Makefile

## Table of Content
[Simple print a text](#simple-print-a-text)  
[Combine two targets in the default target](#combine-two-targets-in-the-default-target)  
[Use of variables](#use-of-variables)  
[User a variable for the target only](#user-a-variable-for-the-target-only)  

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
$ make hello-variable
/ ######################### #
* Variable as text          : Content of variable
* Variable as shell command : 20190520-06:40:19
* Variable as shell script  : /d/n13.org/Makefile/HelloMake
\ ######################### #
```

## Use a variable for the target only
Use a variable just for a target. The target has to be mentioned twice in the Makefile. The first time we define the target variable, the second time we will use the target variable.

Content of the Makefile
```
hello-variable-target-only: MYTARGETVAR="Content of target variable"
hello-variable-target-only:
	@echo "/ #################### #"
	@echo "* Variable from target : $(MYTARGETVAR)"
	@echo "\ #################### #"
```

Use 'make hello-variable-target-only'
```bash
$ make hello-variable-target-only
/ #################### #
* Variable from target : Content of target variable
\ #################### #
```

## Use a variable from environment
Make can access even environment variable, here in the example we use the ```%JAVA_HOME%``` from Windows.

Content of the Makefile
```
hello-env-variable:
	@echo "/ ######################### #"
	@echo "* Variable from environment : $(JAVA_HOME)"
	@echo "\ ######################### #"
```

Use 'make hello-env-variable'
```bash
$ make hello-env-variable
/ ######################### #
* Variable from environment : C:\Program Files\Java\jdk1.8.0_202
\ ######################### #
```

Use 'make hello-env-variable' with -e, to overwrite the env-variabe
```bash
$ make hello-env-variable -e JAVA_HOME=foo
/ ######################### #
* Variable from environment : foo
\ ######################### #
```

Use 'make hello-env-variable' without -e, to overwrite the env-variabe. Sometimes I got here a warning.
```bash
$ make hello-env-variable JAVA_HOME=foo
/ ######################### #
* Variable from environment : foo
\ ######################### #
```

