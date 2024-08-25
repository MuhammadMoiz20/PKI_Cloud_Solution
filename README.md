# PKI Cloud Solution - Moiz and Ramsey
This is our cloud security project for COSC 55 Summer 24. Moiz and I have successfully deployed a one-tier PKI for a small organization hosting two internal webservers. If you're curious, this is what we look like:


<p align="center">
  <img width="200" alt="Screenshot 2024-08-25 at 6 06 52 PM" src="https://github.com/user-attachments/assets/9f119f67-c0c8-477a-99ef-da440e7d452e">  
  <img width="180" alt="Screenshot 2024-08-25 at 6 06 52 PM" src="https://github.com/user-attachments/assets/c39a7907-0aa2-4952-9446-4d7867526a15">   
</p>

### What problem do you solve?
Many organizations are prone to spoofing attacks, where an attacker will make a replica of an existing service or page and pretend to be the real thing. From there the attacker can embed scripts in their fake-site and compromise an organization's security.

### What's your solution?
We provide the organization with an internal Public Key Infrastructure, which is a system to deploy and revoke digital certificates (Learn more about PKI and digital certificates [here](https://www.youtube.com/watch?v=0ctat6RBrFo)). The PKI contains a root Certificate Authority which can sign certificates and distribute them to web servers proving their authentic identity. Thus, an organization can be sure that its webservers belong to it and are communicating securely if the communication they recieve comes with a certificate.

### How does it work?
Our Certificate Authority is an EC2 Ubuntu instance in a secure private subnet that distributes SSL certificates to the organization's EC2 webservers in public subnets (across two availbility zones for reliability). The CA issues certificates to any number of webservers that the organization is hosting internally, and those webservers then manually trust the certificates from the CA. Thus they are able to confirm the identity of webservers within the organization and can trust information gained therein. This way the servers can communicate securely knowing each others identity!

### How can I do it?
Here are some key pages from the Wiki:
* [Here](https://github.com/RamseyW2004/cosc55project/wiki/Functional-PKI-Deployment-Guide) is a guide to deploy the PKI.
* [Here](https://github.com/RamseyW2004/cosc55project/wiki/Functional-Cloud-Deployment-Guide) is a guide to deploy the cloud environment in AWS.
* [Here](https://github.com/RamseyW2004/cosc55project/wiki/System-Deployment-Plan) is an abstract system deployment plan.
* [Here](https://github.com/RamseyW2004/cosc55project/wiki/References) are a list of references we consulted throughout the development of our solution.

### What does it look like?
Here is a diagram of our solution architecture:

![25 PKI cosc55 diagram moiz ramsey drawio](https://github.com/user-attachments/assets/76a3deaa-ded5-4f4f-965e-2a382d9e44d6)

Here is a screenshot of the PKI working successfully, allowing a webserver to recognize another as certified by the organization ("SSL Certificate Verify OK"):

<img width="621" alt="Screenshot 2024-08-25 at 6 04 50 PM" src="https://github.com/user-attachments/assets/c795aa75-263e-4024-9ec7-5832b5b75170">

### If you're a grader...
Please note that this project took far more than 12 hours to complete. Originally, we were hoping to deploy [this stack](https://aws.amazon.com/ar/solutions/implementations/microsoft-pki/) as a base to start from, but after several hours of troubleshooting DNS and elastic IPs we had to abandon this plan. Our Plan B was to deploy a two-tier stack, but after an all-nighter trying to set up certificate chaining we realized the time constraints of this project would not allow us to implement a subordinate CA. After that, we settled on the solution we are now offering, which took another several hours. Be kind!!


