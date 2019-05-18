# Print Versions with Makefile

Content of the Makefile
```
print-versions:
	@echo "/ ###### #"
	@echo "* nodejs : $(shell node -v)"
	@echo "* npm    : $(shell npm -v)"
	@echo "\ ###### #"
```

Use default target
```bash
make
```
or 

```bash
make print-versions
```

will result something similar:
```
"/ ###### #"
"* nodejs : v11.4.0"
"* npm    : 6.9.0"
"\ ###### #"
```
