# singularity_ML
singularity container for machine learning in Python

## Reusing the Recipe
Extra packages could be combined into the container with adding 
```
pip3 install package_name
```
to the %post section in the recipe file.

## Starting the Singularity Container and Running Jupyter Notebook
If the container is to be used on local machine, first pull the singularity image from Sylabs with
```
singularity pull --name your_image_name.sif library://dylanyang/default/singularity_machine_learning:sha256.297b554c8114b201eb634dcde1cfa2a78bdd8b2332b247004d74f151f865919b
```
Given that the pre-built image has also been pulled or a self-built version of singularity image is preferred (suppose the self-built image is also named your_image_name.sif), then the following commands could be run to start jupyter notebook
```
singularity run --bind /local_data:/data,/local_scratch:/scratch your_image_name.sif jupyter notebook
```
If the container is used on a remote server, initiate a port forwarding upon logging in
```
ssh -L XXXXX:localhost:XXXXX user_name@host_name
```
where XXXXX can be any port number of your choice, typical choices are five digit numbers. 
Then pull the image with the above command and run jupyter notebook with 
```
singularity run --bind /local_data:/data,/local_scratch:/scratch your_image_name.sif jupyter notebook --port XXXXX
```

After running singularity the following information will be printed to the terminal
```
[I 18:15:17.676 NotebookApp] Serving notebooks from local directory: /local_directory
[I 18:15:17.676 NotebookApp] The Jupyter Notebook is running at:
[I 18:15:17.676 NotebookApp] http://localhost:10001/?token=399bc21f3afd6e829a45a81ebac36eb624e48dfe50a34aae
[I 18:15:17.676 NotebookApp]  or http://127.0.0.1:10001/?token=399bc21f3afd6e829a45a81ebac36eb624e48dfe50a34aae
[I 18:15:17.676 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[W 18:15:17.679 NotebookApp] No web browser found: could not locate runnable browser.
[C 18:15:17.679 NotebookApp]

    To access the notebook, open this file in a browser:
        file:///home/hyang/.local/share/jupyter/runtime/nbserver-27179-open.html
    Or copy and paste one of these URLs:
        http://localhost:10001/?token=399bc21f3afd6e829a45a81ebac36eb624e48dfe50a34aae
     or http://127.0.0.1:10001/?token=399bc21f3afd6e829a45a81ebac36eb624e48dfe50a34aae
```
Next open a browser and copy the URL to the browser to access Jupyter Notebook
```
http://localhost:10001/?token=399bc21f3afd6e829a45a81ebac36eb624e48dfe50a34aae
```
