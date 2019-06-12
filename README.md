# minerl
[The MineRL Competition!](http://minerl.io/competition/)

# Development Environment
We have two C4130 servers with
 - 4x P100 GPUs
 - 72 CPU Cores
 - 515 GB of Memory
 - ~1.2 TB of SSD(soon to be > 5 TB)
 
 The servers are named GPU1 and GPU2 located at 172.20.5.18 and 172.20.5.19

Landon has been using a Pytorch docker container to start!

Example docker container

`NV_GPU=0 nvidia-docker run  --cpus="6" -m="112g" --rm  -ti --ipc=host -p 4000:800 \
--mount type=bind,src=/home/landon_chambers@SAAS.LOCAL/minerl,dst=/workspace \
e19f3b87dbf3`
