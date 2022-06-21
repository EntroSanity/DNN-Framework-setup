# TensorFlow-gpu installation on M1 Mac
---
>**Check OS Availability**
Update MacOS Monterey to 12.0+ Otherwise importing errors can occur : 


```sh
import tensorflow as tf
'Expected in: /usr/lib/libc++.1.dylib'
```
---
>**Build Miniforge**
Obtain suitable versions at miniforge [github release page](https://github.com/conda-forge/miniforge/releases), build in the terminal, agree prompted conditions and deploy to the default location :
```sh
sh ~/Downloads/Miniforge3-MacOSX-arm64.sh
```
---
>**Create Conda Environment**


Inside the miniforge folder create virtual conda envrionment and activate it :
```sh
conda create --name <env_name>
conda activate <env_name>
```
---
>** Commands**


Within the virtual environment introduce following packages : 
```sh
## Tensorflow dependencies ##
conda install -c apple tensorflow-deps
## Tensorflow base ##
python -m pip install tensorflow-macos
## Tensorflow plugin ##
python -m pip install tensorflow-metal
```
---
>**Ipykernel**


For the current environment make jupyter notebook observe it : 
```sh
## Automatically add all environments ##
conda install nb_conda_kernels
---
## New kernel otherwise jupyter notebook not recognizing the environment ##
source activate <env_name>
python -m ipykernel install --user --name myenv --display-name "Python (myenv)"
```
>**Examinination**


```sh
gpu = len(tf.config.list_physical_devices('GPU'))>0
print("GPU is", "available" if gpu else "NOT AVAILABLE")
```
