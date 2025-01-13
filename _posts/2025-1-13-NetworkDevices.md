---
layout: post
title: Netwrok Devices 🛜
subtitle: How does data travel through air?
excerpt_image: 
categories: Networking 
tags: [CyberSecurity Networking]
---



> Caution : Too many gifs ahead. XD

## Introduction 
<p align='justify'> 
  I'm always found of networking devices and imagining them data flowing around me through those deivces. I'm bad at forming analogies but here I'm trying to make another one 😅.
  Networking is like having your own Avengers team, where each device plays a special role to keep everything running smoothly and securely. 
  The <b>router</b> acts like Iron Man 🤖, connecting all your devices to the internet.
  <b>Servers</b> are like Captain America 🛡️, storing and protecting your important data.
  <b>Firewalls</b> are Thor’s hammer ⚒️, blocking any bad stuff from entering your network.
  <b>VPNs</b> are the Hulk 💪, hiding your identity and keeping your online activities safe.
  <b>Switches</b> are like Spider-Man 🕸️, ensuring all your devices communicate with each other seamlessly.
  Lastly, <b>encryption</b> is Doctor Strange’s magic 🔮, protecting your data and making sure no one can spy on you (we will learn about doctor strange 'in next'). 
  Together, these devices create a powerful network that keeps your internet fast, secure, and ready to tackle anything!
</p>

