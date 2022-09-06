FROM nvidia/cuda:10.1-devel-ubuntu18.04
ARG DEBIAN_FRONTEND=noninteractive
RUN echo "Acquire::http::Proxy \"http://10.112.15.117:3128\";" > /etc/apt/apt.conf.d/proxy.conf
# RUN echo "Acquire::https::Proxy \"https://10.112.15.117:3128\";" >> /etc/apt/apt.conf.d/proxy.conf
WORKDIR /root
ENV TZ=Asia/Seoul
RUN apt update
RUN apt install -y git
ARG HTTP_PROXY=http://10.112.15.117:3128
ARG HTTPS_PROXY=http://10.112.15.117:3128
RUN git clone -b 0.26.0  https://github.com/facebookresearch/bitsandbytes.git
# RUN git clone https://github.com/TimDettmers/bitsandbytes.git
RUN cd bitsandbytes && make cuda10x CUDA_VERSION=101
RUN apt install -y python3 python3-pip
RUN python3 -m pip install --upgrade pip
RUN pip3 install setuptools
# RUN cd bitsandbytes && python3 setup.py build
RUN cd bitsandbytes && python3 setup.py sdist bdist_wheel
