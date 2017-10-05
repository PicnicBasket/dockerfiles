# EventStore (geteventstore.com)
#
# VERSION               3.3.0

FROM microsoft/windowsservercore
MAINTAINER Picnic Software

ADD http://download.geteventstore.com/binaries/EventStore-OSS-Win-v3.3.0.zip /EventStore.zip
RUN Expand-Archive -Path /EventStore.zip -DestinationPath /EventStore

EXPOSE 2113
EXPOSE 1113

RUN New-Item -Path Data -ItemType Directory
RUN New-Item -Path Logs -ItemType Directory

ENV EVENTSTORE_MAX_MEM_TABLE_SIZE 100000
ENV EVENTSTORE_WORKER_THREADS 12

WORKDIR /EventStoreDocker/EventStore-OSS-Win-v3.3.0

CMD /EventStore/EventStore.ClusterNode.exe --db /Data --log /Logs --ext-ip 0.0.0.0 --ext-http-prefixes 'http://+:2113/' 
