
## AWS Accounts

- Idendity and Access Management (IAM) Users
    - IAM Users, Groups, Roles (discussed later)
    - start off w/ no access to AWS account. Are granted after AWS acc is created
    - only identities created inside AWS account AND granted access to that account can access its resources 
    - an AWS account is a container for identities (users) and resources

### Accounts Outline

Can use same gmail: 

email@gmail.com --> email+AWSProd@gmail.com --> email+AWSMgmt@gmail.com --> etc.

1. General (*Management)
    - Will include IAM user
    - make sure to add a budget just in case anything is left running 
2. Production (*PROD)

### Identity and Access Management (IAM) Basics (13:01)

    - Least prividelged access: practice of only giving access to person/group/app for functionalities that are NECESSARY ONLY

    - Every AWS account has its own running IAM instance (or database).
    - IAM is a globally resilient service (all data is secured across all DB regions)
    - I have my own dedicated IAM instance running and that account has (generally) full trust with that IAM instance 
    - Can have seperate identities inside individual IAM (identity A can only do fooA; identity B can only do fooB, etc)

    - IAM allows us: 
        - 3 different types of identity objects (user, group, role)
        
            - Need to learn when to use each (later in course)
        
        - `Users` represent humans or applications that need access to your account 
        
        - `Group` are collection of related users (e.g. development team, finance, HR, etc)
        
        - `Roles` can be used by AWS services, or for granting external access to your account. Generally used to grant access to services within your account to uncertain number of identities. Best used when access is needed for uncertain number of identities or you want AWS services to access other AWS services. 

        - `IAM policies` allow or deny access to AWS services **only when attached to IAM users, groups, or roles** (i.e. need to be attached to identity/s)

        - IAM authenticates me (e.g. password. then, IAM has final say on authorize/deny access to a service)

        - Summary notes:
            - No cost (has limits though)
            - Global service/ global resilience 
            - ALLOW or DENY its identities on its AWS account 
            - No direct control on external accounts or users - only controls local identities in my account 
            - Allows use of Identity federation (e.g. use my company's directory, such as email domain to grant access) and MFA 

### [DEMO] Accounts - Step4 - Adding IAMADMIN to GENERAL Account (12:36)

Here we create an IAM user with following settings: 
- `Provide user access to the AWS Management Console - optional`: Yes
- `I want to create an IAM user`: Yes
- `Custom Password`
- `Users must create a new password at next sign-in - Recommended`: No

After creating, we get to `Set permissions` window, here we do the following: 
1. Select: `Attach policies directly`
2. Select policy: `AdministratorAccess`
3. Select `Next`
4. Select `Create User`


Now, lets test if we can log in as IAM. We will be using this IAM to log in for the remainder of the course. Log on by using URL to log into general AWS account using this IAM user. Simply use URL and use IAM login info we set in the previous step. Upon login, you will see in top-right corner that it shows IAM user info. **This (IAM) identity has admin access and has full control over this account; same level of access as root user of this AWS account**.

From now on, we will be using this IAM account (instead of root).

Now, we need to set up passwords as we did for root account. Set MFA information in `Security credentials` (similar to what we previously did).


#### Account Aliases: 

See `cantrill/keys.md` (ignored file)

### [DEMO] ACCOUNTS - STEP4 - Adding IAMADMIN to PRODUCTION Account (10:17)

#### Summary

In this [DEMO] lesson I will step you through how to add an IAM user to the PRODUCTION AWS Account which has permissions almost equal to the Account Root User

#### Notes 

We essentially do the same thing as previous demo (todo: link it) but for production account.