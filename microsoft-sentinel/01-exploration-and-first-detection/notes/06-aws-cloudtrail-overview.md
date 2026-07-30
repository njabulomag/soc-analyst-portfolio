# Step 6 – Explore AWS CloudTrail Activity

## Objective

Review AWS CloudTrail logs to understand cloud activity and identify potentially suspicious administrative actions.

## Query Used

[06-aws-cloudtrail-overview.kql](../queries/06-aws-cloudtrail-overview.kql)

## Key Findings

The CloudTrail logs showed the following common AWS activities:

| Event Name | AWS Service | Count |
|------------|-------------|------:|
| ConsoleLogin | signin.amazonaws.com | 7 |
| GetObject | s3.amazonaws.com | 4 |
| DescribeInstances | ec2.amazonaws.com | 3 |
| DescribeSecurityGroups | ec2.amazonaws.com | 2 |
| PutObject | s3.amazonaws.com | 2 |

The observed activity consisted primarily of user logins, object access in Amazon S3, and EC2 environment inspection. No immediately suspicious administrative actions such as user creation, access key creation, or logging tampering were identified during this stage of the investigation.

## Evidence

Screenshot:

`06-aws-cloudtrail-overview.png`