<a align='center'> ![CivilWarAvengersGIF](https://github.com/user-attachments/assets/46d17ed3-8460-4a0d-8fb0-beb599de8843)</a>

---

## Servers
- Servers is a computer program or device that provides a service to other computer programs and their users, known as clients, over a network.
- A desktop can act like a server, but the limitations of the regular desktop can't handle heavy traffic; it is only designed for single processors, like Core i7, i5, and so on.
- A supercomputer is specially designed for servers, so handling huge data or hosting a service, traffic is not an issue. They are designed to work with multiple processors (like Intel Xeon processors).  
  These use ECC RAM (Error-Correcting Code).
- ECC RAM is mainly used in servers, detecting if the data was correctly processed. (Intel CPUs don't support ECC RAM, but AMD processors do, and Intel Xeon will also support it.)
- A server should also have hot-swappable hard drives and redundant power supplies, having a stable and robust OS.

<a align='center'> ![SparksElectricalElectricityEquipmentRadioAmateurFireGIF](https://github.com/user-attachments/assets/8af3f2da-d3b0-47e9-ad45-35d4d48e522f) </a>


---

## Hub, Switch, Router
- **HUB**: A device with multiple ports that accepts Ethernet connections from network devices (it is not intelligent).
  - Hub does not filter any data or has any intelligence as to where the data is supposed to be sent. It broadcasts the data among all the devices which are connected.
- **Switch**: It has multiple ports and can connect with Ethernet cable connections, and a switch is an intelligent hub.
  - A switch can actually learn the physical addresses of the devices connected to it and store these physical addresses, called MAC addresses.  
    So when a data packet is sent to a switch, it's only directed to the intended destination port.
- To connect with the internet to exchange or route the data outside the network, a device needs to be able to read IP addresses, so hubs and switches can't read that; this is where **Routers** come in.

<a align='center'>![SmallBusinessNetworkSwitchesMarketGIF](https://github.com/user-attachments/assets/bc7b4892-ec43-48fe-8ea3-6781003ac042) </a>


---

## Modem vs Router
- **Modem**: Brings the internet into your home or business. It establishes and maintains a dedicated connection to your ISP to give you access to the internet.
  - Computers only read digital signals, while signals out on the internet are analog. As analog data comes in from the internet, the modem demodulates the incoming analog signals into digital signals so that computers understand, and vice versa.
- **Router**: Comes in after the modem. There are many different types of routers for houses, small, or large businesses.
  - A router is what routes or passes your internet connection to all your devices in your home. It directs data to your phone, computers, tablet, and so on, so those devices can access the internet.
  - Small home/business routers have a built-in switch so that you can connect multiple devices using Ethernet cables, and they also function as a wireless access point so that wireless devices can connect.
- **Conclusion**: Hubs & switches are used to create a network, and routers are used to connect networks.

<a align='center'>![RouterRettrewGIF](https://github.com/user-attachments/assets/9cdc6f11-eabd-4291-a9bc-6077552309b8)</a>



---

## WiFi Router vs Wireless Access Point
- A WiFi router allows multiple wired and wireless devices to join together in a local area network. It broadcasts a WiFi signal so that wireless devices can connect.  
  It also has a built-in switch with several network ports so that wired devices can connect.
- A Wireless Access Point (WAP) relays data between a wired network and wireless devices.  
  It is basically a wireless hub that's used by wireless devices to connect to an existing wired network.
- A wireless AP connects directly to an organization's router, then it connects to the modem. Using WAP instead of WiFi routers is for easy management.
- Routers consist of firewalls and DHCP services but not WAP.
  
<a align='center'>![TiposDeConexionEthernetVsWifiGIF](https://github.com/user-attachments/assets/4169b659-8538-42a6-809d-50960d549865)</a>


---

## WiFi Security
- **WEP (Wireless Equivalent Privacy)**: 1999, meant to provide the same security for wireless networks as wired networks (40-bit encryption key). Easily hackable.
- **WPA (Wi-Fi Protected Access)**: Used TKIP (Temporary Key Integrity Protocol), dynamically changing its keys as they're being used to ensure data integrity. Still, TKIP has vulnerabilities.
- **WPA2**: Uses AES (Advanced Encryption Standard, a symmetric encryption algorithm) strong enough to resist brute force attacks.
- **WPA + WPA2**: This is for compatibility. Older devices prior to 2006 don't support AES, and modern devices connect to WPA2.
- **WPA3**: Introduced in 2018, provides enhanced security.
- **WPS (Wi-Fi Protected Setup)**: Designed to make it as easy as possible for devices to join a secure wireless network (Push button method, WPS client).
- **Access Control**: Blocks/grants access to the network using MAC addresses (Once the MAC address is blocked, it can generate an IP address but can't communicate with other devices/networks).
<a align='center'>![MeshWifiGIF](https://github.com/user-attachments/assets/c2b46ce4-f504-4768-948d-5030cabff99b)</a>


---

## Bluetooth vs WiFi
- Both use radio frequency technologies for wirelessly connecting to electronic devices. Certain devices have both Bluetooth and WiFi functionality.
- **Bluetooth**:
  - Created to eliminate the hassle of dealing with wires and cables.
  - A low-power, wireless technology that uses short-range radio to connect nearby devices.
  - Range: ~30 feet (10 meters).
  - Operates at 2.4 GHz using FHSS (Frequency Hopping Spread Spectrum), making interception difficult.  
  Example: Wireless earphones and speakers.
- **WiFi**:
  - A wireless technology that allows devices to connect to the internet.
  - Commonly accessed via WiFi routers connected to the ISP.
  - Range: 100-300 feet (30-91 meters).
- **Differences**:
  - Bluetooth connects devices; WiFi connects devices to the internet.
  - Bluetooth has slower transfer rates and shorter range, but uses less power than WiFi.

<a align='center'>![BabyHeadphoneGIF](https://github.com/user-attachments/assets/469f6622-2c50-42a4-bd28-379d165b52b1)</a>


---

## Hotspot
- A location where people access the internet wirelessly with mobile devices like laptops, tablets, or smartphones.
- **Public Hotspots**:
  - Connected with WAP or WiFi routers linked to an ISP. These broadcast WiFi signals for nearby connections.
  - Not all are free—some require passwords or payment.
- **Private Hotspots**:
  - Example: Home WiFi or tethering from smartphones.
  - Mobile hotspots are either standalone devices or built into smartphones.
  - Example: Jio Hotspot.
- **Public Hotspot Precautions**:
  - Turn off folder sharing or protect with passwords.
  - Use antivirus programs and firewalls.
  - Install a VPN.

<a align='center'>![TurnItOnKyleBroflovskiGIF](https://github.com/user-attachments/assets/d096b97f-7ff8-40fb-b139-c5e8583c6541)</a>


---

## Firewall
- A system designed to prevent unauthorized access to a private network by filtering incoming internet traffic.
- Purpose: Creates a safety barrier between private and public networks.
- Operates based on rules known as "ACCESS CONTROL LIST," determined by the Network Administrator.
- **Types**:
  - **Host-based Firewall**: Software installed on individual computers.
  - **Network-based Firewall**: A combination of hardware and software operating at the network layer.

<a align='center'>![FirewallBenrob0329GIF](https://github.com/user-attachments/assets/de6b8cef-b9af-4042-8489-5c5effbfeb9a)</a>
<!--- ![SkandaSrikanthGIF](https://github.com/user-attachments/assets/9fa1f37c-4075-40fc-8991-2f592b5d10ae) ---> 


---

## Virtual Private Network (VPN)
- Establishes a secure and reliable connection over an unsecured network (e.g., the internet).
- Protects your online activity and disguises your identity.
- Provides a secure tunnel between two endpoints.

<a align='center'> ![AskingBuddyGIF](https://github.com/user-attachments/assets/abc3876b-17fc-4d48-ba65-fe7556f264cd) </a>


---

## Proxy Server
- Retrieves data from the internet on behalf of users, acting as a middleman.
- **Benefits**:
  - Privacy (hides IP addresses).
  - Speed (uses caching for faster page retrieval).
  - Saves bandwidth and logs activity.
- Limitation: Doesn't encrypt data (hackers can intercept it).

---

## Example (Opening Instagram)
<p>
  When you open Instagram on your phone, your request goes through your WiFi router or mobile network, which sends it to the internet. 
  A DNS server finds Instagram’s address and connects you to their servers. 
  Once connected, Instagram’s servers send the data (like your feed and reels) back to your phone. 
  When you like a reel, your phone sends this action to Instagram’s servers, where it gets saved and updated for others to see. 
  All of this happens in seconds, thanks to networking devices like routers, modems, and servers working together behind the scenes.
</p>

<a align='center'> ![InstagramDoubleTapGIF](https://github.com/user-attachments/assets/8981b60e-110e-4e36-94df-1369e29ef1fc) </a>

---

## Conclusion 
<p align='justify'>
  Networking is a big part of our connected world today, making it easy for devices to talk to each other and share information. 
By learning the basics like servers and routers, and even advanced things like VPNs and firewalls, you can understand how everything works and keep systems safe. 
Technology keeps changing, so staying updated on networking helps you handle new challenges and take advantage of all the opportunities in this digital age.
</p>

---

### In Next

We will how to connect to these devices and what can we do throught these in later blogs (after completion of Bandit series).

<a align='center'> ![CatComputerGIF](https://github.com/user-attachments/assets/98139f35-5620-406a-8d8c-f0a38fa31a9f) </a>

