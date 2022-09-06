FROM nvidia/cuda:10.1-devel-ubuntu18.04
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Asia/Seoul
RUN apt update
RUN apt install -y git
RUN git clone https://github.com/TimDettmers/bitsandbytes.git
RUN cd bitsandbytes && make cuda10x_nomatmul
RUN apt install -y python3 python3-pip
RUN python3 -m pip install --upgrade pip
RUN pip3 install setuptools
RUN cd bitsandbytes && python3 setup.py sdist bdist_wheel

