# Cloud-Support-Labs
A collection of labs for my portfolio as an aspiring Cloud Support Engineer.
## Lab 1 - EC2 Access and Connectivity Troubleshooting (simulated ticket)
### Objective
This lab simulates a real-world Tier 1 support scenario where a small business client reports that their newly launched WordPress website is inaccessible. Acting as a Cloud Support Engineer within an MSP, I investigated and resolved the issue, communicated the outcome to the client, and documented the ticket internally.
### Skills and Tools Used
- AWS EC2
- Security Groups
- AWS Console
- Ticketing Simulation
- Customer Communication
- Cloud Support Workflow

### Steps Taken

1. I recieved the ticket and noted that our client was unable to access their website on the internet. I then communicated to the client I had recieved their ticket and was actively working to solve the issue.
2. I attempted to load the website on the internet using the instances public IP address which was unsuccessful - Blank loading screen.
3. I attempted to ssh in to the instance using a terminal which was successful - confirms the server is live.
4. In EC2 I checked the security group rules for the instance and found there was no inbound rule allowing access from port 80.
5. I added an an inbound rule to the security group allowing access from port 80.
6. I re-attempted to access the website on the internet using the instances public IP address which was successful
7. I contacted the client to inform them the issue was solved and asked them to attempt to connect to the website to confirm they could connect over the internet.
8. I documented root cause, solution and next steps using the ticketing system.

### Ticket Simulation
#### Inbound Ticket
- Ticket ID: 249837
- Submitted by: John Doe
- Client: John's Small Business
- Date/Time: 18/06/2025 - 09:17AM
- Priority: Medium
- Service: Managed Web Hosting

- Subject: Website not loading
- Message: Hi, I tried checking the website this morning and it's giving me a "This site can't be reached" message. I was told the website would be going live today so I'm not sure if it's an issue on my end or yours. Could you please look in to this and get back to me. Thanks, John.

#### Client Response
- Ticket ID: 249837
- Status: Resolved
- Response Type: Public reply

- Subject: Ticket ID: 249837
- Message: Hi, John. Thanks for your patience - I have just checked and updated your server settings and your website should now be loading correctly. The issue was related to one of the network permissions in the cloud setup. I have adjusted the permissions and confirmed the site is now accessible from several devices. There is no action needed from your side. Best regards, Olly.

#### Internal Ticket Documentation
- Ticket ID: 249837
- Status: Resolved
- Resolution Category: Network Configuration
- Assigned Engineer: Olly Walshe
- Ticket Type: Incident - EC2 Network Access

- Client Reported: Website unreachable post launch
- Issue Identified: Security group attached to EC2 Instance did not include inbound rule for HTTP Port 80.
- Steps Taken:
  1. Verfied instance state and IP
  2. Confirmed web server was active via SSH
  3. Analysed security group permissions and found no inbound rule for Port 80.
  4. Edited security group to include:
     - Type: HTTP
     - Port: 80
     - Source: 0.0.0.0/0
  5. Retested access to website via browser and confirmed full functionality.
- Outcome: Website fully reachable at time of closure. Client notified and confirmed resolution.
