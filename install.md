
# Installing farmingpy

farmingpy can be installed using pip from github, it has not yet been published to PyPi.

```
pip install git+https://github.com/TwinYields/farmingpy.git
```

Dotnet installation is required to interface APSIM and reading ISOBUS data: https://dotnet.microsoft.com/en-us/download/dotnet/.


## APSIM interface

In order to use APSIM interface from `farmingpy.apsim` you need to install APSIM and add the directory containing the Models executable to path or python path (to find the right .dll files). You can use the APSIM installer or build from source.

The latest tested APSIM version includes farmingpy specific extentions for ensemble modeling and is required if you want to use the `APSIMXEnsemble`class. Newer APSIMX version should work as well.

### Source build

```bash
git clone --depth 1 -b twinclock_grass https://github.com/mpastell/ApsimX
```

On Linux or Mac you can use the following command to build APSIM:

```
dotnet build -o ~/.local/lib/apsimx -c Release ApsimX/Models/Models.csproj
```

On Ubuntu make sure you have sqlite installed:

```
sudo apt install libsqlite3-dev
```

And add the build location to Pythonpath (add this to shell config e.g. `.bashrc` or `.zshrc` to make it permanent):

```bash
export PYTHONPATH=~/.local/lib/apsimx
```

To build APSIM on Windows run the following and add the output directory to path or Python path

```
dotnet build -o %USERPROFILE%\apsimx -c Release ApsimX/Models/Models.csproj
```