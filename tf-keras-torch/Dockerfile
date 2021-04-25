FROM tensorflow/tensorflow:2.2.0-gpu
RUN /usr/bin/python3 -m pip install --upgrade pip
RUN pip3 install numpy
RUN pip3 install keras
RUN pip3 install requests
RUN pip3 install pandas
RUN pip3 install torch==1.7.1+cu110 torchvision==0.8.2+cu110 -f https://download.pytorch.org/whl/torch_stable.html
RUN pip3 install sklearn
RUN pip3 install boto3