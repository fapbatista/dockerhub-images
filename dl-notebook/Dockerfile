FROM fapbatista/tf-keras-torch
RUN /usr/bin/python3 -m pip install --upgrade pip
RUN pip3 install Pillow
RUN pip3 install Cython
RUN pip3 install fasttext
RUN pip3 install requests
RUN pip3 install spacy
RUN pip3 install jupyter
RUN pip3 install kfp 
RUN pip3 install transformers
RUN pip3 install nltk
RUN apt-get update -y
RUN apt-get install git -y
RUN export PATH=$PATH:~/.local/bin
RUN which dsl-compile
ENV NB_PREFIX /
RUN groupadd --gid 1000 jovyan \
    && useradd --home-dir /home/jovyan --create-home --uid 1000 \
    --gid 1000 --shell /bin/sh --skel /dev/null jovyan
USER jovyan
CMD ["sh","-c", "jupyter notebook --notebook-dir=/home/jovyan --ip=0.0.0.0 --no-browser --allow-root --port=8888 --NotebookApp.token='' --NotebookApp.password='' --NotebookApp.allow_origin='*' --NotebookApp.base_url=${NB_PREFIX}"]