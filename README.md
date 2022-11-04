# PROJECT NAME
## Respository structure  
This repository comes with a predefined directory structure to ensure files are stored in a convenient location. 
- Directories:
  1. `bin`: for external scripts or compiled programs
  2. `data`: for (test) data files, raw data, metadata, images or other content needed to run the application.
  3. `doc`: for general text documentation files.
  4. `docker`: for all Docker related files.
  5. `logs`: for all logs created by the application.
  6. `notebooks`: for all notebooks.
  7. `results`: for all files generated during runtime of the application.
  8. `src`: for all files associated with the application source code.
- Files
  1. `.gitignore`: for ignoring certain files/extensions/directories that should not be a part of the GIT repository.
  2. `requirements.txt`: the Python modules that should be installed on the device when running the scripts from this repository.

When adding new files to the root directory, name those to reflect their content or function.

## Usage  
It is best practice to clone this repository to your local system and create a specific branch for the feature on which you will start work. Once the feature works as expected without compromising the functionality of existing code, create a pull request with the master branch that will include your newly created branch.

## Using Docker
Start a Docker environment in which you can freely develop, without the bother of other packages currently used. Assuming one is currently in this directory:  
```
docker build -t [IMAGE NAME] -f .\docker\Dockerfile .
```
followed by
```
docker run --rm --name [CONTAINER NAME] -v [LOCAL VOLUME]:/home/jovyan/work -p [LOCAL PORT]:8888 --env-file=.\docker\.env [IMAGE NAME]
```
Any custom installed Python packages can be listed in the `requirements.txt` file, such that it gets installed in the image the next time the image is build using the first command.

## Environment variables
The programs makes use of a couple of environment variables, to be set when creating the Docker container. To do so, create a local `.env` file based on the `example.env` file. The information stored in your local `.env` file is not tracked as all `.env` files are ignored through `.gitignore`. To correctly set the environment variables, run the Docker container with the above stated command.