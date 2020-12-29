FROM mindspore/mindspore-gpu:runtime
RUN wget https://developer.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda_10.1.105_418.39_linux.run
RUN apt-get install freeglut3 freeglut3-dev libxi-dev libxmu-dev libxml2:amd64 -y
RUN uname -a && exit
RUN sh cuda_10.1.105_418.39_linux.run --silent --driver --toolkit && rm cuda_10.1.105_418.39_linux.run
RUN groupadd --gid 1000 jovyan \
    && useradd --home-dir /home/jovyan --create-home --uid 1000 \
    --gid 1000 --shell /bin/sh --skel /dev/null jovyan
USER jovyan
RUN pip install jupyter --user
ENV PATH="/home/jovyan/.local/bin:/usr/local/cuda-10.1/bin:${PATH}"
ENV LD_LIBRARY_PATH="/usr/local/cuda-10.1/lib64:${LD_LIBRARY_PATH}"
ENV NB_PREFIX /
RUN pip install --user https://ms-release.obs.cn-north-4.myhuaweicloud.com/1.0.1/MindSpore/gpu/ubuntu_x86/cuda-10.1/mindspore_gpu-1.0.1-cp37-cp37m-linux_x86_64.whl
CMD ["sh","-c", "/home/jovyan/.local/bin/jupyter notebook --notebook-dir=/home/jovyan --ip=0.0.0.0 --no-browser --allow-root --port=8888 --NotebookApp.token='' --NotebookApp.password='' --NotebookApp.allow_origin='*' --NotebookApp.base_url=${NB_PREFIX}"]