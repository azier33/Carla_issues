# Carla_issues
<h1 align=center>
THis is an issues collections about carla with Ubuntu 22.04
</h1>

## 📌 Setup
We try to install carla 0.9.13 on Ubuntu 22.04 with two RTX 4090 GPUs(48G).

### Environment 
The firt steps is installing the python which version is compatable. The default python version of Ubuntu 22.04 is 3.10, but the carla 0.9.13 need python <= 3.9, So that we try to install python 3.9 firstly on the server and set the path.

We recommand to create an conda enviroment for the installation.
    
    conda create -n carla-py39 python=3.9
    conda create carla-py39
    
When there is a limitation about user permitation, the correct approach is to modify the permissions of the corresponding folder use [chmod +x], do not to use [sudo] command.

    chmod +x /path/to/limit
    
### Installation
Try to clone the repositories from carla 0.9.13

    git clone https://github.com/carla-simulator/carla.git

Please adjust the version of carla.

The key step is transfer the link in the [./Update.sh], if there is an error aboult content is too old when running [make launch] command, you should use the link as follow

    CONTENT_LINK=https://carla-assets.s3.us-east-005.backblazeb2.com/${CONTENT_ID}.tar.gz

Then you should compile the Python API client:

    make PythonAPI ARGS="--python-version=3.9"

## Usage
Launch the UE4 by command:
    cd ~/carla
    make launch

click the [play] button and then run an example: 
    cd ~/carla/PythonAPI/examples
    python3 manual_control.py
