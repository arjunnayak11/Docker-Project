FROM ubuntu:14.04
ENV  path="/srv/www/appsphere/vms" 
ENV  d_path="/home/repo/vms" 


###Install APT Packages ######### 

RUN apt-get update && apt-get install -y python3-setuptools \ 
python3-pip supervisor nginx git mysql-client 

####Install PIP packages############# 

RUN pip3 install django==1.8.4 pymysql gunicorn virtualenv 

###SetUp Project Path##### RUN mkdir -p /srv/www/appsphere 

WORKDIR /srv/www/appsphere 
VOLUME /var/log/vms /var/log/vms 
COPY . /srv/www/appsphere/vms 
#RUN cd $path/deploy && pip install -r requirements.txt 
COPY setup/supervisor_vms.conf /etc/supervisor/conf.d/vmsapp.conf 
COPY setup/nginx_vms.conf /etc/nginx/sites-available/nginx_vms.conf 
RUN mkdir -p /var/log/vms/nginx && \ 
   rm -f /etc/nginx/sites-enabled/default && \ 
   ln -sf /etc/nginx/sites-available/nginx_vms.conf /etc/nginx/sites-enabled/nginx_vms.conf && \   
   update-rc.d -f nginx remove && \ 
   echo "daemon off;" >> /etc/nginx/nginx.conf    


EXPOSE 22 80 8000 
CMD ["/usr/bin/supervisord" ,"-n"]
