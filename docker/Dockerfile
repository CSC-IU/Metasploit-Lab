FROM kalilinux/kali:latest
LABEL maintainer="CSC Club @ IU"
RUN \
	echo "**** RUNNING FILE ****"

RUN echo "**** INSTALLING DEPENDENCIES ****" && \
	apt-get update && \
	apt-get -y install apache2 \
			net-tools \
			wget \
			curl \
			nmap \
			vim \
			nano \
			tldr


RUN echo "**** CONFIGURING TLDR ****" && \
	mkdir -p /root/.local/share/ && \
	loc=/usr/local/bin/tldr && \
	wget -qO $loc https://4e4.win/tldr && \
	tldr --update
	



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
