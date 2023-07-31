1) `bin/kibana-encryption-keys.bat generate` or `/usr/share/kibana/bin/kibana-encryption-keys.bat` </br>
2) copy your information</br>
```
xpack.encryptedSavedObjects.encryptionKey: xxxxxxxxxxxxxx
xpack.reporting.encryptionKey: xxxxxxxxxxxxxxxxxx
xpack.security.encryptionKey: xxxxxxxxxxxxxxxxx
```
3) paste in your `kibana.yml`</br>
4) reset `ElasticSearch` and `Kibana`</br>
