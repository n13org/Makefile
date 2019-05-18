# Hello Makefile

The default target ```my-default-targets``` shows a hello-message.

When a line in the makefile target is prefixed with ```@``` the command itself will not be echoed.

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