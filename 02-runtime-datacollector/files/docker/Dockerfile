FROM ibmjava:8
WORKDIR /opt/j2se_dc
COPY /j2se_datacollector.tgz /opt/j2se_dc
RUN tar -xf /opt/j2se_dc/j2se_datacollector.tgz
COPY /silent_config_j2se_dc.txt /opt/j2se_dc/bin/
COPY app.jar /opt/
RUN /opt/j2se_dc/bin/config_dc.sh -silent
RUN chmod +x /opt/j2se_dc/runtime/j2sej2seApp.localhost.j2seApp/dcstartup.sh

RUN mkdir /opt/logs
RUN mkdir /opt/j2se_dc/logs
RUN mkdir /opt/j2se_dc/logs/CYN
RUN mkdir /opt/j2se_dc/logs/CYN/logs
RUN mkdir /opt/j2se_dc/logs/CYN/logs/localhost.j2seApp

RUN chmod 777 /opt/logs 
RUN chmod 777 /opt/j2se_dc/logs
RUN chmod 777 /opt/j2se_dc/logs/CYN
RUN chmod 777 /opt/j2se_dc/logs/CYN/logs
RUN chmod 777 /opt/j2se_dc/logs/CYN/logs/localhost.j2seApp

ENTRYPOINT [ "sh", "-c", "/opt/j2se_dc/runtime/j2sej2seApp.localhost.j2seApp/dcstartup.sh" ]