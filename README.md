# Essential-skills-in-Scripting

## Overview

This project focuses on 5 critical skills in shell scripting  to better equip us with the capabilities to harness the required skills needed in both shell scripting and cloud computing.

We will demonstrate how to leverage on and apply these tools together, to achieve our desired objective to build, deploy and manage scalable and robust systems in the cloud.

These 5 critical concepts are:

1. Functions 

2. Arrays

3. Environment variables

4. Command line arguments

5. Error Handling


We will use **Datawise Solutions**, a Data science consulting company to demonstrate how these concepts can be applied in a real-world setting when a company recognises the need for efficiency in setting up such environments using automation.

The task therefore is to deploy Data-science workspace for one of **Datawise Solution's** clients, an e-commerce startup, who wants to harness the power of data science to analyse customer behaviour and enhance their shopping experience.

This start-up wishes to deploy their data-science workspace on AWS, utilizing EC2 instances for computational tasks and S3 Buckets for storing their vast datasets of customer interactions.

### REQUIREMENTS

To develop a script that automates the setup of EC2 instances and S3 Buckets. It will incorporate the 5 critical shell scripting concepts earlier mentioned.

**EC2 setup**

**Applying Functions**

We will use the vi editor to develop our script, first we start with the shebang line.

This is the hash sign followed by the exclamation mark (#!), then specify the path to the interpreter that we want our script to be evaluated by.

  #!/bin/bash

  Also AWS Cli must be configured before

  We will apply functions in setting up EC2 and define it using the following syntax:

  function_name() {"\n}  # function body\n

  Breaking down the syntax:

 * function_name: This is the name of the function ; in this case "create_ec2_instance"

 * Parentheses(): They are used to define the function

 * Curly braces{}: They enclose the body of the function, where you define the commands or logic the function will execute. 



 ### Function to launch an EC2 instance

  launch_instance() {
  local AMI_ID=$1
  local INSTANCE_TYPE=$2
  local KEY_NAME=$3
  local SECURITY_GROUP=$4
  local SUBNET_ID=$5


 echo "Launching EC2 instance..."

  aws ec2 run-instances \
    --image-id "$AMI_ID" \
    --instance-type "$INSTANCE_TYPE" \
    --key-name "$KEY_NAME" \
    --security-group-ids "$SECURITY_GROUP" \
    --subnet-id "$SUBNET_ID" \
    --count 1 \
    --tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=MyInstance}]'
 }

  Using the Vi editor we develop the script as follows:

   ![alt text](<Images/Scrpting images 1.PNG>)
  
  
  **Arrays:** Arrays are used in shell scripting to manage and loop through multiple values. For instance, to store multiple configuration options like AMI IDs, instance types, security groups etc or even launch multiple instances. This start-up can therefore use arrays in configuring their vast range of customer information using automation.
  We therefore update the script to use arrays in the configuration options as follows.


 
   ![alt text](<Images/Scripting Images 2.PNG>)
   ![alt text](<Images/Scripting Images 3.PNG>)
   
   
   
   **Environment variables**

     Environment variables  are used in scripting to code sensitive information about AWS credentials without exposing the actual values.
     For instance AWS-access_key_id and AWS_secret_access_key can be stored in the environment variables.
     Applying environment variables can ensure this start-up is able to securely handle  sensitive customer information without any fear of compromise.

     This can be stored securely in .env or ~/.bash_profile or  alternatively, set temporarily in a shell.

     Putting it in a .env file

      # .env file
      AMI_ID="ami-0abcdef1234567890"
      INSTANCE_TYPE="t2.micro"
      KEY_NAME="my-key"
      SECURITY_GROUP="sg-0abc123def456"
      SUBNET_ID="subnet-0123456789abcdef0"

      Then load it in the script as follows:

      source .env


      Alternatively, set them temporarily in a shell

      export AMI_ID="ami-0abcdef1234567890"
      export INSTANCE_TYPE="t2.micro"
      export KEY_NAME="my-key"
      export SECURITY_GROUP="sg-0abc123def456"
      export SUBNET_ID="subnet-0123456789abcdef0"

      The script will look like this:


      ![alt text](<Images/Scripting Images 4.PNG>)


   **Command line Arguments**

   We can use command line arguments to specify an EC2 instance type or S3 bucket name thereby allowing for flexible deployments. Instead of hardcoding values or relying on environment values, we can pass values directly when running the script.

   It is possible to pass multiple parameters to a script, the dollar sign ($) is used to prefix the position of the argument passed to the script.

   So the e-commerce start-up  could  modify information relating to customers' configurable parameters like AMI-ID, Key-name, Instance type etc, thereby using the same script for multiple customers by applying command line arguments in the script as follows:

   ![alt text](<Images/Scripting Images 5.PNG>)
   ![alt text](<Images/Scripting Images 6.PNG>)



   **Error Handling**

    Error handling and debugging techniques such as printing debug information, using exit codes in functions, enabling debug mode by adding set -x to the code and trapping errors by a custom error-handling function can be incorporated in script to launch an instance.

    With this, datawise's client can develop a script that  ensures a safe, robust and friendly interface
    and catch any customer configuration issues like missing parameters, failed AWS CLI calls, or network/authentication errors, and respond with clear messages. 

   Example Script to check for empty values:

   ![alt text](<Images/Scripting Images 7.PNG>)

   The above script can then be added to their launch instance script to catch any errors on customer information before the instance is launched, thereby making for a more seamless customer experience.

   The script can be updated , applying these 5 concepts to develop a script for Datawise's E-commerce Start-up.


   

