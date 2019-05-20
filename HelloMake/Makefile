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
	
