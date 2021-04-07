FROM lsiobase/rdesktop-web:bionic

RUN \
	echo "**** install packages ****" && \
	apt-get update && \
	DEBIAN_FRONTEND=noninteractive \
	apt-get install --no-install-recommends -y \
		firefox \
		libnss3 \
		pavucontrol \
		terminator \
		xfce4 \
		xfce4-goodies \
		xubuntu-default-settings \
		xubuntu-icon-theme && \
	echo "**** cleanup ****" && \
	apt-get clean && \
	rm -rf \
		/tmp/* \
		/var/lib/apt/lists/* \
		/var/tmp/*

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
COPY /root /
COPY /desktop /config/Desktop

# ports and volumes
EXPOSE 3000
VOLUME /config
