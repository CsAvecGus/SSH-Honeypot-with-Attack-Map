# SSH Honeypot with Attack Map

<h2>Description</h2> 

This project demonstrates the deployment of an SSH honeypot to simulate real-world brute-force login attempts, capture attacker metadata, and visualize the attacks on an interactive map.

The goal was to showcase log collection, geolocation, and security event visualization of attackers on a live basis using a remote EC2 instance deployed with Cowrie. The honeypot recorded failed SSH login attempts, including source IP addresses, attempted usernames/passwords, and timestamps. These logs were then parsed with Python, geolocated using a public IP intelligence API, and visualized on a world map using the Folium library.

<h2>Technologies</h2> 

- <b>Kali Linux</b>
- <b>Cowrie</b>
- <b>AWS EC2</b>
- <b>Python</b>
- <b>Folium / Leaflet.js</b>
- <b>IP-API.com</b>
- <b>FireFox</b>

<h2>Overview</h2>

Configuration of AWS EC2 Instance with AMI, Network and Security settings<br/>
<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/c8b22250-bdc1-4aa5-9586-2cdc4becf5f3" /></td>
    <td><img src="https://github.com/user-attachments/assets/2814cdc8-5b7a-4b9b-999c-6160f8722baf" /></td>
  </tr>
</table>
<br/>
<br/>

The EC2 instance is accessed via SSH with Kali, Cowrie is cloned from Github
A virtual environment is created within the instance and Python package manager (pip) is updated
<img width="774" height="281" src="https://github.com/user-attachments/assets/1e26d7a1-b040-47c0-a0a1-9d22d044571d" />
<br/>
<br/>

Cowrie is configured to listen on port 2222, allowing it to capture attempted SSH logins and generate log files for analysis <br/>
<img width="552" height="269" src="https://github.com/user-attachments/assets/3c458a02-e68e-49b3-9840-a2a9686ee98e" />
<br/>
<br/>

The Honeypot service is successfully started within the instance and port 2222 is listening for traffic
<img width="774" height="281" src="https://github.com/user-attachments/assets/c189f888-232c-41e1-9ecc-a364a5e3f9b6" />
<br/>
<br/>

After some time, Cowrie has saved attempted logins from 3 different IP addresses into a JSON file
<img width="833" height="56" src="https://github.com/user-attachments/assets/0d40fad2-b498-4e13-a4a6-19552fd49aff" />
<img width="832" height="55" src="https://github.com/user-attachments/assets/2726e771-0a0c-4d56-b50a-a6d0f515b995" />
<img width="841" height="47" src="https://github.com/user-attachments/assets/a9ad8bd3-f377-4ce8-92e3-d3ced0d3ec8d" />
<br/>
<br/>

We can develop a Python script to take SSH logs from the JSON file to plot and record them geographically
<img width="731" height="785" src="https://github.com/user-attachments/assets/8bd86d46-78e2-4728-b1be-cebfd289c5fd" />
<br/>
<br/>

Our python file is ran in Kali to generate a HTML where we can view this information in FireFox
<img width="848" height="81" src="https://github.com/user-attachments/assets/b3515970-9b94-4d47-a2ab-465fec6a4a33" />
<img width="303" height="45" src="https://github.com/user-attachments/assets/f022a34e-a4b4-4b43-856d-64a98a07c33f" />
<br/>
<br/>

Finally, our attempted logons are visualised on an interactive map
<img width="1681" height="805" src="https://github.com/user-attachments/assets/257f5229-2a2e-4013-bf15-7cce3ae2820c" />
<br/>
<br/>

Upon clicking on a marker, we can see detailed information relating to the source IP, the attempted username, a timestamp of the attack and an approximate source location
<img width="813" height="606" src="https://github.com/user-attachments/assets/0bd592ae-7551-4620-9d6a-05fc5509ad4b" />
<br/>
<br/>
