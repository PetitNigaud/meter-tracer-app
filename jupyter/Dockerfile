FROM jupyter/minimal-notebook:python-3.11.6

#USER root

#RUN apt-get update && apt-get install ffmpeg libsm6 libxext6  -y
#RUN apt-get update && apt-get install -y tesseract-ocr

#USER $NB_USER

COPY requirements.txt /tmp

RUN pip install --no-cache-dir -r /tmp/requirements.txt && \
    pip install --no-cache-dir --upgrade jupyterlab jupyterlab-git

