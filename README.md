# Analyze Network Layer Communication

This exercise is part of the '**Connect and Protect: Networks and Network Security**' module in the '<a href="https://www.coursera.org/google-certificates/cybersecurity-certificate?network=g&utm_source=gg&creativeid=693701665321&matchtype=p&adgroupid=165119487572&gclid=Cj0KCQjwqdqvBhCPARIsANrmZhNXAt_8j18BwKrshjpWbrgJpCQfqPhGyrrYAAGAKKxGWwPNNPP4HwYaAoWqEALw_wcB&keyword=google%20cybersecurity%20professional%20certificate&utm_content=B2C&hide_mobile_promo=&utm_campaign=B2C_APAC_Google_FTCOF_Cybersecurity_Google_Professional_Certificate_ArtE_Set_2_Mar_24&campaignid=21105066676&gad_source=1&devicemodel=&adpostion=&utm_medium=sem&device=c&redirected_from_description_page=true">Google Cybersecurity Professional Certificate</a>', and the purpose of this exercise is to analyze a tcpdump log.

<br>

In the internet layer of the TCP/IP model, the IP formats data packets into IP datagrams. The information provided in the datagram of an IP packet can provide security analysts with insight into suspicious data packets in transit.

## Task

The purpose of this activity is to analyze DNS and ICMP traffic in transit using data from a network protocol analyzer tool, and identify which network protocol was utilized in assessment of the cybersecurity incident. 

## Scenario

Review the scenario below. Then complete the step-by-step instructions.

You are a cybersecurity analyst working at a company that specializes in providing IT services for clients. Several customers of clients reported that they were not able to access the client company website www.yummyrecipesforme.com, and saw the error “destination port unreachable” after waiting for the page to load. 

You are tasked with analyzing the situation and determining which network protocol was affected during this incident. To start, you attempt to visit the website and you also receive the error “destination port unreachable.” To troubleshoot the issue, you load your network analyzer tool, tcpdump, and attempt to load the webpage again. To load the webpage, your browser sends a query to a DNS server via the UDP protocol to retrieve the IP address for the website's domain name; this is part of the DNS protocol. Your browser then uses this IP address as the destination IP for sending an HTTPS request to the web server to display the webpage  The analyzer shows that when you send UDP packets to the DNS server, you receive ICMP packets containing the error message: “udp port 53 unreachable.” 

![tcpdump_log](https://github.com/andrewrodgers90/analyze_network_layer_communication/blob/main/tcpdump_log.png)

In the tcpdump log, you find the following information:

1. The first two lines of the log file show the initial outgoing request from your computer to the DNS server requesting the IP address of yummyrecipesforme.com. This request is sent in a UDP packet.

2. The third and fourth lines of the log show the response to your UDP packet. In this case, the ICMP 203.0.113.2 line is the start of the error message indicating that the UDP packet was undeliverable to port 53 of the DNS server.

3. In front of each request and response, you find timestamps that indicate when the incident happened. In the log, this is the first sequence of numbers displayed: 13:24:32.192571. This means the time is 1:24 p.m., 32.192571 seconds.

4. After the timestamps, you will find the source and destination IP addresses. In the first line, where the UDP packet travels from your browser to the DNS server, this information is displayed as: 192.51.100.15 > 203.0.113.2.domain. The IP address to the left of the greater than (>) symbol is the source address, which in this example is your computer’s IP address. The IP address to the right of the greater than (>) symbol is the destination IP address. In this case, it is the IP address for the DNS server: 203.0.113.2.domain. For the ICMP error response, the source address is 203.0.113.2 and the destination is your computers IP address 192.51.100.15.

5. After the source and destination IP addresses, there can be a number of additional details like the protocol, port number of the source, and flags. In the first line of the error log, the query identification number appears as: 35084. The plus sign after the query identification number indicates there are flags associated with the UDP message. The "A?" indicates a flag associated with the DNS request for an A record, where an A record maps a domain name to an IP address. The third line displays the protocol of he response message to the browser: "ICMP," which is followed by an ICMP error message

6. The error message, "udp port 53 unreachable" is mentioned in the last line. Port 53 is a port for DNS service. The word "unreachable" in the message indicates the UDP message requesting an IP address for the domain "www.yummyrecipesforme.com" did not go through to the DNS server because no service was listening on the receiving DNS port.

7. The remaining lines in the log indicate that ICMP packets were sent two more times, but the same delivery error was received both times.

Now that you have captured data packets using a network analyzer tool, it is your job to identify which network protocol and service were impacted by this incident. Then, you will need to write a follow-up report. 

As an analyst, you can inspect network traffic and network data to determine what is causing network-related issues during cybersecurity incidents. Later in this course, you will demonstrate how to manage and resolve incidents. For now, you only need to analyze the situation. 

This event, in the meantime, is being handled by security engineers after you and other analysts have reported the issue to your direct supervisor. 

## Step 1: Provide a summary of the problem found in the tcpdump log

After analyzing the data presented to you from the tcpdump log, identify trends in the data. Assess which protocol is producing the error message from the DNS server for the yummyrecipesforme.com website. Recall that one of the ports that is displayed repeatedly is port 53, commonly used for DNS. In your analysis:  

+ Include a brief summary of the tcpdump log analysis and identify which protocols were used for the network traffic.
+ Provide a few details about what was indicated in the log.
+ Interpret the issues found in the log.
+ Record your responses in part one of the <a href="https://github.com/andrewrodgers90/analyze_network_layer_communication/blob/main/cybersecurity_incident_report.md">cybersecurity incident report</a>.  

## Step 2: Explain your analysis of the data and provide one solution to implement 

Now that you’ve inspected the traffic log and identified trends in the traffic, describe why the error messages appeared on the log. Use your answer in the previous step and the scenario to identify the reason behind the ICMP error messages. The error messages indicate that there is an issue with a specific port. What do the different protocols involved in the log reveal about the incident? In your response:

+ State when the problem was first reported.
+ Provide the scenario, events, and symptoms identified when the event was first reported.
+ Explain the current status of the issue.  
+ Describe the information discovered while investigating the issue up to this point.
+ List the next steps in troubleshooting and resolving the issue.
+ Provide the suspected root cause of the problem.
+ Record your responses in part two of the <a href="https://github.com/andrewrodgers90/analyze_network_layer_communication/blob/main/cybersecurity_incident_report.md">cybersecurity incident report</a>. 
