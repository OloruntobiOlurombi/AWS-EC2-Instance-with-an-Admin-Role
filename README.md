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


#### Step 3. Create an IAM Role
> Navigate to the IAM dashboard, and select the Roles services in the left-hand navigation pane.

![image](https://user-images.githubusercontent.com/40290711/171467697-a0ddfd63-06de-4bce-92c3-a0f7717c4abe.png)

![image](https://user-images.githubusercontent.com/40290711/171467871-6ea792e8-dad6-4942-b277-b256abe4fb8e.png)

- > Click on the Create role button, and provide the configuration details, as follows.

![image](https://user-images.githubusercontent.com/40290711/171468181-031fd25a-c042-456a-b8ae-63c3636a06e9.png)

- > Select AWS service as the type of trusted entity, and choose EC2 service to assume the new role. It will allow the EC2 instance, to whom we will attach this role later, to be able to call any AWS service on your behalf.

![image](https://user-images.githubusercontent.com/40290711/171469161-65ab2fc4-ec23-4f43-8c22-82256b8e9ae5.png)
> Select the AWS service as the trusted entity, and choose the EC2 service to assume the new role

- > In the Filter policies textbox, search for the "admin" policy. Select the AdministratorAccess policy to apply to the new role.

![image](https://user-images.githubusercontent.com/40290711/171470123-78f1aee2-792d-4f22-9992-7312e7332f50.png)
> Attach the admin policy to the new role

> Provide a name to the new role, such as VocareumSecureServerRole, or choose any other name of your choice.

![image](https://user-images.githubusercontent.com/40290711/171471094-6592a7b9-4eac-4f36-a6a2-373c9d25a9e5.png)
- >  Provide a role name

![image](https://user-images.githubusercontent.com/40290711/171471586-764f5563-b6cb-4d94-b847-7ca3fd70fe61.png)
- > A successfully created role

#### Step 4. Attach the Role to the EC2 Instance

> Go back to the EC2 dashboard, and view the list of the running instances.

> Select the checkbox against the recently launched (earlier in this exercise) EC2 instance, and click the Actions button on the top of the list. It will open up drop-down options, select the Security → Modify IAM role option. See the snapshot below.

![image](https://user-images.githubusercontent.com/40290711/171473008-64ec8c34-bfd5-4d45-abee-2d074d2ce66c.png)


