FROM fapbatista/nlp-pipelines
RUN apt-get install git -y
RUN pip3 install jupyter
RUN export PATH=$PATH:~/.local/bin
ENV NB_PREFIX /
RUN groupadd --gid 1000 jovyan \
    && useradd --home-dir /home/jovyan --create-home --uid 1000 \
    --gid 1000 --shell /bin/sh --skel /dev/null jovyan
USER jovyan
CMD ["sh","-c", "jupyter notebook --notebook-dir=/home/jovyan --ip=0.0.0.0 --no-browser --allow-root --port=8888 --NotebookApp.token='' --NotebookApp.password='' --NotebookApp.allow_origin='*' --NotebookApp.base_url=${NB_PREFIX}"]