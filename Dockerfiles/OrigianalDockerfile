# CPU: ubuntu22.04
# GPU: nvidia/cuda:11.8.0-cudnn8-devel-ubuntu22.04
FROM nvidia/cuda:11.8.0-cudnn8-devel-ubuntu22.04

# SH -> BASH
SHELL ["/bin/bash", "-c"]

# initialize
RUN apt-get clean && apt-get update
RUN apt-get upgrade -y --fix-missing

# set env
ENV TZ=Asia/Tokyo

# install curl, git, build-essential, opengl
RUN apt-get install -y curl
RUN apt-get install -y git
RUN apt-get install -y build-essential
RUN apt-get install -y libgl1-mesa-glx

# install python
RUN apt-get install -y software-properties-common
RUN add-apt-repository ppa:deadsnakes/ppa
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y python3.10
RUN update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.10 1
RUN apt-get install -y python3.10-dev
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y python3.10-venv

# initialize python
RUN apt-get install -y python3-pip
RUN pip install --upgrade pip
RUN pip install --upgrade setuptools

# sample install librarys
RUN pip install jupyter
RUN pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
RUN pip install timm
RUN pip install numpy
RUN pip install pandas
RUN pip install opencv-python
RUN pip install matplotlib
RUN pip install plotly
RUN pip install scipy
