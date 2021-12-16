## Activity File: Exploring Kibana

* You are a DevOps professional and have set up monitoring for one of your web servers. You are collecting all sorts of web log data and it is your job to review the data regularly to make sure everything is running smoothly. 

* Today, you notice something strange in the logs and you want to take a closer look.

* Your task: Explore the web server logs to see if there's anything unusual. Specifically, you will:

:warning: **Heads Up**: These sample logs are specific to the time you view them. As such, your answers will be different from the answers provided in the solution file. 

---

### Instructions

1. Add the sample web log data to Kibana.

2. Answer the following questions:

    - In the last 7 days, how many unique visitors were located in India? 225

    - In the last 24 hours, of the visitors from China, how many were using Mac OSX? 7

    - In the last 2 days, what percentage of visitors received 404 errors? How about 503 errors?
0% if you look at what the diagram says, but breaking it down one will notice that at certain times 100% of visitors experience a 503 error and it decreases throughout the day but then shoots back up. While at most 30% of users experienced a 404 error within those 2 days.
    
- In the last 7 days, what country produced the majority of the traffic on the website? China
    
- Of the traffic that's coming from that country, what time of day had the highest amount of activity? Hour 13
    
- List all the types of downloaded files that have been identified for the last 7 days, along with a short description of each file type (use Google if you aren't sure about a particular file type).
GZ: a compressed gzip file
CSS:cascading style sheets, is used to customize the HTML elements of a webpage
ZIP: a file that compresses and stores multiple files into one location
DRB: are uncommon files associated with the Dr.Beam software
RPM: red hat package manager files that contain installation package software on Linux OS

3. Now that you have a feel for the data, Let's dive a bit deeper. Look at the chart that shows Unique Visitors Vs. Average Bytes.
     - Locate the time frame in the last 7 days with the most amount of bytes (activity).
12-12-2021 at 21:00 hours has the most amount of activity coming in with an average amount of 10,735 bytes from 3 unique visitors.
     - In your own words, is there anything that seems potentially strange about this activity?
This anomaly can account for an unknown malware or file being deployed by the unique visitor, as there is a higher exchange of bytes between the source and the destination. 

4. Filter the data by this event.
     - What is the timestamp for this event? Dec 12, 2021 @ 21:57:28.552
     - What kind of file was downloaded? RPM File
     - From what country did this activity originate? India 
     - What HTTP response codes were encountered by this visitor?

35.143.166.159 - - [2018-07-30T02:57:28.552Z] "GET /beats/metricbeat/metricbeat-6.3.2-i686.rpm HTTP/1.1" 200 15709 "-" "Mozilla/5.0 (X11; Linux i686) AppleWebKit/534.24 (KHTML, like Gecko) Chrome/11.0.696.50 Safari/534.24"

5. Switch to the Kibana Discover page to see more details about this activity.
     - What is the source IP address of this activity? 35.143.166.159
     - What are the geo coordinates of this activity? { "lat": 43.34121, "lon": -73.6103075 }
     - What OS was the source machine running? Windows 8
     - What is the full URL that was accessed? https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-6.3.2-i686.rpm
     - From what website did the visitor's traffic originate? India

6. Finish your investigation with a short overview of your insights. 

     - What do you think the user was doing? The user is accessing a rpm file over Facebook
     - Was the file they downloaded malicious? If not, what is the file used for? Non-malicious file as they are requesting to get the metric beat file to download it onto the Linux OS 
     - Is there anything that seems suspicious about this activity? Nothing suspicious 
     - Is any of the traffic you inspected potentially outside of compliance guidlines? Nothing out of the ordinary

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.  