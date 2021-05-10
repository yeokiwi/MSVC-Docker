# container
This file is used for creation of docker image for vs2015 c++/C# build.
In addition to this file, the docker creation will require vs2015 docker public assemblies directory and win64 directory

C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\PublicAssemblies

C++ compilation:

1. The compilation only works in Release mode.
2. It also requires Windows SDK10 instead of Windows SDK 8.1
3. The C/C++ "DEbug Information Format" will have to set to "None"
4. If you switch to SDK10, you will find that you will be unable to compile as rc.exe is not found. you will need to add the following path to your environmental variables "C:\Program Files(x86)\Windows Kits\8.1\bin\x64"
5. To generate deterministic build, the following needs to be added
Under C/C++ => Command Line => Additonal Options, include the following:
/D__DATE__=CONSTANT /D__TIME__=CONSTANT
Under linker => Command Line => Additonal Options, include the following:
/Brepro

C# compilation

1. For those projects that need unittest framework, you will need to add "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\PublicAssemblies" to your reference path. It will not affect your current native compilation.
2. To generate deterministic build, <Deterministic>true</deterministic> needs to be added into csproj under "\<propertygroup\>\<\/propertygroup\>"



