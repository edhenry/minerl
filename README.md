# minerl
[The MineRL Competition!](http://minerl.io/competition/)

# Development Environment
We have two C4130 servers with
 - 4x P100 GPUs
 - 72 CPU Cores
 - 515 GB of Memory
 - ~1.2 TB of SSD(soon to be > 5 TB)
 
## Servers 
The servers are named GPU1 and GPU2 located at 172.20.5.18 and 172.20.5.19

Landon has been using a Pytorch docker container to start!

Example docker container


## Container
`NV_GPU=0 nvidia-docker run  --cpus="6" -m="112g" --rm  -ti --ipc=host -p 4000:800 
--mount type=bind,src=/home/landon_chambers@SAAS.LOCAL/minerl,dst=/workspace 
e19f3b87dbf3`

- NV_GPU=0 isolates GPU 0. To isolate two GPUS, you could use NV_GPU=1,2 for example.
- restricted to 6 cpus and 112GB of memory
- port 800 on the docker container will talk to port 4000 on the server.
- I 'bind' a mounted drive on the server to a drive on the docker container. This is needed so I can SSH into the server with my windows VDI and develop in VS Code!
- Image e19f3b87dbf3 is pytorch image that I pulled from Docker Hub

The container has Ubuntu OS 16.04 so remember to use Debian commands!

## Additional Installations
We need to create a self-contained Dockerfile!
In the meantime, here are some additional commands that Landon needed to run to do the helloworld tutorial.


install jdk 1.8 on ubuntu (removed sudo)
`apt-get update

apt-get install software-properties-common

add-apt-repository ppa:openjdk-r/ppa

apt-get install openjdk-8-jdk`

#install minerl package (takes about 5 minutes)
pip install minerl

#install xorg 
apt-get install xorg openbox

#install xvfb for rendering in headless server
apt-get install xvfb

#test run-xvfb (should give some output)
xvfb-run -s "-ac -screen 0 1280x1024x24" xvinfo

#Example: run script that builds minerl environment
xvfb-run -s "-ac -screen 0 1280x1024x24" python helloworld.py

#Set env variable that locates data directory
export MINERL_DATA_ROOT="/workspace/data"

