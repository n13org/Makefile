# Hello Makefile

The default target ```my-default-targets``` shows a hello-message.

When a line in the makefile target is prefixed with ```@``` the command itself will not be echoed.

## Simple print a text
```bash
$ make hello
Hello, to the world of make (should be seen once)
```

```bash
$ make hello-with-echo
echo "Hello, to the world of make (should be seen twice)
"Hello, to the world of make (should be seen twice)
```