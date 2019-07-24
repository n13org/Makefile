NugetVersion="5.1.0"

my-default-targets: nuget-version

nuget-version:
	@echo "/ ###### #"
	@echo "* nuget  : $(shell nuget help | head -1)"
	#@echo "* nuget  : $(shell nuget help | select -First 1)"	# PowerShell, Windows
	@echo "\ ###### #"

nuget-install-latest:
	curl --output nuget.exe https://dist.nuget.org/win-x86-commandline/latest/nuget.exe

nuget-install:
	curl --output nuget.exe https://dist.nuget.org/win-x86-commandline/$(NugetVersion)/nuget.exe