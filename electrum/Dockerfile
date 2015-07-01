FROM ubuntu:14.10

RUN apt-get update
#RUN apt-get install -y libleveldb1 libleveldb-dev python3-pip python3-setuptools python-openssl python git
RUN apt-get install -y g++ git python-dev python-setuptools python-openssl python-leveldb libleveldb-dev
#RUN apt-get install -y virtualenv
#RUN virtualenv ding
#RUN source ding/bin/activate
#RUN pip3 install plyvel
#RUN deactivate
RUN easy_install jsonrpclib plyvel

EXPOSE 50001
EXPOSE 8081
EXPOSE 50002
EXPOSE 8082

RUN useradd -m electrum

WORKDIR /home/electrum
RUN mkdir .python-eggs
RUN chmod og-w .python-eggs

RUN git clone https://github.com/spesmilo/electrum-server.git
WORKDIR /home/electrum/electrum-server
RUN chown -R electrum ..
RUN ./configure
RUN python ./setup.py install
#ADD enter /enter
#RUN	chmod +x /enter
ENTRYPOINT ["/home/electrum/enter"]
ADD	* /home/electrum/



