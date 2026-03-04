# Log Analysis

```
wc -l for word count


cat vsftpd.log | grep "\[ftpuser\] OK DOWNLOAD" | awk -F ',' '{print $3}'
| awk -F ' ' '{print $1}' | awk '{s+=$1} END{print s}'
6008032
```

