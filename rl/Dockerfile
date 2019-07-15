FROM tensorflow/tensorflow:latest-gpu-py3-jupyter
ENV NAME rl

# Python
RUN apt update
RUN apt install -y python3 python3-pip

# PyTorch
RUN pip3 install https://download.pytorch.org/whl/cu100/torch-1.1.0-cp36-cp36m-linux_x86_64.whl
RUN pip3 install https://download.pytorch.org/whl/cu100/torchvision-0.3.0-cp36-cp36m-linux_x86_64.whl

# Tensorflow / Keras
RUN pip3 install keras

# OpenAI Gym
RUN pip3 install gym[atari]
