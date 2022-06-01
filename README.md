# Topic: AWS-EC2-Instance-with-an-Admin-Role

### Overview

> You will create an EC2 Instance based on Amazon Linux AMI that you can connect via SSH. While provisioning the instance, you will make sure to limit access to your IP address only, using Security Groups. The instance will already have the CLI installed by default. You just need to assign permissions to this instance.

> Once the instance is running, create an IAM role with admin access to your account. Then, attach the role to your EC2. In this case, the CLI tool will pick up the credentials from the role and won’t need hard-coded credentials.

> Let's do this exercise to make your learning fun.

### Prerequisites:
> AWS Account

### Tasks
> Launch a secure EC2 instance

> Create IAM role with admin privileges

> Attach the IAM role to the EC2 instance created earlier

> Connect to your EC2 instance via SSH

> Use CLI tool in the EC2 instance

### Steps

#### Step 1:Create a default VPC

> It is possible that you already have a default VPC created in your account. If not, go to the VPC dashboard and create a default VPC.

![image](https://user-images.githubusercontent.com/40290711/171456820-4e8c6055-b720-4c14-aa21-862f653ae139.png)

#### Step 2. Launch an EC2 instance

> Navigate to the EC2 dashboard, and select the Instances services in the left-hand navigation pane.

![image](https://user-images.githubusercontent.com/40290711/171457891-95190ffa-733d-406c-b6d6-64cf4b064b17.png)

> Use the Launch Instance wizard to launch an instance with the following configuration, and leave the remaining values as the defaults:

           Stage	                           Configuration	                    Value
            1.	                          Amazon Machine Image (AMI)	    Amazon Linux 2 AMI (HVM), SSD Volume Type Note: You have chosen a Free Tier Eligible AMI
            2.	                            Instance Type	                    t2.micro
            3.	Configure                   Instance Details	
                                          >  a. Number of Instances	                      1
                                          >  b. Network	                              Default
                                                                         Select the VPC that was created in the previous step
                                         > c.   Subnet	                             Default
            4.	                            Storage	                             Default
            5.	                              Tags	                             Optional
            6.	                             Security Group	                    New.
                                                                              Limit access to your IP address only



- >  See a snapshot below:

![image](https://user-images.githubusercontent.com/40290711/171458262-da11863e-f456-4782-8cbc-3a0beceb7769.png)

![image](https://user-images.githubusercontent.com/40290711/171462445-3c1e21dc-5ac3-4205-b0d9-2805e01dfacd.png)

![image](https://user-images.githubusercontent.com/40290711/171462749-aa2c9715-f37d-4f14-ab9e-64b5f52bd04c.png)

- > Download a new SSH Key if you don't have one already.

- > Important: This key-pair will allow you to log into your instance, using SSH, from your local machine. Save the key-pair carefully, because the same private key cannot be re-generated.

![image](https://user-images.githubusercontent.com/40290711/171463945-41af0009-c331-4a80-b3a5-670826fe4b14.png)
- > Allow only yourself to access the EC2 instance

- > Verify that you should see the newly created EC2 instance in the Instances services. Check the instance state, it should say Running.

![image](https://user-images.githubusercontent.com/40290711/171467310-75135ce8-f825-4df0-a0cd-4adbde916451.png)
