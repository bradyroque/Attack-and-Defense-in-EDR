# Attack-and-Defense-in-EDR

<h2> Project </h2>
This lab focuses on emulating an authentic cyber intrusion and endpoint detection and response scenario. Drawing from Eric Capuano's online tutorial, I'll employ virtual machines to replicate both the threat and victim environments. The attacking machine will leverage 'Sliver' as a command-and-control (C2) framework to target a Windows endpoint machine, while the latter will run 'LimaCharlie' as its EDR solution.
<br> </br>
Eric Capuano's Guide: https://blog.ecapuano.com/p/so-you-want-to-be-a-soc-analyst-intro?utm_campaign=post&utm_medium=web

<h2> Setup </h2>
The initial phase of the lab involves configuring both systems. The attack machine will operate on Ubuntu Server, while the endpoint will run Windows 11. To ensure smooth operation of the lab, Microsoft Defender and other relevant settings should be disabled. Additionally, I'll install Sliver on the Ubuntu machine as the primary attack tool and configure LimaCharlie on the Windows machine as the EDR solution. LimaCharlie will be equipped with a sensor connected to the Windows machine and configured to import sysmon logs.

<h4> Windows Machine </h4>

![264707503-75977c64-7faa-4b38-a5ad-1824cec2e508](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/beb08732-36eb-47b5-9c0f-b5de728260d6)
![264707527-aebc3ac4-3631-4efe-a0f3-fc301997e48e](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/279c13b6-37af-4491-b07c-34dce335716e)
![264708076-d42cbd4d-7732-4f45-9e22-66457d2056ac](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/2d070354-367e-49ff-9aa7-11c4219d8347)
![264708101-ec31655e-ee37-48de-bcf0-ae04c8f5bb06](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/c728f1ce-5c1b-46b4-832c-b94e02cdb66f)

<h4> Ubuntu Machine </h4>

![264708323-1ed6cce1-4793-412b-8b8d-d0b65fbc6aa2](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/0b982c70-fd45-4c8c-af8b-8b7045c58cb8)

<h4> The Offenses and the Defensive Strategies </h4>
Initially, we'll craft our payload using Sliver and embed the malware into the Windows host machine. Subsequently, once the malware is executed on the endpoint, we can establish a command and control session.

![264709166-10b13df6-8edd-4f79-bc04-e6fdca12cf68](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/7f099015-e7ae-4928-9c97-7c9ad0ddf6f2)
![264709215-fd752f1f-324c-4d76-93f0-d1db0f6d5120](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/a1d7b138-8c49-4854-b011-e19f1dffdfb1)
![264709305-4e4c15cd-4e6a-42ce-b554-73137e203a1c](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/57444514-8066-4720-9db9-e27fbc5d1ace)

<br> </br>
With an active session established between the two machines, the attack machine can now commence reconnaissance activities, such as assessing privileges, gathering host information, and evaluating the host's security measures.

![264709842-1daf9c90-bab4-4a0c-ac98-5322a58dbc5e](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/f5aa088a-5093-4e7c-a629-bf2ddc7ab8d2)
![264709970-0400c100-5a4b-4ab8-bc73-46f6e7e634a7](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/2066c00b-c628-4be5-97cd-2cf676245d34)

<br> </br>
Within the host machine, we can inspect our LimaCharlie SIEM to observe telemetry data from the attacker. This allows us to pinpoint the running payload and identify the connected IP address.

![264710185-5e6c093c-91f8-4ad3-967c-ad51dcb2e9aa](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/f3333dc4-161d-4713-861d-10ba3be20359)
![264710205-ae55f753-45d1-40c3-905a-3f2d0df716f5](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/5f83cb67-96df-48d3-a985-aac3f1480894)
![264710318-4122902c-702b-4ff6-bebf-98d1d41256d2](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/e7f791fc-a0c3-4ee5-8fd0-d98b931ced67)

<br> </br>
Additionally, LimaCharlie enables us to scan the payload hash via VirusTotal. However, as we've freshly generated the payload ourselves, it will appear clean in the scan results.

![264710644-96a2a29c-08dc-40aa-a40f-09eb9d8500da](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/408c52fe-7f2f-4c51-8e1c-220c43c6de49)
![264710658-f62fdcc2-458a-4929-9527-1ea97f38acb4](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/1634d78e-629d-4176-98c4-fe5d7f44253c)

<br> </br>
Presently, on the attack machine, we can simulate a credential theft attack by extracting LSASS memory. Within LimaCharlie, we can monitor the sensors, analyze telemetry data, and formulate rules to identify the sensitive process.

![264711505-7c420d51-63f2-43ee-9423-6eab89a00910](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/f724c3f3-473c-4847-8a62-4a5cacf5e1a7)
![264711546-b6ca8680-a990-4543-b4ee-55f543e68856](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/400e9b8a-c229-42cd-ac3d-a04f811e0c3e)
![264711553-f7c4bc72-94d9-405c-bb5d-0e10fa505f4c](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/27240e71-db16-412f-aeaf-96ca889e7a09)

<br> </br>
Now, rather than solely focusing on detection, we can leverage LimaCharlie to craft a rule capable of detecting and thwarting attacks originating from the Sliver server. Meanwhile, on the Ubuntu machine, we can simulate aspects of a ransomware attack by targeting the deletion of volume shadow copies. Using LimaCharlie, we can analyze telemetry data and subsequently devise a rule to entirely block such attacks. Once this rule is implemented within our SIEM, any further attempts from the Ubuntu machine to execute the same attack will be rendered ineffective.

![264712455-0e95674a-5ea7-4dd3-a5d9-462f8f93b950](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/211585a8-688b-4534-b442-b92ab1825669)
![264712465-4915d804-7a8e-471c-8d46-e78b13792dce](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/6030e1fb-0fa6-4ecc-8ac8-aaccbf51ce89)
![264712522-67cfa38a-af15-46d2-9773-fbc4086eade5](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/27640179-9cb2-4cc8-8c28-93d32b332932)
![264712563-6c59bd6c-de0f-412c-a116-b1f8923cedef](https://github.com/bradyroque/Attack-and-Defense-in-EDR/assets/166454401/ba486159-51e1-485d-bb25-5c4d45c3e5b6)









