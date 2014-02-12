Nuget
------

###Nuget basic configuration
The configuration from nuget is in nuget.config

###Add grep and Nuget to your Path

$env:Path = "c:\cygwin64\bin\;C:\Nuget;" + $env:Path

Get the list of project names
-----------------------------

> grep -i -r -l --include=*.csproj <NugetPackage> | % { ([xml](Get-Content $_)).Project.PropertyGroup[0].AssemblyName } | % { Install-Package <NugetPackage> -Project $_ }


###The same just in Powershell
> dir -recurse -include *.csproj | Select-String -SimpleMatch "FluentValidation" | group path | % { ([xml](Get-Content $_.Name)).Project.PropertyGroup[0].AssemblyName } | % { Install-Package jQuery -Project $_ }

###Creating a new nugep package

In the directory of the library:

> nuget spec

Edit the spec file, add the line:

 <files>
     <file src="*.dll" target="lib"/>
 </files>

Execute the command:

> nuget pack .\Package.nuspec


###Publish the package
API Key: <Your key>

> nuget push .\unhaddins.3.0.0.773.nupkg -s http://<YourRepository>/ <YourKey>

###Delete a package from repository
> nuget delete unhaddins 3.0.0.773 -Source http://<YourRepository>/ -ApiKey <YourKey>

###Additional nuget commands
Show the list of sources in nuget:
nuget sources

Show the packages available in a repository:
> nuget list -s <Repository>

Reinstall packages in a project (useful when changing the version of .net in a
project):

> Update-Package -Project <YourProject> -Reinstall
