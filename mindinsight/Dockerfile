FROM mindspore/mindspore-cpu:runtime
COPY src /home/jovyan/src
WORKDIR /home/jovyan
RUN apt-get install -y build-essential
RUN wget https://github.com/Kitware/CMake/releases/download/v3.19.2/cmake-3.19.2.tar.gz
RUN tar -zxvf cmake-3.19.2.tar.gz
WORKDIR /home/jovyan/cmake-3.19.2
RUN ./bootstrap && make && make install
WORKDIR /home/jovyan/node
RUN wget https://nodejs.org/download/release/v10.19.0/node-v10.19.0-linux-x64.tar.xz
RUN tar -xf node-v10.19.0-linux-x64.tar.xz
RUN mv node-v10.19.0-linux-x64/ /usr/local/node
ENV PATH="/usr/local/node/bin:${PATH}"
RUN pip install pybind11
WORKDIR /home/jovyan/src
RUN pip install -r /home/jovyan/src/requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
ENV PYTHONPATH=/usr/local/python-3.7.5/bin/python3
ENV PATH="/usr/local/python-3.7.5/bin:${PATH}"
ENV PATH="${PYTHONPATH}:${PATH}"
RUN pip install python-config configparser wheel
RUN python setup.py install
RUN bash ./build/build.sh
RUN pip install /home/jovyan/src/output/mindinsight-1.1.0-cp37-cp37m-linux_x86_64.whl -i https://pypi.tuna.tsinghua.edu.cn/simple
WORKDIR /home/jovyan
#RUN pip install https://ms-release.obs.cn-north-4.myhuaweicloud.com/1.0.1/MindInsight/ascend/ubuntu_x86/mindinsight-1.0.1-cp37-cp37m-linux_x86_64.whl --trusted-host ms-release.obs.cn-north-4.myhuaweicloud.com -i https://pypi.tuna.tsinghua.edu.cn/simple
RUN groupadd --gid 1000 jovyan \
    && useradd --home-dir /home/jovyan --create-home --uid 1000 \
    --gid 1000 --shell /bin/sh --skel /dev/null jovyan
RUN apt-get install -y supervisor
ENV MINDINSIGHT_CONFIG=/home/jovyan/config.py
COPY config.py /home/jovyan/config.py
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
CMD ["/usr/bin/supervisord"]