
# Pull base image.
FROM ubuntu:latest
# Install Nginx.
RUN \
  apt-get update && \
  apt-get -y install software-properties-common && \
  add-apt-repository -y ppa:nginx/stable && \
  apt-get install -y git && \
  apt-get install -y nginx && \
  rm -rf /var/lib/apt/lists/* && \
  echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
  chown -R www-data:www-data /var/lib/nginx
 
RUN ssh-agent bash -c 'ssh-add /home/vsts/work/_temp/azuredevops; git clone git@bitbucket.org:g-sureshsala/nginx.git'
CMD ["ls"]
