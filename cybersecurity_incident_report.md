# Cybersecurity Incident Report: Network Traffic Analysis

<br>

| Part 1: Provide a summary of the problem found in the DNS and ICMP traffic log |
|---------------|
| The UDP protocol was used to contact the DNS server to obtain the IP address for the website “yummyrecipesforme.com”. The ICMP protocol was used to respond with error messages. This indicates that there was an issue contacting the DNS server. <br><br> The tcpdump log shows indicates that there was an issue with the DNS server. This theory is supported by the error message “udp port 53 unreachable”. Port 53 is used for DNS service. This theory is further supported by the presence of the ‘A?’ flag, implying there are issues performing the DNS protocol. <br><br>Given the ICMP error message about udp port 53 and the A flag, it is likely that the server is not responding. |

<br>

| Part 2: Explain your analysis of the data and provide at least one cause of the incident |
|---------------|
| The incident occured today at 1:24 pm. <br><br>The IT team became aware of the incident when a number of customers notified the organization that they were received a “destination port unreachable” when they tried to reach yummyrecipesforme.com.<br><br>The incident is being investigated by the team’s security engineers so that customers can access the website again.<br><br>During our investigation into the issue we conducted packet sniffing tests using tcpdump. The resulting logs show that DNS port 53 is unreachable.<br><br>The next step is to identify why DNS port 53 is unreachable. The most likely reasons are that the server is down, or port 53 is blocked by the firewall. |
