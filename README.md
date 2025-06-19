# Cloud-Support-Labs
A collection of labs for my portfolio as an aspiring Cloud Support Engineer.
## Lab 1 - EC2 Access and Connectivity Troubleshooting (simulated ticket)
### Objective
Simulate a 1st line support ticket where a client of the MSP I work at as a Cloud Support Engineer is reporting an issue with accessing their Wordpress website that has recently been laucnhed in EC2.
I will take ownership of the ticket, investigate and solve the issue, communicate with the client and record my works in the ticketing system.
Ticket: 
### Steps Taken
1. I recieved the ticket and noted that our client can not access their website on the internet. I then communicated to the client I had recieved their ticket and was actively working to solve the issue.
2. I attempted to load the website on the internet using the instances public IP address which was unsuccessful - Blank loading screen.
3. I attempted to ssh in to the instance using a terminal which was successful - confirms the server is live.
4. In EC2 I checked the security group rules for the instance and found there was no inbound rule allowing access from port 80.
5. I added an an inbound rule to the security group allowing access from port 80.
6. I re-attempted to access the website on the internet using the instances public IP address which was successful
7. I contacted the client to inform them the issue was solved and asked them to attempt to connect to the website to confirm they could connect over the internet.
8. I documented root cause, solution and next steps using the ticketing system.
### Ticket Simulation
Inbound Ticket
