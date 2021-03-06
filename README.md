# NuspecFromGithub
Utility to create .nuspec file from github and project assembly

# Usage
```bash
-p, --project... Specify the project path file

-f, --force[optional]... Force recreate file

-g, --github... Specify the username/repository of github
```

# Features

* Create nuspec file automatically
* Access github API to get attributes: id,  title, authors, owners, license, project url, description, commit notes and tags
* Get version file of AssemblyInfo.cs by regex

# How to run

Get binary file on github releases, chocolatey or adding nuget reference and execute:

```bash
NuspecFromGithub.exe -p ..\..\ --force -g jefersonsv/NuspecFromGithub
```

NuspecFromGithub

## From github releases
Get the realease on: https://github.com/jefersonsv/NuspecFromGithub/releases/tag/1.0.0

## From chocolatey
```bash
choco install NuspecFromGithub
```

## Adding nuget reference
```bash
PM> Install-Package NuspecFromGithub
```

# Result

This command will generate the **NuspecFromGithub.nuspec** in same folder of .csproj file with content

```xml
<?xml version="1.0" encoding="utf-8"?>
<package>
  <metadata>
    <id>NuspecFromGithub</id>
    <version>1.0.0.0</version>
    <title>Utility to create .nuspec file from github and project assembly</title>
    <authors>Jeferson Tenorio</authors>
    <owners>Jeferson Tenorio</owners>
    <licenseUrl>http://choosealicense.com/licenses/mit/</licenseUrl>
    <projectUrl>https://github.com/jefersonsv/NuspecFromGithub</projectUrl>
    <iconUrl></iconUrl>
    <requireLicenseAcceptance>false</requireLicenseAcceptance>
    <description>Utility to create .nuspec file from github and project assembly</description>
    <releaseNotes>implementation</releaseNotes>
    <copyright>Copyright 2017</copyright>
    <tags></tags>
  </metadata>
</package>
```

After file created, on same folder of .csproj file run below command to create .nupkg:
* For NuGet Version: 4.3.0.4406

Set your nuget ApiKey before below steps running the command (it's necessary only first time):
```bash
nuget.exe setApiKey <api-key>
```

To put your package to Nuget execute:

```bash
nuget pack NuspecFromGithub.nuspec -IncludeReferencedProjects
nuget push <nupgk-generated-file>.nupkg -Source https://www.nuget.org/api/v2/package
```



The command setApi it's option if the key has been configureted previous

# Tips
* https://docs.microsoft.com/en-us/nuget/create-packages/creating-a-package
* https://blog.codeinside.eu/2017/02/13/create-nuget-packages-with-cake/
* https://docs.microsoft.com/en-us/nuget/tools/nuget-exe-cli-reference

# Thanks

* https://github.com/j-maly/CommandLineParser
