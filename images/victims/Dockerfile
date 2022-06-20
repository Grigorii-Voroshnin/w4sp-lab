#import from w4sp base
FROM w4sp/labs:base

RUN git clone https://github.com/secdev/scapy.git
RUN cd scapy && python setup.py install

RUN git clone https://gitlab.cern.ch/smm-rme/pysmbclient.git
RUN cd pysmbclient && python setup.py install
RUN apt-get install -y winbind dhcping

#set dhclient.conf to be aggressive with dhcp requests
RUN echo 'retry 10;' >> /etc/dhcp/dhclient.conf
RUN echo 'timeout 10;' >> /etc/dhcp/dhclient.conf

#fixup nsswitch so we can resolve wins
RUN sed 's/files dns/wins files dns/' /etc/nsswitch.conf >> /etc/nsswitch.conf

ADD start_vic.py /start_vic.py
#add configs for supervisord
ADD supervisor_vics.conf /etc/supervisor/conf.d/supervisor_vics.conf




