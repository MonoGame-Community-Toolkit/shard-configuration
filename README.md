# Shared Configuration
This repository contains shared configuration used for all of the MonoGame Community Toolkit repositories.

# Installation
This is designed to be installed as a git submodule at the root of any MonoGame Community Toolkit repository.  The MonoGame Community Toolkit repository needs to be setup so that it conforms to the following project structure

```sh
├── .gitignore
├── LICENSE
├── Solution.sln
├── README.md
└── source
    └── Project
        └── Project.csproj
```

Once the project is setup, add the shared configuration as a git submodule in the root directory of the MonoGame Community Toolkit repository.

```sh
git submodule add https://github.com/MonoGame-Community-Toolkit/shared-configuration.git shared-configuration
```

Next create a new **Directory.Build.props** file at the root of the MonoGame Community Toolkit repository with the following content:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project>
    <PropertyGroup>
        <!-- This MUST be defined before importing props. -->
        <SolutionDirectory>$(MSBuildThisFileDirectory)</SolutionDirectory>
    </PropertyGroup>

    <!-- Import the shared global .props file -->
    <Import Project="$(MSBuildThisFileDirectory)shared-infrastructure\msbuild\Shared.Global.props" />
</Project>
```

Next, create a **Directory.Build.targets** file at the root of the MonoGame Community Toolkit repository with the following content:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project>
    <!-- Import the shared global .props file -->
    <Import Project="$(MSBuildThisFileDirectory)shared-infrastructure\msbuild\Shared.Global.targets"/>
</Project>
```

