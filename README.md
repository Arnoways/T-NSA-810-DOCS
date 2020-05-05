|
 |
 |
 |
| --- | --- | --- |

# CIA PROJECT

## REPORT – GROUP N°5

![](RackMultipart20200505-4-180sv6w_html_ca782b55cd67bb6c.png)

| Wilfried RAYNAUD | [wilfried.raynaud@epitech.eu](mailto:wilfried.raynaud@epitech.eu) |
| --- | --- |
| Arnaud SINAYS | [arnaud.sinays@epitech.eu](mailto:arnaud.sinays@epitech.eu) |
| Lucas LEMOIGNE | [lucas.lemoigne@epitech.eu](mailto:lucas.lemoigne@epitech.eu) |

# SUMMARY

1. CIA PROJECT PRESENTATION
  1. INTRODUCTION
  2. CONSTRAINTS
  3. NEEDS AND LENS
2. HOW WE GET FULL ACCESS ON THE INFRASTRUCTURE
  1. INFORMATIONS GIVEN BY THE MANAGER
  2. INFORMATIONS RETRIEVED
3. COMPLETE INVENTORY OF THE INFRASTRUCTURE AT THE BEGINNING
  1. TABLE OF MACHINES RESOURCES
  2. TABLE OF CONTAINERS STATUS BY MACHINES
4. WEB APPLICATION FUNCTIONNAL AGAIN
  1. PREREQUISITES
  2. MODIFICATIONS TO MAKE IT FUNCTIONNAL AGAIN
5. API LOGGING SYSTEM
6. NEXUS SETTED UP TO STORE ALL ARTIFACTS
  1. WHY NEXUS ?
  2. HOW WE STORE ALL ARTIFACTS
  3. HOW ARTIFACTS ARE RETRIEVED FROM NEXUS
7. GITLAB SETTED UP WITH A CI/CD PROCESS LINKED TO NEXUS
  1. HOW THE CI/CD WORKS
8. COMPLETE REPORT OF VULNERABILITIES DETECTED
9. ALL PATCHED VULNERABILITIES
10. ALL UNPATCHED VULNERABILITIES
11. CONCLUSION

# CIA PROJECT PRESENTATION

## INTRODUCTION

We have been recruited to replace the former system administrator and our first mission is to restore the web application. It is not functional and this has paralyzed the inventory department. The company fears a cyber-attack against it in the coming weeks. So we had to take possession of the infrastructure and repair it. Then we had to meet all the needs and objectives provided by the manager.

## CONSTRAINTS

Four constraints to respect:

- API will not be moved to another host
- The web application must not be hosted on the same host as that of the API
- All services must be containerized
- All containers must be launched with the user &quot;service - web&quot;.

## NEEDS AND LENS

We had to make the infrastructure sustainable. For this we had to set up:

- A complete API logging system
- Gitlab with a CI/CD process
- An artifact management software

We also had to fix all the vulnerabilities detected.

# HOW WE GET FULL ACCESS TO THE INFRASTRUCTURE

## INFORMATIONS GIVEN BY THE MANAGER

The website is hosted by four virtual machines:

- The web platform
- The API
- The Database
- The monitoring

The monitoring is managed by Portainer.

Some credentials (login and password) without the corresponding platform.

## INFORMATIONS RETRIEVED

We retrieved some informations:

1. Resources by VM.
2. The (unsecure) root password of all machines: admin
3. All IP addresses (DHCP).
4. Identifying which host is hosting which service: (see above : COMPLETE INVENTORY OF THE INFRASTRUCTURE AT THE BEGINNING)

# COMPLETE INVENTORY OF THE INFRASTRUCTURE AT THE BEGINNING

## TABLE OF MACHINES RESOURCES

| Machine name | IP - DHCP | vCPU | CPU Usage ~ (%) | RAM (GB) | RAM Usage ~ (%) |
| --- | --- | --- | --- | --- | --- |
| Machine-1 | 192.168.1.64 | 2 | 0.2 | 2 | 5 |
| Machine-2 | 192.168.1.61 | 2 | 0.2 | 2 | 5 |
| Machine-3 | 192.168.1.62 | 2 | 0.3 | 2 | 5 |
| Machine-4 | 192.168.1.63 | 2 | 0.8 | 2 | 5 |

##

## TABLE OF LAUNCHED CONTAINERS BY MACHINE

| Machine name | Container name | Port(s) | Status | Image |
| --- | --- | --- | --- | --- |
| Machine-1 | front\_front\_1 | 8080:80 | Up | front\_front |
| m1\_proftpd\_1 | 21:21 | Up | m1\_proftpd |
| m1\_nginx\_1 | 80:80 | Up | m1\_nginx |
| m1\_flatfile\_1 | 80 (exposed) | Up | m1\_flatfile |
| Machine-2 | m2\_server\_1
 | 80 (exposed)222:2280:3000 | Up | m2\_server
 |
| m2\_db\_1 | 3306 (exposed)33060 (exposed) | Up | mysql:5.7 |
| Machine-3 | nostalgic\_ganguly | 80:80 | Up | nagiosxi:5.5.6 |
| dev\_db
 | 3306:330633060 (exposed) | Up | mysql:5.7 |
| Machine-4 | brave\_napier | ??? | Restarting (1) | octobercms:1.0.412 |
| portainer | 8000:80009000:9000 | Up | portainer/portainer |

# WEB APPLICATION FUNCTIONNAL AGAIN

## PREREQUISITES

We saw that the API IP address was incorrect in the web application .env file, so we decided to have a static IP address for each machine to fix this and prevent it from happening again.

New IP addresses:

| Machine name | IP - STATIC |
| --- | --- |
| Machine-1 | 192.168.43.201 |
| Machine-2 | 192.168.43.202 |
| Machine-3 | 192.168.43.203 |
| Machine-4 | 192.168.43.204 |

## MODIFICATIONS TO MAKE IT FUNCTIONNAL AGAIN

So, the web application is on the host named &#39;machine-1&#39; and his configuration is in the directory /home/service-web/front/. But for now, we don&#39;t know where is the API.

After researches, we found a docker-compose.yml file in the directory /home/service-web/back/ of the host named &#39;machine-3&#39; with a wrong configuration. We fixed it, rebuilt the docker image and started the container. At this moment, the API was running but we also had to update the .env file for the front-end to make the web application working again.

# API LOGGING SYSTEM

It already exists: [http://machine-3:3000/swagger-stats/ui](http://machine-3:3000/swagger-stats/ui)

# NEXUS INSTALLED AND CONFIGURED TO STORE ALL ARTIFACTS

## WHY NEXUS ?

Nexus is one of the best Repository Managers with an Open Source version. It will cover all of our needs :

- Hosted Docker Registry
- Proxy for Docker Hub

## HOW WE STORE ALL ARTIFACTS

## HOW ARTIFACTS ARE RETRIEVED FROM NEXUS

# GITLAB SETTED UP WITH A CI/CD PROCESS LINKED TO NEXUS

## HOW THE CI/CD WORKS

# COMPLETE REPORT OF VULNERABILITIES DETECTED

# ALL PATCHED VULNERABILITIES

# ALL UNPATCHED VULNERABILITIES

SPOF

# CONCLUSION
