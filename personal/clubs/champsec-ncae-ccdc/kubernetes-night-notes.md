# Kubernetes Night Notes

### Windows Team

* Lock down windows enviornment
* Help coord inject tasks
* Common Services
  * ADDS, DNS, DHCP, File Services
  * User Management/Group Policy
  * Firewall
  * LDAP: 389
  * Secure LDAP: 636

### Inject Team

* Buisness of Technical Tasks
* Half the points earned
* Incident Response Reporting
* Take a screenshot if you see something
  * Identify steps and remediate issues
* Regain points from Red Team

administrator H3ll0WindwsNight!

contractor Passwording1234!

## Basics

5005 is Master: Controller for all the services, tracks all the workers

5009 is Worker: Responsible for running the services, scaled as large as you need.

Network: Segmented network that keeps track of all connections, scales everything to the CIDR address.

## Priorities

* Managing a pre-deployed Kubernetes cluster
  * Find anomalies in micro and containerized services
  * **Tools: Falco**
  * Manage all the services in the environment.<br>

Service you want everyone to work on, you can run a few things on your cluster, and everything has the service.

## Range Diagram

Range WAN is the DHCP&#x20;

## Key things

Self-Healing: Tries to fix itself and automatically restarts

Load Balancing: Distributes network traffic, load balances itself

Storage Orchestration:&#x20;

Automated Rollouts and Rollbacks: Update applications

## Scenario

Needs a bunch of microservices, hosting nginx

Deploy your own cluster and your services

Run Falco and nginx.

Check for any logs of suspicious activity, record it



Uname: goober

Password: neccdc



kubeadm init --pod-network-cidr=192.168.0.0/16 --cri-socket=unix:///run/cri-dockerd.sock --control-plane-endpoint=192.168.1.102:6443

export PATH=$PATH:/usr/local/sbin

```
kubeadm token create --print-join-command
```

```
    sudo kubeadm join <control-plane-ip>:6443 --token <token> --discovery-token-ca-cert-hash sha256:<hash>

```

&#x20;/var/run/cri-dockerd

Worker: 192.168.1.101

Master: 192.168.1.102



CRI-dockerd.sock - Main socket to run the services on

## Questions

What makes Kubernetes different from Docker?

Manage services
