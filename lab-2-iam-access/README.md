## Lab 2 - IAM Access Denied (MSP Ticket Simulation)

### Objective
Simulate a real-world support ticket from a managed service client reporting that a new team member cannot access the AWS Billing Dashboard. Act as a Cloud Support Engineer within an MSP and investigate the issue, resolve, communicate with the client and document the resolution.

### Steps Taken

1. I recieved the ticket and noted that our client was unable to access the billing dashboard. I then communicated to the client I had recieved their ticket and was actively working to solve the issue.
2. I assumed the cross-account SupportEngineer role within the organisation
3. I located the user in AWS IAM and confirmed their account had been added to the FinanceDepartment IAM group
4. I checked the IAM group's attached policies and found no billing permissions assigned.
5. I attached AWSBillingReadOnlyAccess policy to the FinanceDepartment IAM group.
6. Verified the policy had been attached to the users account.
7. Asked the client to confirm they now had access to the Billing Dashboard.
8. Responded to the clients ticket with a clear explanation of the issue and resolution.
9. Documented the workflow in the internal ticketing system.

### Ticketing Simulation

#### Inbound Ticket
- Ticket ID: 928374
- Submitted by: Jane Doe
- Client: Jane's Small Business
- Date/Time: 19/06/2025 - 11:43AM
- Priority: Medium
- Service: AWS Access Management (IAM)

- Subject: New user can’t access billing dashboard
- Message:  Hi, We've just onboarded a new employee to the finance department and followed the IAM user setup you provided. They are able to log in but keep getting "Access Denied" when trying to view the Billing Dashboard. Could you take a look? Thanks.

#### Client Response
- Ticket ID: 928374
- Status: Resolved
- Response Type: Public Reply

- Subject: Ticket ID: 928374
- Message: Hi Jane, thanks for raising this. I have investigated the new employees IAM configurtion and confirmed they were correctly added to the Finance Department user group. However, this group did not have a policy allowing access to the Billing Dashboard. I have added a read only permission to allow access to the Billing Dashboard for users in this group - including the new employee. Could you please have them log in and confirm they now have access to the Billing Dashboard. Thanks, Olly.

#### Internal Ticket Documentation
- Ticket ID: 928374
- Status: Resolved
- Resolution Category: IAM Permissions
- Assigned Engineer: Olly Walshe
- Ticket Type: Incident - IAM Access Denied

- Client Reported: New finance team member unable to access AWS Billing Dashboard despite being added to the correct IAM group.
- Issue Identified: The Finance Department IAM group did not have the AWSBillingReadOnlyAccess policy attached.
- Steps Taken:
  1. Assumed the cross-account SupportEngineer role within the organisation
  2. Located the user in AWS IAM and confirmed their account had been added to the FinanceDepartment IAM group.
  3. Checked the IAM group's attached policies and found no billing permissions assigned.
  4. Attached AWSBillingReadOnlyAccess policy to the FinanceDepartment IAM group.
  5. Verified the policy had been attached to the users account.
  6. Asked the client to confirm they now had access to the Billing Dashboard.
- Outcome: Client now has access to Billing Dashboard. Client notified and confirmed resolution.
