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
[Configuring the Elasticsearch to access it publicly.](https://github.com/engkasra/ELK/blob/main/elasticsearch%20yml.txt)
```bash
#Installing Kibana
sudo apt-get update && sudo apt-get install kibana
systemctl start kibana.service
systemctl enable kibana.service
```
[Configure the Kibana](https://github.com/engkasra/ELK/blob/main/kibana%20yml.txt)
</br>
* You can then generate an enrollment token for Kibana with the `elasticsearch-create-enrollment-token` tool.
* Navigate to the directory where you installed Elasticsearch and run the elasticsearch-create-enrollment-token tool to generate an enrollment token.
```bash
cd /usr/share/elasticsearch
bin/elasticsearch-create-enrollment-token -s kibana
```
* Copy the generated token and paste it into the browser and  click configure elastic button.
* After Kibana will prompt for Verification code.
* To generate Verification code , navigate to Kibana installation directory and execute the following script.
```bash
cd /usr/share/kibana
bin/kibana-verification-code
```
