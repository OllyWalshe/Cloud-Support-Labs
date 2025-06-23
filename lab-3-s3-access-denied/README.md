## Lab 3 - s3 Access Denied - Bucket Policy Conflict

### Objective
Simulate a real-world support ticket in which a client reports that an IAM user, who previously had access to an Amazon s3 bucket, is now receiving an “Access Denied” error when attempting to download files. Act as a Cloud Support Engineer within an MSP. Reproduce the issue, investigate root cause, resolve it, communicate the outcome to the client, and log the resolution internally.

### Steps Taken
1. Assumed the IAM user role analytics-team-user and reproduced error by attempting to download an object from company-bucket bucket
2. Analysed IAM user policy and confirmed policy allowed s3:GetObject
3. Analysed bucket policy and found explicit deny policy for users outisde of a specific AWS account.
4. Modified bucket JSON policy to add an allow s3:GetObject for principal analytics-team-user.
5. Retested access by attempting to download object from bucket which was successful.
6. Contacted the client to confirm the issue was resolved.
7. Documented the root cause and solution in the internal ticketing system.

### Ticketing Simulation

#### Inbound Ticket
- Ticket ID: 102938
- Submitted by: Joe Bloggs
- Client: Joe's Agency
- Date/Time: 22/06/2025 - 12:23AM
- Priority: High
- Service: Amazon S3 - Object Access

- Subject: User getting Access Denied on S3 bucket
- Message: Hi, One of our analysts, using the IAM user analytics-team-user, is getting an “Access Denied” error when trying to download files from the S3 bucket company-bucket. Could you investigate this as it’s currently blocking some of our reporting tools? Thanks, Joe.

#### Client Response
- Ticket ID: 102938
- Status: Resolved
- Response Type: Public Reply

- Subject: Ticket ID: 102938
- Message: Hi Joe, Thanks for reporting this — I’ve investigated the access issue and confirmed that the IAM user had the necessary permissions via their IAM policy. However, the S3 bucket policy for company-bucket had recently been updated to restrict access only to a specific AWS account, which didn’t include your user. I’ve updated the bucket policy to explicitly allow access for your AWS account, and confirmed that the user can now access the objects in the bucket again. Please ask the user to test again and let me know if the issue is fully resolved from your side. Best regards, Olly Walshe.

#### Internal Ticket Documentation
- Ticket ID: 102938
- Status: Resolved
- Resolution Category: S3 Bucket Access
- Assigned Engineer: Olly Walshe
- Ticket Type: Incident - S3 Access Denied

- Client Reported: User analytics-team-user received “Access Denied” when trying to download files from S3 bucket company-bucket.
- Issue Identified: S3 bucket policy included an explicit deny that blocked access to all principals not in a specific AWS account.
- Steps Taken:
1. Assumed the IAM user role analytics-team-user and reproduced error by attempting to download an object from company-bucket bucket
2. Analysed IAM user policy and confirmed policy allowed s3:GetObject
3. Analysed bucket policy and found explicit deny policy for users outisde of a specific AWS account.
4. Modified bucket JSON policy to add an allow s3:GetObject for principal analytics-team-user.
5. Retested access by attempting to download object from bucket which was successful.
6. Contacted the client to confirm the issue was resolved.
- Outcome: Access restored. Client confirmed issue resolved. Recommended reviewing bucket policy before future IAM adjustments. Ticket closed.
