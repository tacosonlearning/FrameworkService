# .NET Framework 4.8 Windows Service

This repository demonstrates the following topics:

- Creating a Windows Service using .NET Framework 4.8
- Using the SDK style project format
- Enabling hosting through the Microsoft.Extensions.Hosting framework
- Enabling dependency injection through the Microsoft.Extensions.DependencyInjection framework
- Enabling logging through the Microsoft.Extensions.Logging framework
- Deploying the service as a Docker container

## Prerequisites

- .NET Framework 4.8
- Visual Studio 2022
- Docker Desktop

Optionally, you can use VS Code, though creating the initial scaffolding for the service is not covered in this repository and while it can be done by hand, it's not recommended.

## Creating the service

The initial project is created using Visual Studio 2022. The following steps are performed:

- Create a new project
- Select the "Windows Service (.NET Framework)" template

## Converting the project to the SDK style

Locate and open the `.csproj` file and remove everything. Replace it with the following:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net48</TargetFramework>
    <OutputType>WinExe</OutputType>
  </PropertyGroup>
</Project>
```

Next, you'll need to remove the `Properties.AssemblyInfo` that the project template created. This is done by deleting the `AssemblyInfo.cs` file, though deleting the entire `Properties` folder is recommended.

Finally, Windows Service projects require a reference to the `System.ServiceProcess` assembly. Add the following to the `.csproj` file:

```xml
<ItemGroup Label="RequiredReferences">
  <Reference Include="System.ServiceProcess" />
</ItemGroup>
```

The above snippet creates a new item group named `RequiredReferences`. While the label isn't required, it is recommended for organization purposes.

**Note**: *The `App.config` file isn't required, so it may safely be deleted.*
