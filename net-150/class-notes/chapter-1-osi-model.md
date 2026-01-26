# Chapter 1: OSI Model

## What is the OSI Model

The OSI model describes the **theoretical** best network stack. The OSI model is made up of 7 layers as described below.&#x20;

<table><thead><tr><th width="51" data-type="number">#</th><th>Layer Name</th><th>Description</th><th data-hidden></th></tr></thead><tbody><tr><td>7</td><td>Application</td><td>Handles HTTP/HTTPS requests and higher-level protocols like SMTP. </td><td></td></tr><tr><td>6</td><td>Presentation</td><td>Handles how to interpret the 1s and 0s coming through, like ASCII or UTF-8. </td><td></td></tr><tr><td>5</td><td>Session</td><td>Handles session connections and port management </td><td></td></tr><tr><td>4</td><td>Transport/Transmission</td><td>Handles TCP/UDP connections, splitting data into pieces and ports</td><td></td></tr><tr><td>3</td><td>Network</td><td>Runs on IP addresses, handles routing.</td><td></td></tr><tr><td>2</td><td>Data Link</td><td>Provides MAC addresses, determines type of data, and usually a checksum for error correction.</td><td></td></tr><tr><td>1</td><td>Physical</td><td>The job of the NIC, spitting bits over the network</td><td></td></tr></tbody></table>

## Data Sent in a Request Frame

|                     |                |      |      |          |
| ------------------- | -------------- | ---- | ---- | -------- |
| Destination Address | Source Address | Type | Data | Checksum |

## Limits of IPv4 vs. IPv6

IPv4 only supports 32-bits (4,294,967,295 IP addresses), meaning that we have run out of IP addresses. IPv6 is 128-bits, meaning it supports 2<sup>128</sup> addresses.<br>
