# updox_challenge2
Updox Challenge 2 - Site firewall rules

Given the following assumptions regarding a network architecture, plus any assumptions of your own, identify the ideal locations of firewalls (physical or virtual) and write a set of rules for each. The rules can be implemented in pseudo code, iptables or ufw. To simplify, substitute names for IP addresses, ranges, and VLANs (ie: db_cluster, wiki_server, web_group).

Assume the following:
  * All sites
    * Two OpenVPN networks exist: an office VPN for all employees, as well as an admin VPN for the ops team
    * The 3 sites are connected via IPSec tunnels over the internet
    * All hosts should be able to:
      * Send logs to a log aggregation server in the data center
      * Receive health checks from a monitoring server in the data center on port 6556

  * HQ
    * Wifi guest network should have internet access only
    * VoIP phone system should be accessible from the internet
    * Remote employees should be able to connect to the office VPN from the internet

  * Data center
    * The data center hosts a web application with a standard 3-tier architecture (web, app, data)
    * A group of load balancers terminate SSL and then forward requests to a group of web servers
    * The log aggregation and monitoring servers mentioned above live here, as well as a SMB file server which should be accessible by all employees

  * AWS
    * One VPC exists in AWS and it is a replica of the data center
    * AWS is used as a hot standby