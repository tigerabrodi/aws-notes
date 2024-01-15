# IAM

- Account is a closed bucket of resources.
- The root user is the owner of your account.
- IAM users for tailor made permissions to fulfill daily tasks.
- Groups to easily manage permissions for a set of users.

## ARNs

- Amazon Resource Names: `arn:partition:service:region:account-id:resource-id`
- How resources are uniquely identified across all of AWS.

## Tips and Tricks

- Grant least privilege.
- Rotate access keys regularly.
- Use multi-factor authentication.
- Don't use root account for daily work
- Leverage IAM roles as much as possible

# Shared Responsibility Model

- AWS is responsible for the security of the cloud.
- You are responsible for security in the cloud.
