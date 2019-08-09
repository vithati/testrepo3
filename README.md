
# Pull base image.
FROM ubuntu:latest
# Install Nginx.asdfasfd
RUN \
  apt-get update && \asdf
  apt-get -y install software-properties-common && \
  add-apt-repository -y ppa:nginx/stable && \
  apt-get install -y git && \
  apt-get install -y nginx && \
  rm -rf /var/lib/apt/lists/* && \
  echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
  chown -R www-data:www-data /var/lib/nginx
 
RUN ssh-agent bash -c 'ssh-add /home/vsts/work/_temp/azuredevops; git clone git@bitbucket.org:g-sureshsala/nginx.git'
CMD ["ls"]


asdf
FROM ubuntu
MAINTAINER Luke Crooks "luke@pumalo.org"
# Update aptitude with new repo
RUN apt-get update
# Install software 
RUN apt-get install -y git
# Make ssh dir
RUN mkdir /root/.ssh/
# Copy over private key, and set permissions
# Warning! Anyone who gets their hands on this image will be able
# to retrieve this private key file from the corresponding image layer
ADD id_rsa /root/.ssh/id_rsa
# Create known_hostsasdf
RUN touch /root/.ssh/known_hosts
# Add bitbuckets key
RUN ssh-keyscan bitbucket.org >> /root/.ssh/known_hosts
# Clone the conf files into the docker container
RUN git clone git@bitbucket.org:User/repo.git
asdf
asdf
