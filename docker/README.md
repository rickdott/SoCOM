The /docker directory contains the files required to build and run the docker image that is used for development on UU servers or at home. This allows everyone that uses this software to use the same versions of packages etc.

### Building and/or starting the Docker image
1. Make sure Docker is installed and available from the command line. The `install_*.sh` files included in this folder can be used to install additional dependencies or software, like Docker, GitHub CLI and Visual Studio Code.
2. Make sure you have cloned the [hmp-ai package](https://github.com/rickdott/hmp-ai) and [this](https://github.com/rickdott/socom) repository to the same folder, your folder structure should look like:

GIT/\
├── SoCOM/\
│ ├── docker/\
│ │ └── README.md (this file)\
├── hmp-ai/\
├── hmp/ 

>    Clone the [hmp](https://github.com/rickdott/hmp) repository if you want to use the forked version of HMP.

3. Make a copy of `.env_EXAMPLE` and rename it to `.env`, change the `DATA_PATH` variable to represent the location inside the Docker container that has the data (this folder contains `sat1`, `sat2`, `ar` folders), mounted from a network share or locally. Edit `SOLIS_ID` and `PASSWORD` to represent your UU credentials. This file is not pushed to git repositories and the `PASSWORD` environment variable is removed after using it to mount the network share. Make sure you are authorized by tech support to read and write to the folder in `mount_drive.sh`.
4. Open command line/terminal in the /docker directory.
5. Run `docker compose build` and then `docker compose up -d`, this will do everything required to build and start the image.
6. You can open a terminal inside the running Docker container by running `docker exec -it hmp-ai /bin/bash`.

### Running code inside the Docker image
1. Install Visual Studio Code (You run it from the command line by using `code .` to open a VSCode instance in the current directory)
2. Install the 'Docker' extension for VSCode
3. A whale has found its way into your VS Code sidebar, click on it, right-click the running Docker container and click 'Attach Visual Studio Code', find the `/workspace` directory, going up a directory if `/root` is automatically selected. Changes you make to files in `SoCOM` or `hmp-ai` are synchronized on your host machine and the docker container. This allows you to run code in the container and edit it locally or in the container, whichever is preferred. This approach ensures one source of truth for the code.
4. Make sure that the notebooks use the `base` conda kernel (selector top-right)

You are now able to work inside the Docker container.
