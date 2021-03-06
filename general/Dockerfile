FROM tensorflow/tensorflow:1.9.0-py3

MAINTAINER Seongheon Henry Lee <skynspace@kaist.ac.kr>
#sudo docker run -d -p 8888:8888 -p 6006:6006 -v $PWD:/mnt/notebooks/ [IMAGE] 
#sudo docker run -it -p 8888:8888 -p 6006:6006 -v $PWD:/mnt/notebooks/ [IMAGE]
#sudo docker exec -it [NAME] /bin/bash

#! Linux apps. 
RUN apt-get update && \
    apt-get install -y \
        build-essential \
        cmake \
        git \
        libavformat-dev \
        libhdf5-dev \
        libjasper-dev \
        libjpeg-dev \
        libpng-dev \
        libpq-dev \
        libswscale-dev \
        libtbb-dev \
        libtbb2 \
        libtiff-dev \
        pkg-config \
        python-opengl \
        unzip \
        vim \
        wget \
        xvfb \
        yasm
        
        
WORKDIR /mnt/notebooks


#! Python libs. with OpenAI Gym 
RUN pip3 --no-cache-dir install \
        cvxpy \
        h5py \
        hdf5storage \
        matplotlib \
        numpy \
        pandas \
        py3nvml \
        scipy \
        scikit-learn \
    && pip3 --no-cache-dir install \
        gym \
# Dependency to render OpenAI Gym in a Jupyter notebook as a gif.
    && git clone https://github.com/jakevdp/JSAnimation \
        && cd JSAnimation \
        && python3 setup.py install \
# Ver 0.2
    && python3 -m pip install gym[atari] \
    && python3 -m pip install scikit-image


#! Ports
# Jupyter Notebook
EXPOSE 8888
# TensorBoard
EXPOSE 6006


#! System settings
# Virtual frame buffer settings for the OpenAI Gym 
RUN echo '#!/bin/bash' > /tmp/openai-gym.sh && \
    echo '/usr/bin/xvfb-run -s "-screen 0 1280x720x24" /usr/local/bin/jupyter-notebook --no-browser --ip=0.0.0.0 --notebook-dir=/mnt/notebooks --allow-root' >> /tmp/openai-gym.sh && \
    chmod +x /tmp/openai-gym.sh
CMD ["/tmp/openai-gym.sh"]
