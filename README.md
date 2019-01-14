# docker-letsencrypt-nginx-proxy-wordpress

#voir la date de fin du certificat
openssl x509 -in monDomaine.crt -enddate

#droits WPress
pour les plugins j'ai passé chmod 777 sur le hôte 
chmod 777 -R /var/docker/wpress

