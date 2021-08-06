FROM ubuntu

RUN apt-get update -y && \
	apt-get upgrade -y && \
	apt-get install wget openssh-server sudo ca-certificates postfix -y

RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh && \
	chmod 777 script.deb.sh && \
	sudo bash script.deb.sh && \
	apt-get install gitlab-ce

RUN apt update && \
	apt install -y tzdata

EXPOSE 443 80 22

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && \
	sed -i "s/# grafana\['enable'\] = true/grafana['enable'] = false/g" /etc/gitlab/gitlab.rb && \
	sed -i "s/unicorn\['worker_timeout'\] = 60/unicorn\['worker_timeout'\] = 300/g" /etc/gitlab/gitlab.rb && \
	gitlab-ctl reconfigure && \
	tail -f /dev/null

#docker build -t ex03 .
#docker run -it --rm -p 8080:80 -p 8022:22 -p 8443:443 --privileged ex03
