# How to create a Nuget Package and Import it locally


### 1. Create the package
Create a new project with the `classlib` template.
```cli
> dotnet new classlib -n MyPackage
```

Add this atributtes to .csproj of the package, inside of `<PropertyGroup>`.
```
<PackageId>MyPackage</PackageId>
<Version>1.0.0</Version>
```

Compile and pack the package.
```cli
> dotnet pack
```

It will create a `.nupkg` in bin/Release.  
Move the `.nupkg` to a another folder, for example `"PackageFolder"`.


### 2. Import into another project
Create a new `console` project.
```cli
dotnet new console -n ImportPackageTest
```

Add the package to the project using source folder (not file path).
```cli
dotnet add package MyPackage --source "../PackageFolder"
```
The source path can be relative or absolute.


## Done

Now you can import the package and use it.
```csharp
using MyPackage;

var package = new MyPackage.MyPackage();
package.Run();
```