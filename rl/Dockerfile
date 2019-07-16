# Taken from tensorflow/tensorflow:latest-gpu-py3 dockerfile.
# https://github.com/tensorflow/tensorflow/blob/master/tensorflow/tools/dockerfiles/dockerfiles/gpu.Dockerfile
# Original license applies.

ARG UBUNTU_VERSION=18.04
ARG ARCH=
ARG CUDA=10.0

FROM nvidia/cuda:${CUDA}-base-ubuntu${UBUNTU_VERSION} as base

ARG ARCH
ARG CUDA
ARG CUDNN=7.4.1.5-1

SHELL ["/bin/bash", "-c"]

RUN apt-get update && apt-get install -y --no-install-recommends \
        build-essential cuda-command-line-tools-${CUDA/./-} cuda-cublas-${CUDA/./-} \
        cuda-cufft-${CUDA/./-} cuda-curand-${CUDA/./-} cuda-cusolver-${CUDA/./-} \
        cuda-cusparse-${CUDA/./-} curl libcudnn7=${CUDNN}+cuda${CUDA} \
        libfreetype6-dev libhdf5-serial-dev libzmq3-dev pkg-config software-properties-common unzip

ENV LD_LIBRARY_PATH /usr/local/cuda/extras/CUPTI/lib64:/usr/local/cuda/lib64:$LD_LIBRARY_PATH

ARG PYTHON=python3
ARG PIP=pip3

ENV LANG C.UTF-8

RUN apt-get update && apt-get install -y \
    ${PYTHON} \
    ${PYTHON}-pip

RUN ${PIP} --no-cache-dir install --upgrade \
    pip \
    setuptools

RUN ln -s $(which ${PYTHON}) /usr/local/bin/python 

ARG TF_PACKAGE=tensorflow
ARG TF_PACKAGE_VERSION=
RUN ${PIP} install ${TF_PACKAGE}${TF_PACKAGE_VERSION:+==${TF_PACKAGE_VERSION}}

## More stuff

# PyTorch
RUN ${PIP} install https://download.pytorch.org/whl/cu100/torch-1.1.0-cp36-cp36m-linux_x86_64.whl
RUN ${PIP} install https://download.pytorch.org/whl/cu100/torchvision-0.3.0-cp36-cp36m-linux_x86_64.whl

# Tensorflow / Keras
RUN ${PIP} install keras

# OpenAI Gym
RUN ${PIP} install gym[atari]

# OpenGL check
RUN apt-get install -y mesa-utils
