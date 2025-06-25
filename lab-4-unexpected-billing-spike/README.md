## Lab 4 - Unextpected AWS Billing Spike

### Objective
Simulate a real-world MSP support ticket in which a client reports an unexpected AWS billing spike. Act as a Cloud Support Engineer tasked with investigating the root cause, communicating with the client, resolving the issue, and implementing preventative measures such as billing alarms.

### Steps Taken
1. Assumed delegated SupportEngineer role in clients AWS account
2. Opened the Billing and Cost Management Dashboard and launched Cost Explorer
3. Identified a significant increase in EC2 usage during the current billing cycle
4. Investigated running EC2 Instances and found a recently created m5.24xlarge instance that had been running for 72 hours - Estimated cost $288
5. Contacted the client to confirm whether the instance was intentionally running - confirmed it was created for testing purposes and left running my mistake
6. Proceeded to terminate the instance
7. Checked for any active billing alerts and found they were disabled - enabled billing alerts
8. Created a CloudWatch Billing Alarm for EstimatedCharges, greater than 200USD with a new SNS topic subscribed to client's admin email
9. Contacted client to confirm that the cause of the billing spike was found and resolved and projected spend for the billing period was back to within a normal range
10. Walked client through subscribing to the alarm and explained how the alarm will work
11. Documented all findings, actions and reccomendations in internal ticketing system

### Ticketing Simulation
#### Inbound Ticket
- Ticket ID: 190699
- Submitted by: Neil Foster
- Client Company: Simplix Ltd
- Date/Time: 24/06/2025 – 08:14AM
- Priority: High
- Service: AWS Billing & Cloud Monitoring

- Subject: Unexpected AWS bill – can you investigate?
- Message: Hi, We’ve just received a notification from AWS that our spend this month is already over £350 — which is a big jump from our usual £100–£150. We haven’t launched anything new this month. Could you please take a look and let us know what’s causing the increase? If there’s something that shouldn’t be running, can you shut it down or advise us? Thanks, Neil.

#### Client Response
- Ticket ID: 190699
- Status: Resolved
- Response Type: Public Reply
- Date/Time: 25/06/2025 – 10:12AM

- Subject: Ticket ID: 190699
- Message: Hi Neil, Thanks for flagging this. I’ve reviewed your AWS billing and usage data and found that the increase in charges this month is due to a large EC2 instance (m5.24xlarge) running in the London region. It’s been active for several days and has contributed approximately $288 to your bill. I wanted to confirm whether this instance was intentionally running. If not, I can go ahead and terminate it to prevent further charges. I also noticed that billing alerts weren’t currently configured in your account. I've now enabled them and created a CloudWatch alarm that will notify you by email if your estimated monthly spend exceeds £200. Please confirm you're happy with this setup and let me know if you'd like me to assist with additional cost control options like AWS Budgets or automated cleanup policies for non-production resources. Best regards, Olly Walshe.

### Internal Ticket Documentation
- Ticket ID: 190699
- Status: Resolved
- Resolution Category: Cost Anomaly – EC2
- Assigned Engineer: Olly Walshe
- Ticket Type: Incident – Billing Spike Investigation

- Client Reported: Unexpected billing notification from AWS showing over $350 in charges for the month, significantly higher than their usual monthly spend (~$120). No known service changes reported by the client.
- Issue Identified: An m5.24xlarge EC2 instance was created for testing purposes and left running for 72 hours
- Steps Taken:
1. Assumed delegated SupportEngineer role in clients AWS account
2. Opened the Billing and Cost Management Dashboard and launched Cost Explorer
3. Identified a significant increase in EC2 usage during the current billing cycle
4. Investigated running EC2 Instances and found a recently created m5.24xlarge instance that had been running for 72 hours - Estimated cost $288
5. Contacted the client to confirm whether the instance was intentionally running - confirmed it was created for testing purposes and left running my mistake
6. Proceeded to terminate the instance
7. Checked for any active billing alerts and found they were disabled - enabled billing alerts
8. Created a CloudWatch Billing Alarm for EstimatedCharges, greater than 200USD with a new SNS topic subscribed to client's admin email
9. Contacted client to confirm that the cause of the billing spike was found and resolved and projected spend for the billing period was back to within a normal range
10. Walked client through subscribing to the alarm and explained how the alarm will work
- Outcome: Billing issue resolved. Instance terminated with client approval. Billing alarm configured. Client confirmed resolution and follow-up recommendations accepted. Ticket closed.
