# PKI Cloud Solution - Moiz and Ramsey
This is our cloud security project for COSC 55 Summer 24. Moiz and I have successfully deployed a one-tier PKI for a small organization hosting two internal webservers. 

Our Certificate Authority is an EC2 Ubuntu instance in a private subnet that distributes SSL certificates to the organization's EC2 webservers in public subnets across two availbility zones. The CA issues certificates to any number of webservers that the organization is hosting internally, and those webservers then manually trust the certificates from the CA. Thus they are able to confirm the identity of webservers within the organization and can trust information gained therein, and can comunicate securely.

Key pages from the Wiki:
* [Here](https://github.com/RamseyW2004/cosc55project/wiki/Functional-PKI-Deployment-Guide) is a guide to deploy the PKI.
* [Here](https://github.com/RamseyW2004/cosc55project/wiki/Functional-Cloud-Deployment-Guide) is a guide to deploy the cloud environment in AWS.
* [Here](https://github.com/RamseyW2004/cosc55project/wiki/System-Deployment-Plan) is an abstract system deployment plan.
* [Here](https://github.com/RamseyW2004/cosc55project/wiki/References) are a list of references we consulted throughout the development of our solution.




Here is a diagram of our solution architecture:

![25 PKI cosc55 diagram moiz ramsey drawio](https://github.com/user-attachments/assets/76a3deaa-ded5-4f4f-965e-2a382d9e44d6)




