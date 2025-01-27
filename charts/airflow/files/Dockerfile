FROM apache/airflow:2.6.2

WORKDIR /opt/airflow
RUN pip install apache-airflow-providers-apache-spark

USER root
RUN apt-get update -y && apt-get install openjdk-17-jdk -y

USER 50000