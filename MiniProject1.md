# Finding Suspicious IPs and Identifying Hostnames in Wireshark
Short Wireshark Project, designed to get you hands-on experience in an easy/digestable format.

1. Introduction

● Objective: Learn how to identify suspicious IP addresses using Wireshark's
Conversations window and figure out how to use different protocols to
identify hostnames.
● Pre-Requisites: Please ensure you have downloaded Wireshark x64
(windows) and you are able to open it successfully.

2. Step-by-Step Breakdown

Step 1: Analyzing the Packet Capture with Wireshark
● Download the exercise packet exercise 2025-01-22 from
https://www.malware-traffic-analysis.net/2025/01/22/index.html
● The packet will come in a zip folder, please be sure to extract the contents
of it in a folder labled “PCAP Files” in the initial directory of your C: Drive.
This will make it very easy to find the packet later.

● Open the packet capture ( exercise 2025-01-22) in Wireshark.
● Packet captures provide us with real-time network data,
which helps us identify patterns and possible threats.

1. Open the packet capture in Wireshark.
2. Go to Statistics > Conversations to see a summary of all the
conversations (communications) between IP addresses. This will
show you which IPs are communicating with each other.
3. Look for suspicious behavior: You might spot repeated
communication from a single IP or unusual traffic patterns. We can
often identify an attacker by looking at this behavior.

4. In this specific case, let’s sort by the IPV4 tab at the top of the
Conversations window, then we can order the IPs by descending
number of packets by clicking on the packets tab once or twice. This
is what’s really going to show us which IP is communicating the
most, and by what amount.

Step 2: Using the Conversations Window to Find Suspicious IPs
● Look at the IPs listed in the Conversations window.
● The Conversations window shows us all the interactions
between devices on the network, allowing us to spot outliers or
irregularities.
● What to look for:
1. Look for IPs with high amounts of communication or frequent
requests.
2. If you see a single IP with a disproportionate amount of traffic, that
might be suspicious.
3. Sort by columns like Packets or Bytes to see which IPs are
generating the most traffic. An unusually high amount of traffic could
indicate something malicious, such as a compromised device or a
DDoS attack.

Step 3: Understanding the Importance of Conversations Window
● The Conversations window gives us an overview of all the
communication happening in a network. This can help us quickly identify
anomalies (like strange IP communication patterns or unexpected traffic
spikes), which are often indicators of suspicious activity.
○ Suspicious IPs often show up as having abnormal levels of
communication, so the Conversations window helps us filter out the
noise and focus on the most suspicious interactions.
○ In this case, our suspicious IP is 10.1.17.215.

Step 4: Identifying Hostnames Using Protocols

Protocols

● Think of a protocol like a set of rules or instructions for how devices
communicate with each other over a network. Just like in a conversation
where we follow certain rules (like taking turns and understanding each
other's language), computers and devices follow protocols to exchange
data smoothly and correctly.
● They ensure smooth, secure, and organized communication between
devices. In cybersecurity, understanding protocols helps you spot
problems or vulnerabilities in the communication process, and it's
essential for identifying suspicious activities or attacks like
man-in-the-middle attacks or DNS spoofing.

In the second half of the mini-project, we’re going to identify the hostname of this
suspicious IP via different protocol types.

● Protocols that help identify hostnames:
○ DNS (Domain Name System): DNS queries and responses can reveal
the hostnames of devices, since DNS translates domain names to IP
addresses.
■ Look for packets containing DNS request and response (e.g.,
queries for or ).

○ LLMNR (Link-Local Multicast Name Resolution): If a device can’t
resolve a hostname through DNS, it might try LLMNR to resolve
names locally.
○ NetBIOS: This protocol is often used on Windows networks and can
expose hostnames as part of the communication (via NetBIOS Name
Service).

○ mDNS (Multicast DNS): Similar to LLMNR, mDNS is used in local
networks, especially for devices like printers, IoT devices, etc.
● Why it matters: Knowing the protocols that reveal hostnames can help us
trace the identity of devices on the network. This is key for spotting
malicious devices or compromised systems.

Step 5: How to Use These Protocols in Wireshark

Go ahead and close the Conversations window and go back to the main display.
At the top of the packets you’ll see there is a “Filters” bar to filter out what part of
the traffic you want to see. Since this is a beginner friendly project, we won’t go
too deep into filters, but please note that there are very specific (and very helpful)
ways to use the filters bar. ● Look for DNS requests:

1. Use the filter in Wireshark to find DNS queries and responses.
2. Click on the some of the packets in where the source IP is the
suspicious one we found earlier
3. Look for “A records” (which map hostnames to IP addresses) and
“PTR records” (which map IPs to hostnames) on the right side of the
main packet window.

In this specific instance, we can see that there are multiple hostnames associated
to that IP, so we will have to find another way to find the real hostname.

● Look for LLMNR traffic:
1. Use the filters to catch LLMNR name resolution packets.
2. These packets can show you the names of devices on the network.
3. Now we can see there are only 6 packets displayed, all of which have
the same hostname, and 4 of them are directly involved with our
suspicious IP address.

3. Summary

● Identifying unusual IPs or traffic spikes can
help detect malicious behavior or a compromised device on the network.
By using Wireshark's Conversations window, we can easily pinpoint these
outliers and investigate further.

● Knowing which protocols provide hostnames
(like DNS, LLMNR, NetBIOS, mDNS) helps us identify the devices
associated with suspicious IPs, allowing us to better assess whether the
device is legitimate or malicious.

4. Next Steps (If You Want To Know More)
I highly recommend going over to TryHackMe and going into their
Wireshark rooms. They have been incredibly helpful in understanding the
basics of Wireshark and how to navigate through the application.
Some of the THM modules can get a little rough at times, so don’t be afraid
to look-up the THM walkthroughs on Medium when you’ve started to
become frustrated with some of the problems/exercises.
If you feel comfortable enough to tackle the exercise from the
malware-traffic-analysis website, feel free! It can be quite difficult for
those brand-new to wireshark.

5. Project Conclusion

You’ve learned how to use Wireshark’s Conversations window to identify
suspicious IPs, and you’ve explored useful protocols to uncover hostnames
associated with network devices. This is a very simple and basic exercise
designed to get beginners with hands-on experience using this application.
As a beginner myself, I understand cybersecurity can be daunting, so the more
real world experience we can expose ourselves to, the better we get, and the 
more confident we are in our foundational knowledge.
