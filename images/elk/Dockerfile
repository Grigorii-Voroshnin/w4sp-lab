#build off of w4sp base image
FROM w4sp/labs:base

RUN wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg 
RUN apt-get install apt-transport-https
RUN echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D27D666CD88E42B4
RUN sudo apt update
RUN sudo apt -y install elasticsearch
RUN sudo apt -y install default-jre-headless

ENV KIBANA_VERSION 4.4.1 

RUN cd /tmp && \
    wget -nv https://download.elastic.co/kibana/kibana/kibana-${KIBANA_VERSION}-linux-x64.tar.gz && \
    tar zxf kibana-${KIBANA_VERSION}-linux-x64.tar.gz && \
    rm -f kibana-${KIBANA_VERSION}-linux-x64.tar.gz && \
    mv /tmp/kibana-${KIBANA_VERSION}-linux-x64 /kibana

RUN echo 'network.host: 0.0.0.0' >> /etc/elasticsearch/elasticsearch.yml

#add supervisor conf to start kibana and es
ADD supervisor_elk.conf /etc/supervisor/conf.d/supervisor_elk.conf
