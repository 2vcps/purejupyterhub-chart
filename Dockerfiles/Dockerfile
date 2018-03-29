FROM jupyter/tensorflow-notebook:c88678a1c7c9


ARG JUPYTERLAB_VERSION=0.31.12
RUN     pip install jupyterlab==$JUPYTERLAB_VERSION \
    &&  jupyter labextension install @jupyterlab/hub-extension
