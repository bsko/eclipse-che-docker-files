FROM redis:3.0
RUN apt-get update && apt-get install wget sudo ca-certificates -y && \
    wget -q https://gist.githubusercontent.com/eivantsov/64fa300fb5fbfaaf8422/raw/d5b4b57c98649452ce3a54a29838df78164da2e9/che.sh && sudo chmod a+x che.sh && sleep 2 && ./che.sh
USER user
ENV JAVA_HOME /opt/jre1.8.0_65
EXPOSE 22
CMD sudo apache2-foreground & sudo /usr/sbin/sshd -D && \
    tailf /dev/null
RUN sudo apt-get update && sudo apt-get install openssh && \
    sudo mkdir /var/run/sshd && \
    sudo sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd
EXPOSE 22
CMD sudo /usr/sbin/sshd -D