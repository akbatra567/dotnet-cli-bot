# Package the tool

1. Open the microsoft.botsay.csproj file and add three new XML nodes to the end of the <PropertyGroup> node:

```xml
<PackAsTool>true</PackAsTool>
<ToolCommandName>botsay</ToolCommandName>
<PackageOutputPath>./nupkg</PackageOutputPath>
```

<ToolCommandName> is an optional element that specifies the command that will invoke the tool after it's installed. If this element isn't provided, the command name for the tool is the project file name without the .csproj extension.

<PackageOutputPath> is an optional element that determines where the NuGet package will be produced. The NuGet package is what the .NET CLI uses to install your tool.

The project file now looks like the following example:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>

    <OutputType>Exe</OutputType>
    <TargetFramework>net6.0</TargetFramework>

    <PackAsTool>true</PackAsTool>
    <ToolCommandName>botsay</ToolCommandName>
    <PackageOutputPath>./nupkg</PackageOutputPath>

  </PropertyGroup>

</Project>
```


2. Create a NuGet package by running the dotnet pack command:

```sh
dotnet pack
```


The microsoft.botsay.1.0.0.nupkg file is created in the folder identified by the <PackageOutputPath> value from the microsoft.botsay.csproj file, which in this example is the ./nupkg folder.

When you want to release a tool publicly, you can upload it to https://www.nuget.org. Once the tool is available on NuGet, developers can install the tool by using the dotnet tool install command. For this tutorial you install the package directly from the local nupkg folder, so there's no need to upload the package to NuGet.