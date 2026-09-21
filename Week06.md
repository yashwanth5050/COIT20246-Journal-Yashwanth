# Week 6 Journal – Internet Applications

**Student Name:** Yashwanth. **GitHub:** https://github.com/yashwanth5050. **Unit:** COIT20246 Networking and Cyber Security. **Week:** 6. **Topic:** Internet Applications.

## Activity 1 – Creating a Web Page in OpenWRT

### Objective

This activity aims to tweak the web content served through the OpenWRT Linux server and begin to see how HTML, CSS and JavaScript interact in the creation of a simple web application.

### Work Completed

The OpenWRT web server was located on 192.168.56.2 with an address of http://192.168.56.2/ and the files for the web server were stored in /srv/www. I navigated to that directory and looked at the files there and copied index.html to make a second HTML file, named after my student ID. Thereafter, I adjusted index.html to reference to the new page.

But it had my identifying data, referenced a file for my style sheet and had java script that after pushing a button would display the current date and time on the newly created page. I wrote mystyle.css and set it up to manipulate selected text. Three main commands were used during this work: cd /srv/www, ls, and cp index.html and then the student-ID-based name of a file, and then nano and then the name of a file to be edited.

### Interpretation

This activity demonstrated the various functions of the key browser technologies. HTML contains the structure and contents of the page, CSS governs the presentation of it and JavaScript is able to manipulate the content after the page has been loaded in the browser.

## Activity 2 – Capturing HTTP Packets

### Objective

In this activity, we are going to intercept traffic during web surfing to the OpenWRT pages, and then analyze the HTTP & TCP activity.

### Work Completed

On OpenWRT I moved back to the home directory and began a tcpdump on the interface eth0, excluding SSH traffic on TCP port 22. My student ID was used to generate the file name for the capture. I then opened a private browser window and went to http://192.168.56.2/, clicked on the link for student page and pressed the date-and-time button twice. Then I came back to OpenWRT and stopped the capture by Ctrl^C.

I had to create traffic between windows and OpenWRT server and view the Windows ARP table with arp – a. This is how I was able to help tie in application traffic with local AR.

In this activity, you will explore the contents of the .pcap file.For this activity, explore the contents of the .pcap file.

### Objective

The idea behind this activity was to find the requests and responses, plus the connection setups of the web browsing activity.

### HTTP Requests and Responses

Initially when I went to http://192.168.56.2/, Web browser asks for the default page of the server and server responds with successful response including the HTML. A click of the link to the student web page provoked another HTTP download of a second HTML file. The page referenced an external stylesheet which also resulted in mystyle.css being requested. Hence, a request for the root resource, followed by a request to get the stylesheet and to get the student page was made, and all three requests were successful with a corresponding HTTP response from the server.

The source IP address, destination IP address, transport protocol, source port and destination port is used to identify the first web flow. In this environment, the Windows host uses 192.168.56.1 and the OpenWRT server uses 192.168.56.2. TCP is the transport protocol and destination port number 80 identifies the HTTP service. Client source port: An ephemeral port that the operating system chooses for the connection.

By using client side java script for the pressing of date-and-time button, another request to the Web-server was not necessary. The necessary code was already downloaded along with the Web page and the browser was capable of performing the computation and displaying date and times as local times.

With only a click from the OpenWRT main-page (http://192.168.56.2/), it shows the Referer which is that page from where you navigated. The origin of the referrer information can be used to gain information about how they got to a specific resource and can be used for navigation paths on web servers.

The User-Agent is used to inform about browser and operating environment. This information can help a server adapt content, troubleshoot compatibility problems or perform usage analysis. The communication over the web is based on the HTTP protocol, which is transmitted via the TCP protocol, that is, connection oriented and reliable.

TCP makes three-way handshake using SYN, SYN-ACK and ACK before it starts HTTP data transfer. Once connected, acknowledgements are sent to acknowledge that transmitted sequence data is received. TCP can only send cumulative ACKs, and can even send delayed ACKs, depending on the implementation and traffic pattern.

Activity 4: Viewing Browser Cookies

### Objective

The goal of this activity was to verify the kind of information that is stored in a cookie, without revealing private cookie values.

### Work Completed

As part of my research, I examined cookies set by a site that I visited on a regular basis using the developer tools of my web browser. The cookie name, domain and path were stored as well as expiry details, security flags and a value. Elementary pieces of information that can be conveyed through a cookie are, for example, session identifiers (to maintain a user's session), preference information (dynamic setting of the language or graphical interface of a website), analytic information (statistics of site use), consent information (to receive the applications the user has requested), security information (for security operations within the application).

I didn't post real cookie values as cookie values may be sensitive and you may have a real session.

### Interpretation

The activity demonstrated a need for information in web applications which is not displayed in the browser window. Cookies have been a big part of "session and preference information," which aids a stateless protocol in maintaining information between requests, but also impose privacy and security obligations.

## Problems and Troubleshooting

Separating activities that generated network traffic from activities within the browser was the big one. It was easier to filter the capture for HTTP to identify application requests and it was necessary to view the full capture to understand the TCP connection establishment and acknowledgement.

## Weekly Reflection

Week 6 was dealing with the very basics of web development as well as packet analysis. Comparing the HTML + CSS to the contents of the screen revealed the user interface, whereas a dump of the network exchanges from the application (tcpdump or Wireshark) revealed network exchanges that supported the page's contents.

The most helpful clue: Clicking a JavaScript date-time button doesn't necessarily trigger another HTTP request. Also learned how the way TCP connection is set up provides additional information when dealing with HTTP and how fields like Referer and User-Agent provide useful information about navigation and client software.