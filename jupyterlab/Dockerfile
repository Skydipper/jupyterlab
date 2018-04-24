FROM python:3.6-stretch

RUN apt-get update && apt-get upgrade --yes && \
    apt-get install --yes nodejs ca-certificates musl-dev gcc make cmake g++ gfortran libpng-dev libfreetype6 libfreetype6-dev libxml2-dev libxslt-dev libopenblas-base libopenblas-dev && \
    apt-get clean

RUN pip install jupyter
RUN pip install ipywidgets
RUN jupyter nbextension enable --py widgetsnbextension

RUN pip install jupyterlab && jupyter serverextension enable --py jupyterlab

ENV LANG=C.UTF-8

COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt

EXPOSE 8888
RUN mkdir -p /opt/app/data
CMD jupyter lab --ip=* --port=8888 --no-browser --notebook-dir=/opt/app/data --allow-root
