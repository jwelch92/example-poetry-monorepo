# example-poetry-monorepo

An example based on https://medium.com/opendoor-labs/our-python-monorepo-d34028f2b6fa with some tweaks. 

Local packages are installed editable so making library and app changes is seamless. 

## Quirks

- Docker builds need to happen from the root so that it can copy in the `lib` directory for locally installed packages. The `build.sh` script changing dirs. 
- The paths are a little clunky with Poetry's stutter naming for packages.  
- Some editors might not like the multiple projects with their own Poetry managed virtualenvs. 

