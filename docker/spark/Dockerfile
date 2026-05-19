FROM apache/spark:latest

USER root

# Instalar Python 3.11 para compatibilidad con Spark 4.1.1
RUN apt-get update && \
    apt-get install -y software-properties-common && \
    add-apt-repository -y ppa:deadsnakes/ppa && \
    apt-get update && \
    apt-get install -y python3.11 && \
    apt-get clean && rm -rf /var/lib/apt/lists/* && \
    update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.11 1 && \
    update-alternatives --set python3 /usr/bin/python3.11

# Configurar PySpark para usar Python 3.11
ENV PYSPARK_PYTHON=python3.11
ENV PYSPARK_WORKER_PYTHON=python3.11

USER spark
