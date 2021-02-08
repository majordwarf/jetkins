FROM centos:centos7
LABEL maintainer="tejastank10@gmail.com"

# Update packages and install prerequisites
RUN yum makecache \
    && yum update -y \
    && yum install -y yum-utils

# Setup the nginx repository for YUM to use and install nginx
COPY nginx.repo /etc/yum.repos.d/nginx.repo
RUN yum-config-manager --enable nginx-mainline \
    && yum install -y nginx

# Remove default nginx configurations
RUN rm /etc/nginx/conf.d/default.conf

# Add default configuration
COPY conf/jenkins.conf /etc/nginx/conf.d/jenkins.conf
COPY conf/nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

CMD ["nginx"]
