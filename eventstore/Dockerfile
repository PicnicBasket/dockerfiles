FROM microsoft/windowsservercore
LABEL title="EventStore (geteventstore.com)"
LABEL version="4.0.2"
LABEL author="Picnic Software"

ADD https://eventstore.org/downloads/EventStore-OSS-Win-v4.0.2.zip /EventStore.zip
RUN powershell -command Expand-Archive -Path /EventStore.zip -DestinationPath /EventStore
RUN powershell -command Remove-Item /EventStore.zip -Force

EXPOSE 2113
EXPOSE 1113

RUN powershell -command New-Item -Path Data -ItemType Directory
RUN powershell -command New-Item -Path Logs -ItemType Directory

ENV EVENTSTORE_MAX_MEM_TABLE_SIZE 100000
ENV EVENTSTORE_WORKER_THREADS 12
ENV TZ "Australia/Melbourne"

WORKDIR /EventStoreDocker/EventStore-OSS-Win-v4.0.2

CMD /EventStore/EventStore.ClusterNode.exe --ext-http-prefixes http://+:2113/ --ext-ip 0.0.0.0 --db /Data --log /Logs --run-projections=all