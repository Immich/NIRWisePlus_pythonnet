# NIRWisePlus_pythonnet
Example of Python and c# integration

## Integrate C# and Python through Pythonnet

1. Create an environment (optional but recommended) `conda create -n myenv python=3.7`
2. Clone the pythonnet [repo](https://github.com/pythonnet/pythonnet)
3. In the pythonnet folder, cd src\runtime
4. Create the dll `$dotnet build -c ReleaseMonoPY3 -f netstandard2.0 Python.Runtime.csproj`
5. You must set Runtime.PythonDLL property or PYTHONNET_PYDLL environment variable (Typical values are python3X.dll (Windows), libpython3.X.dylib (Mac), libpython3.X.so (most other *nix))
6. Configure dylib for (unix systems) `$conda env config vars set PYTHONNET_PYDLL=/opt/anaconda3/envs/ml/lib/libpython3.7m.dylib`
7. cs.proj should be in the same directory as the the script.cs
8. Modify csproj
```
<Project Sdk="Microsoft.NET.Sdk">
 
 <PropertyGroup>
   <OutputType>Exe</OutputType>
   <TargetFramework>net5.0</TargetFramework>
 </PropertyGroup>
 
 <ItemGroup>
   <Reference Include="Python.Runtime">
       <HintPath>/Users/michellediazvi/NET/pythoneto/pythonnet/pythonnet/runtime/Python.Runtime.dll</HintPath>
   </Reference>
 </ItemGroup>
 
</Project>
``` 
8. Run `$dotnet run --framework net5.0`
