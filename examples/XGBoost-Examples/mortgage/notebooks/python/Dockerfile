FROM gcr.io/datamechanics/spark:platform-3.2-latest

USER root
RUN curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -
RUN apt-get update && apt-get install -y apt-transport-https python3  python3-pip libffi-dev
ENV PYSPARK_MAJOR_PYTHON_VERSION=3

WORKDIR /opt/application/

COPY ./MortgageETL-cpu.ipynb .


RUN apt-get install -y gfortran
RUN pip3 install --upgrade pip
RUN pip3 install cmake
RUN pip3 install xgboost
#RUN pip3 install cudf-cu11 --extra-index-url=https://pypi.ngc.nvidia.com
RUN pip3 install numpy
RUN pip3 install scikit-learn

RUN pip3 install jupyter
RUN conda update jupyter_core jupyter_client
RUN jupyter nbconvert --to script MortgageETL-cpu.ipynb