FROM metasploitframework/metasploit-framework
LABEL maintainer="CSC Club @ IU"

RUN echo "**** INSTALLING DEPENDENCIES ****" && \
	apk add \
		wget \
		curl \
		nmap \
		vim \
		nano \
		npm

RUN npm install -g tldr

RUN echo "**** CONFIGURING TLDR ****" && \
	mkdir -p /root/.local/share/ && \
	loc=/usr/local/bin/tldr && \
	wget -qO $loc https://4e4.win/tldr && \
	tldr --update
	
#RUN mkdir -p /dev/console

#attempt to cache msfconsole stuff and then kill it to make it quicker to run later
RUN /usr/src/metasploit-framework/msfconsole & \
	sleep 30s 

#RUN echo "**** INSTALLING METASPLOIT ****" && \
#	apt-get -y install metasploit-framework

#code below is left as a template for installing a program 
#
#COPY response.varfile /tmp
#COPY --from=downloader /download/burpsuite.sh /tmp/
#RUN \
#	echo "**** install burpsuite ****" && \
#	cd /tmp && \
#	chmod +x burpsuite.sh && \
#	./burpsuite.sh -q -varfile response.varfile && \
#	rm -rf /tmp/*

# add local files
# COPY /root /
# COPY /desktop /config/Desktop

# ports and volumes
EXPOSE 80
# VOLUME /config

CMD ["/bin/sh","-c","while :; do sleep 1; done"]
