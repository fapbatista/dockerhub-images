FROM fapbatista/tf-keras-torch
RUN apt-get update
RUN apt-get install gcc-6 -y
RUN apt-get install protobuf-compiler libprotoc-dev -y
RUN pip3 install Cython
RUN pip3 install --upgrade keyrings.alt
RUN pip3 install --upgrade gensim
RUN pip3 install nltk
RUN pip3 install spacy
RUN pip3 install pytext-nlp
RUN pip3 install fasttext