# Attack-and-Defense-in-EDR

<h2> Project </h2>
This lab focuses on emulating an authentic cyber intrusion and endpoint detection and response scenario. Drawing from Eric Capuano's online tutorial, I'll employ virtual machines to replicate both the threat and victim environments. The attacking machine will leverage 'Sliver' as a command-and-control (C2) framework to target a Windows endpoint machine, while the latter will run 'LimaCharlie' as its EDR solution.

Eric Capuano's Guide: https://blog.ecapuano.com/p/so-you-want-to-be-a-soc-analyst-intro?utm_campaign=post&utm_medium=web

<h2> Setup </h2>
The initial phase of the lab involves configuring both systems. The attack machine will operate on Ubuntu Server, while the endpoint will run Windows 11. To ensure smooth operation of the lab, Microsoft Defender and other relevant settings should be disabled. Additionally, I'll install Sliver on the Ubuntu machine as the primary attack tool and configure LimaCharlie on the Windows machine as the EDR solution. LimaCharlie will be equipped with a sensor connected to the Windows machine and configured to import sysmon logs.

<h4> Windows Machine </h4>

![264707503-75977c64-7faa-4b38-a5ad-1824cec2e508](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/beb08732-36eb-47b5-9c0f-b5de728260d6)
![264707527-aebc3ac4-3631-4efe-a0f3-fc301997e48e](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/279c13b6-37af-4491-b07c-34dce335716e)
![264708076-d42cbd4d-7732-4f45-9e22-66457d2056ac](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/2d070354-367e-49ff-9aa7-11c4219d8347)
![264708101-ec31655e-ee37-48de-bcf0-ae04c8f5bb06](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/c728f1ce-5c1b-46b4-832c-b94e02cdb66f)
























