### uncoder
[https://tdm.socprime.com/uncoder-ai/translate](https://tdm.socprime.com/uncoder-ai/translate)

### Pour recupérer le fihcier `savedsearches.conf` :
#### 1️- Sur la VM (`vm_soc`) :
```bash
 sudo docker cp soc_splunk:/opt/splunk/etc/apps/search/local/savedsearches.conf ./savedsearches.conf; sudo chmod +r ./savedsearches.conf 
```
#### 2️- Sur votre machine locale :
```bash
scp user@100.67.56.61:/home/user/savedsearches.conf .
```
