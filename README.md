# About
This Docker container contains an installation of TexLive with the `scheme-full` setting which downloads all packages from CTAN.

# Usage
Run the container providing the path to the LaTeX project directory to generate the output files.

1. Clone the repository
2. `cd` into the repository
3. Build the container
    - `docker build -t latex-full .`
4. Optionally, you can just build the container directly from GitHub with the following command:
    - `docker build https://github.com/simutex/docker-latex.git -t latex-full:latest`
5. Wait for the image to be built. It may take a while as all CTAN packages are downloaded and installed.
6. Run the container with:
    - `docker run --rm -i --net=none -v /path/to/project:/data --name latex-full-builder latex-full latexmk -cd -f -interaction=batchmode -pdf in.tex`
7. The output files will be found in the project directory.

# Notes
If you are using this container to automatically build projects based on a given set of parameters, it may be best to provide a unique ID to the `--name` parameters so that Docker does not attempt to create two containers of the same name at the same time. Once the container finishes processing the project it will automatically be removed and the name can be reused.