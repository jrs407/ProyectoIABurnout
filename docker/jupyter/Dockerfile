FROM quay.io/jupyter/pyspark-notebook:latest

USER root

# Desinstalar Python 3.13 y instalar Python 3.11
RUN apt-get update && \
    apt-get install -y software-properties-common && \
    add-apt-repository -y ppa:deadsnakes/ppa && \
    apt-get update && \
    apt-get install -y python3.11 python3.11-dev python3.11-distutils && \
    apt-get remove -y python3.13 python3.13-dev || true && \
    update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.11 1 && \
    update-alternatives --install /usr/bin/python python /usr/bin/python3.11 1 && \
    apt-get install -y curl wget git && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Configurar PySpark para Python 3.11
ENV PYSPARK_PYTHON=/usr/bin/python3.11
ENV PYSPARK_DRIVER_PYTHON=/usr/bin/python3.11

WORKDIR /home/${NB_USER}

USER ${NB_UID}
