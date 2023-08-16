```bash
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg
#You may need to install the apt-transport-https package on Debian before proceeding
# installing the packages before proceeding
sudo apt-get install apt-transport-https
# Save the repository
echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list
sudo apt-get update && sudo apt-get install elasticsearch
#After executing the above command, elastic superuser password will be prompt on the screen.  Please save the same in a text file, we need this password for further configurations. 
systemctl start elasticsearch.service
systemctl enable elasticsearch.service
#Change your path to tmp directory . Then, execute the curl command
cd /tmp
curl --cacert /etc/elasticsearch/certs/http_ca.crt -u elastic https://localhost:9200
```
### Configuring the Elasticsearch to access it publicly. ###
