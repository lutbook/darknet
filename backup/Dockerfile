#from tensorflow/tensorflow:latest-devel-gpu
#from nvidia/cuda:10.2-cudnn7-runtime
#rom nvidia/cuda:10.1-cudnn7-devel-ubuntu18.04
from nvidia/cuda:10.2-cudnn7-devel-ubuntu18.04
#from spmallick/opencv-docker:opencv

ENV DEBIAN_FRONTEND noninteractive
run apt update
run apt install -y build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev

run apt install -y python3-pip
run apt-get install -y pkg-config
run apt-get -y install python3-opencv
run apt-get -y install clang
run apt install -y dos2unix
run apt-get -y install cmake
run apt upgrade -y

#copy /kw_resources/darknet_07 /kw_resources/
#workdir /kw_resources/darknet_07
#run git clone --single-branch --branch master https://github.com/yoshihikoueno/DNNCancerAnnotator
#workdir DNNCancerAnnotator
#workdir /darknet
#cmd ./run.sh
run gcc --version
run nvcc --version
run clang --version
run nvidia-smi
run make -j
run chmod +x /kw_resources/darknet_07 ./darknet

workdir /kw_resources/darknet_07
run dos2unix ./data/train.txt
run dos2unix ./data/val.txt
run dos2unix ./data/yolo.data
run dos2unix ./data/yolo.names
run dos2unix ./cfg/yolov4-custom_trainPole_20200727.cfg
run ./darknet detector train data/yolo.data cfg/yolov4-custom_trainPole_20200727.cfg yolov4.conv.137
