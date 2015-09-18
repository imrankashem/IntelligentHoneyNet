# The Intelligent HoneyNet

*Work in progress*

*Last update, 9/17/2015*
(http://imgur.com/Sfk9Az4)
(http://imgur.com/13V78fz)


Purpose
--------------------
This repository includes a shell script that will install both a honeypot server and any number of honeypots that will communicate with the server.
In addition, there are several python scripts that will automatically process log files generated by various honeypots, adding the information to an Elasticsearch instance and to a Flask page.

Kibana can be configured to show dashboards for all the attack attempts, including a 'threat map', which management loves.

The Flask site, which I'm calling 'Intel' displays useful information, such as:

* Successful SSH connections
* Unsuccessful SSH connections
* Callouts performed by attackers when connected to the SSH honeypot
* Connections to the GasPot honeypot
* Connections to ConPot

The honeynet server scripts use OpenDNS Investigate and Virustotal at the moment to grab information about the IP's connecting in and the domains and IP's contacted by attackers who think they're exploiting a system.

Current Honeypots
--------------------
* Cowrie: SSH Honeypot (it's a fork of Kippo)
* GasPot: Attackers think they're connecting to gas station sensors
* ConPot: SCADA honeypot
* Dionaea: Collects malware

Upcoming
--------------------
Currently being worked on:

* Updating logstash to properly filter conpot and dionaea
* Creating a python script to automatically replay SSH session and gather intel from them
* Adding more honeypots
* The Flask page is kind of ugly. This is being worked on.
* Check malware against malwr.com (not just virustotal)
* The ability to download csv files of all the IP's, domains and other indicators


Requirements:
--------------------
*The server should work on any version of Linux, but it's been tested on Ubuntu Server 12.04
*The client should be installed on Ubuntu Server 12.04 (Dionaea only seems to work on this version)
Once installed, you need to add a virustotal API key to /opt/analysis/virustotal_api_key.txt and an investigate API key to /opt/analysis/investigate_api_key.txt