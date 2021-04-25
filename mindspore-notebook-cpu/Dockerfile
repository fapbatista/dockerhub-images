FROM mindspore/mindspore-cpu:runtime
RUN apt-get install freeglut3 freeglut3-dev libxi-dev libxmu-dev libxml2:amd64 -y
RUN uname -a && exit
ENV PYTHONPATH=/usr/local/python-3.7.5/bin/python3
ENV PATH="/usr/local/python-3.7.5/bin:${PATH}"
ENV PATH="${PYTHONPATH}:${PATH}"
ENV PATH="/home/jovyan/.local/bin:${PATH}"
RUN groupadd --gid 1000 jovyan \
    && useradd --home-dir /home/jovyan --create-home --uid 1000 \
    --gid 1000 --shell /bin/sh --skel /dev/null jovyan
USER jovyan
RUN pip install jupyter --user

ENV NB_PREFIX /
RUN pip install --user pip install https://ms-release.obs.cn-north-4.myhuaweicloud.com/1.1.0/MindSpore/cpu/ubuntu_x86/mindspore-1.1.0-cp37-cp37m-linux_x86_64.whl
CMD ["sh","-c", "/home/jovyan/.local/bin/jupyter notebook --notebook-dir=/home/jovyan --ip=0.0.0.0 --no-browser --allow-root --port=8888 --NotebookApp.token='' --NotebookApp.password='' --NotebookApp.allow_origin='*' --NotebookApp.base_url=${NB_PREFIX}"]