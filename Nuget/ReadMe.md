# NuGet.org Makefile

[NuGet.org](https://nuget.org) is the package manager for .NET. The NuGet client tools provide the ability to produce and consume packages. The NuGet Gallery is the central package repository used by all package authors and consumers.  

The commannd line tool of nuget is [nuget.exe](https://www.nuget.org/downloads).

## Make Commands

Download the latest version of nuget.exe to the current folder
```bash
make nuget-install-latest
```

Download a specific version of nuget.exe to the current folder
```bash
make nuget-install NugetVersion=4.9
```

## Links

- [NuGet](https://www.nuget.org/)
- [NuGet CLI](https://www.nuget.org/downloads)
