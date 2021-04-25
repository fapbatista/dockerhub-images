FROM mindspore/mindspore-gpu:devel
RUN wget https://developer.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda_10.1.105_418.39_linux.run
RUN apt-get install freeglut3 freeglut3-dev libxi-dev libxmu-dev libxml2:amd64 -y
RUN uname -a && exit
RUN sh cuda_10.1.105_418.39_linux.run --silent --driver --toolkit && rm cuda_10.1.105_418.39_linux.run
ENV PYTHONPATH=/usr/local/python-3.7.5/bin/python3
ENV PATH="/usr/local/python-3.7.5/bin:${PATH}"
ENV PATH="${PYTHONPATH}:${PATH}"
ENV PATH="/home/jovyan/.local/bin:/usr/local/cuda-10.1/bin:${PATH}"
ENV LD_LIBRARY_PATH="/usr/local/cuda-10.1/lib64:${LD_LIBRARY_PATH}"
RUN pip install https://ms-release.obs.cn-north-4.myhuaweicloud.com/1.0.1/MindSpore/gpu/ubuntu_x86/cuda-10.1/mindspore_gpu-1.0.1-cp37-cp37m-linux_x86_64.whl
CMD ["ls"]