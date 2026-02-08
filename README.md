<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-iam)

**Author:** lazim Mohammed  
**Email:** kmlazim98@gmail.com

---

![Image](http://learn.nextwork.org/lively_teal_daring_titipounamu/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate creating EC2 instnace and configure IAM policy a.d IAM group to control the accesI'm doing this project to learn secuirty policy how host EC2 instnce

### Tools and concepts

The key services and concepts I learned in this project were IAM (users, groups, policies, account alias), EC2 instance management, tag‑based access control, permission boundaries, and how Allow/Deny rules impact real‑world access to PROD vs Development environments.

### Project reflection

It took me only a short time to complete this project, as the steps were straightforward—about 30 minutes from start to finish.

---

## Tags

### What I did in this step

In this step, I will proviosn EC2 instance because to need to enhance computing power

### Understanding tags

The tags ‘PROD’ and ‘Development’ will be useful in the future for better segregation and to help manage access permissions more effectively

### My tag configuration

The tag I applied to my EC2 instances is called ‘ENV’. For these instances, I assigned the values ‘PROD’ and ‘Development’.

![Image](http://learn.nextwork.org/lively_teal_daring_titipounamu/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

### What I did in this step

In this step, I will create an IAM policy to define permission rules. This is important because, for security reasons, the PROD environment should have restricted access, while the DEV environment can allow broader access for developers

### Understanding IAM policies

IAM policies are used to configure permissions that define who can access the instances and who cannot

### The policy I set up

For this project, I’ve set up a policy using JSON,

### Policy effect

This IAM policy enforces the following rules:

Allow full EC2 access for Development instances
The first statement grants permission to perform any EC2 action (ec2:*) only on resources tagged with:
Env = development

This ensures users can fully manage only Development environment instances.


Allow read‑only access to all EC2 resources
The second statement gives users the ability to run all describe operations (ec2:Describe*), allowing them to view instances, volumes, snapshots, and other EC2 details across all environments.


Deny the ability to modify tags
The final statement explicitly denies:

ec2:CreateTags
ec2:DeleteTags

This prevents users from changing or removing tags on any EC2 resource—an important security measure to stop users from bypassing tag‑based access controls.

### Understanding Effect, Action, and Resource

Effect → Says whether the action is Allowed or Denied.
Action → Specifies what operations the user can perform.
Resource → Defines which AWS resources the action applies to.

---

## My JSON Policy

![Image](http://learn.nextwork.org/lively_teal_daring_titipounamu/uploads/aws-security-iam_1c864649)

---

## Account Alias

### What I did in this step

In this step, I will create an account alias to make the login process easier, because the default AWS account ID is long and hard to remember.

### Understanding account aliases

An account alias is a custom name you assign to your AWS account so that users don’t have to remember the long, numeric AWS account ID when signing in.

### Setting up my account alias

Creating an account alias took me. 2 mins Now, my new AWS console sign-in URL is. https://nextwork-alias-lazim090.signin.aws.amazon.com/console

![Image](http://learn.nextwork.org/lively_teal_daring_titipounamu/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### What I did in this step

I will go to the Groups and Users sections to define and assign the necessary permissions

### Understanding user groups

IAM user groups are collections of IAM users that share the same permissions. Instead of assigning permissions to each user individually, you assign policies to the group, and all members automatically inherit those permissions

### Attaching policies to user groups

I attached the policy I created to this user group, which means all users in the group automatically receive the same permissions defined in that policy.

### Understanding IAM users

IAM users are individual identities in AWS that represent people or applications needing access. Each IAM user has their own login credentials and can be assigned specific permissions to control what they can do in the AWS account.

---

## Logging in as an IAM User

### Sharing sign-in details

Send the sign‑in URL
– Share the AWS account sign‑in link (with the account alias) so the user can log in.


Send their login credentials
– Provide the username and the temporary password that AWS generated for them.

### Observations from the IAM user dashboard

Once I logged in as my IAM user, I noticed many services showing ‘Access Denied’. This happened because the IAM policy we created restricts access to only the permitted resources.”

![Image](http://learn.nextwork.org/lively_teal_daring_titipounamu/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

### What I did in this step

### Testing policy actions

I started the Development instance and verified full access, and I attempted to stop the Production instance to test the policy restrictions.

### Stopping the production instance

When I tried to stop the production instance, the action was denied because the policy explicitly includes a ‘Deny’ rule that prevents stopping instances in the PROD environment .

![Image](http://learn.nextwork.org/lively_teal_daring_titipounamu/uploads/aws-security-iam_0e7a9d6a)

### Stopping the development instance

When I tried to stop the Development instance, the action was successful because the IAM policy allows full EC2 access for resources tagged as Development.

![Image](http://learn.nextwork.org/lively_teal_daring_titipounamu/uploads/aws-security-iam_1811801c)

---

## IAM Policy Simulator

### Understanding the IAM Policy Simulator

### How I used the simulator

---

---
