#import from w4sp base
FROM w4sp/labs:base

RUN sudo apt -y install wget
RUN sudo wget https://github.com/secdev/scapy/archive/refs/tags/v2.5.0.tar.gz
RUN sudo tar -xvf v2.5.0.tar.gz
RUN cd scapy-2.5.0 && sudo python setup.py install

RUN sudo wget https://github.com/jbsilva/pysmbclient/archive/refs/heads/main.zip
RUN sudo apt install unzip
RUN sudo unzip main.zip
RUN cd pysmbclient-main && python setup.py install
RUN apt-get install -y winbind dhcping

#set dhclient.conf to be aggressive with dhcp requests
RUN echo 'retry 10;' >> /etc/dhcp/dhclient.conf
RUN echo 'timeout 10;' >> /etc/dhcp/dhclient.conf

#fixup nsswitch so we can resolve wins
RUN sed 's/files dns/wins files dns/' /etc/nsswitch.conf >> /etc/nsswitch.conf

ADD start_vic.py /start_vic.py
#add configs for supervisord
ADD supervisor_vics.conf /etc/supervisor/conf.d/supervisor_vics.conf




