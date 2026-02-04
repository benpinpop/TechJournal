# Wazuh Installation Steps

```sh
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh
curl -sO https://packages.wazuh.com/4.14/config.yml
```

Edit ./config.yml with your files

```sh
bash wazuh-install.sh --generate-config-files
bash wazuh-install.sh --wazuh-indexer node-1
bash wazuh-install.sh --start-cluster
```

Fetch admin password:

```sh
tar -axf wazuh-install-files.tar wazuh-install-files/wazuh-passwords.txt -O | grep -P "\'admin\'" -A 1
```

Verify integrity:

```sh
curl -k -u admin https://<WAZUH_INDEXER_IP_ADDRESS>:9200
```

Install server and dashboard, remove wazuh from package repositories to stop unintended updates

```shellscript
bash wazuh-install.sh --wazuh-server wazuh-1
bash wazuh-install.sh --wazuh-dashboard dashboard

sed -i "s/^deb /#deb /" /etc/apt/sources.list.d/wazuh.list
apt update
```



See: [https://documentation.wazuh.com/current/installation-guide/index.html](https://documentation.wazuh.com/current/installation-guide/index.html)
