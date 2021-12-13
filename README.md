# Lamba-CSV-To-Parquet

# Table of Contents

● [Overview](#overview)<br/>

● [Using Lambda On Your Local Machine](#usinglambda)<br/>
&emsp;◌ [AWS Toolkit for Visual Studio Code](#awstoolkit)<br/>

● [Using Lambda in AWS Console](#lambdaconsole)<br/>
&emsp;◌ [Settig up Layers](#settinguplayers)<br/>
&emsp;◌ [Creating Lambda Function](#creatinglambdafunction)<br/>
&emsp;◌ [Adding Permissions to Lambda](#addingpermissionstolambda)<br/>
&emsp;◌ [Checking Files in S3 for transformation](#checkingfilesins3)<br/>
&emsp;◌ [Creating Script for transformation](#scriptfortransformation)<br/>

## Overview <a name="overview"></a>

[__Lambda__](https://www.dynatrace.com/news/blog/what-is-aws-lambda-2/) -> What is AWS Lambda?
AWS Lambda is a serverless compute service that can run code in response to predetermined events or conditions and automatically manage all the computing resources required for those processes. It also enables DevOps teams to connect to any number of AWS services or run their own functions.

Organizations are realizing the cost savings and management benefits of serverless automation. But with the benefits also come concerns about observability, and how to monitor and manage ever-expanding cloud software stacks.

## Using Lambda On Your Local Machine <a name="usinglambda"></a>

### AWS Toolkit for Visual Studio Code <a name="awstoolkit"></a>

To do this procedure is needed to install [VS Code](https://code.visualstudio.com/download) on your local Machine.

Once you've installed VSCode, some steps will be needed from now on. 

1) [Obtaining AWS Acess Keys](https://docs.aws.amazon.com/toolkit-for-vscode/latest/userguide/obtain-credentials.html)

2) How to [set up the AWS Credentials](https://docs.aws.amazon.com/toolkit-for-vscode/latest/userguide/setup-credentials.html) on your Local Machine

3) [Connecting to AWS through the AWS Toolkit for Visual Studio Code](https://docs.aws.amazon.com/toolkit-for-vscode/latest/userguide/connect.html)

Once you've already followed the step-by-step guide above, if you acess your VSCode, you may see something like this:

<img src="https://user-images.githubusercontent.com/69978184/144343625-8553c492-8bcf-4a85-8b3e-8567acfcafe7.png" width="800" height="400"/>

It means that the connection between cloud and local machine has been completed Successfully.

The next step you may need to download the [AWS SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html).

With its download finished up, you may see something like this below:

<img src="https://user-images.githubusercontent.com/69978184/144772002-d6d30532-927a-4a94-90b9-51932791a2e5.png" width="800" height="400"/>

Hence, you click on "Create Lambda SAM Application" and keep following the steps below.

<img src="https://user-images.githubusercontent.com/69978184/144772002-d6d30532-927a-4a94-90b9-51932791a2e5.png" width="800" height="400"/>

<img src="https://user-images.githubusercontent.com/69978184/144772754-bab0a84b-d5e9-4a7b-82d4-d6cf2cbc683c.png" width="600" height="400"/>

<img src="https://user-images.githubusercontent.com/69978184/144772883-933aad3e-2203-49c0-8ba4-a920191028c6.png" width="600" height="250"/>

<img src="https://user-images.githubusercontent.com/69978184/144772987-15fb2090-42cc-41df-b834-4ebbfb3a5d5c.png" width="600" height="250"/>

For this project has been decided to use three libraries, which are:

1) AWSWrangler
2) Boto3
3) Pandas

<img src="https://user-images.githubusercontent.com/69978184/144774523-0083e9ab-dd44-4761-9e8e-a59d6f9b49ea.png" width="600" height="400"/>

## Using Lambda in AWS Console <a name="lambdaconsole"></a>

Before setting up the layers you've got to go through AWS Console Management and click on Lambda or look for Lambda to get started.

<img src="https://user-images.githubusercontent.com/69978184/145729245-bbc9532a-133b-462d-8301-b39ff6f398cd.png" width="800" height="400"/>

### Setting up Layers <a name="settinguplayers"></a>

Before, keep going let's understand a little about what is Lambda Layer.

A [Lambda layer](https://aws.amazon.com/blogs/compute/using-lambda-layers-to-simplify-your-development-process/) is an archive containing additional code, such as libraries, dependencies, or even custom runtimes. When you include a layer in a function, the contents are extracted to the /opt directory in the execution environment.

Now you have some idea about what is, let is keep setting it up.

Once you've already accessed the Lambda section, you must click on layers which is on the left side

<img src="https://user-images.githubusercontent.com/69978184/145729461-9c11b1e3-a45b-4b7e-9cbf-791e95916c3d.png" width="800" height="400"/>

and then, click on "Create layers"


<img src="https://user-images.githubusercontent.com/69978184/145729882-e87864a2-1def-41c7-81de-ed894c322117.png" width="800" height="400"/>

To create a Lambda layer, complete the following steps

1. Give a name to your layer; for example, aws-data-wrangler.<br/>
<img src="https://user-images.githubusercontent.com/69978184/145730774-a0bf70c6-f088-4c4c-b2e3-962e396b15f8.png" width="400" height="400"/><br/>
2. Select Upload a .zip file. (This AWS Data Wrangler zip.file is shared in this repository, but if you can get the most recent version, [here](https://github.com/awslabs/aws-data-wrangler/releases) <br/>
3. Click on Upload, and select the path where the zip file is<br/>
4. For Compatible runtimes, choose Python 3.6.<br/>
5. Click on Create.<br/>
<img src="https://user-images.githubusercontent.com/69978184/145730818-e68db881-2e59-4acc-85b7-bff22eb36736.png" width="1000" height="400"/><br/>
<img src="https://user-images.githubusercontent.com/69978184/145730861-8aaf878f-9514-42b2-bfd4-c127961408f7.png" width="1000" height="400"/><br/>

### Creating Lambda Function <a name="creatinglambdafunction"></a>

For this step you must click on "Functions" which is on the left side

<img src="https://user-images.githubusercontent.com/69978184/145731091-e219edec-b0c8-42e1-af8e-dc461383b650.png" width="800" height="400"/>

and then, click on "Create function"

<img src="https://user-images.githubusercontent.com/69978184/145731207-4d0e833d-6f06-40bf-b84a-3aeaa96e9c6f.png" width="1000" height="400"/>

To create a Lambda function and trigger an Amazon S3 event, complete the following steps:

1. Give a name to your function; for example, conversion-csv-to-parquet.<br/>
<img src="https://user-images.githubusercontent.com/69978184/145731621-6d5a7d03-5f02-4883-b921-56f6632ef1fe.png" width="1000" height="600"/><br/>
2. For Runtime, choose Python 3.6.<br/>
3. Select "Create a new role with basic Lambda Permissions" on default execution role<br/>
<img src="https://user-images.githubusercontent.com/69978184/145731382-fecd87da-3db0-4987-83b0-4554931088bc.png" width="1000" height="600"/><br/>
4. Click on Create function.<br/>
<img src="https://user-images.githubusercontent.com/69978184/145731722-a54a1648-e3ad-4781-9525-59ec95d720b2.png" width="1000" height="300"/><br/>

To increase the lambda timeout setting, complete the following steps

1. Go to the Configuration tab, under General configuration, choose edit<br/>
<img src="https://user-images.githubusercontent.com/69978184/145731942-f2fe330b-b7b1-4c1e-ac55-c8afe0d3c7f0.png" width="1000" height="600"/><br/>
2. Set 30 sec as Timeout<br/>
<img src="https://user-images.githubusercontent.com/69978184/145732117-d1c2073b-2e40-4fb8-91a4-e292edf04017.png" width="400" height="400"/><br/>
4. Click on Save.
<img src="https://user-images.githubusercontent.com/69978184/145732162-105bd5f5-2fc5-43b8-a22d-baaa1b0a2e17.png" width="1000" height="600"/><br/>

### Adding Permissions to Lambda <a name="addingpermissionstolambda"></a>

To add appropriate permissions for this Lambda function to read and write Amazon S3 objects, complete the following steps:

1. On the permission table, under Permissions, click on "conversion-csv-to-parquet-role-jnui0vec" to be redirected to IAM roles for that role name<br/>
<img src="https://user-images.githubusercontent.com/69978184/145732720-2296e346-0164-4e02-9d45-4eda91853683.png" width="1000" height="400"/><br/>
2. On the AWS Identity and Access Management (IAM) console, click on Policies<br/>
3. Click on Create Policy.<br/>
4. On the JSON tab, enter the following policy (replace the target bucket name arn:aws:s3:::lambdaconvertion* with your own bucket name)<br/>
<img src="https://user-images.githubusercontent.com/69978184/145733057-af9ca04a-69b5-4ef3-a021-31a0e89202b0.png" width="600" height="400"/><br/>
5. Click on Next Tags<br/>
6. Click on Next Review<br/>
<img src="https://user-images.githubusercontent.com/69978184/145733116-0971b056-0a70-4615-8dff-6955e28c810f.png" width="600" height="400"/><br/>
7. Give a name to your new policy; for example, lambda-s3-CSV-to-Parquet<br/>
<img src="https://user-images.githubusercontent.com/69978184/145733142-1a3f4c95-b35c-4b99-9bd5-cad313ac9c9a.png" width="600" height="400"/><br/>
8. To finish it up, click on Create policy<br/>
9. On policies section in the search field, look for the recent policy created<br/>
<img src="https://user-images.githubusercontent.com/69978184/145733406-b945e834-5fc5-4db1-af9c-32f1c339ba10.png" width="600" height="400"/><br/>
10. Click on it<br/>
11. Click on Policy usage and then on attach<br/>
<img src="https://user-images.githubusercontent.com/69978184/145733821-b66c3555-88bb-4274-985c-19e56a54b2c5.png" width="600" height="400"/><br/>
12. Select the role and click on Attach policy<br/>
<img src="https://user-images.githubusercontent.com/69978184/145733878-8f9e80a0-3a29-4994-abb7-dc71477336e5.png" width="600" height="400"/><br/>


<!-- {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:ListBucket"
            ],
            "Resource": [
                "arn:aws:s3:::lambdaconvertion",
                "arn:aws:s3:::lambdaconvertion/*"
            ]
        }
    ]
}
-->

### Checking Files in S3 for transformation <a name="checkingfilesins3"></a>

You've got to go through AWS Console Management and click on S3 or look for S3 to get started.

To check files in s3, complete the following steps:

1. Select "lambdaconvertion" bucket<br/>
<img src="https://user-images.githubusercontent.com/69978184/145734423-f54f6a8d-53dd-44e7-a43d-cfacf15b9c06.png" width="800" height="600"/><br/>
2. Create input folder in the "lambdaconvertion" bucket<br/>
<img src="https://user-images.githubusercontent.com/69978184/145734537-45a84946-6b3b-420a-b6b5-2b27238324c0.png" width="600" height="400"/><br/>
3. Create output folder in the "lambdaconvertion" bucket<br/>
<img src="https://user-images.githubusercontent.com/69978184/145734575-af7298b4-b87c-44c9-8ff2-fcad5ce576c2.png" width="600" height="400"/><br/>
4. Upload CSV file into input folder<br/>
<img src="https://user-images.githubusercontent.com/69978184/145734739-f195d5bf-805d-4abe-984c-a47f464a93fb.png" width="600" height="400"/><br/>

### Creating Script for transformation <a name="scriptfortransformation"></a>

Access Lambda section, and click on Code tab to enter your code

<img src="https://user-images.githubusercontent.com/69978184/145735395-c2a082d0-ca78-4fe6-b03f-1d1231fca374.png" width="600" height="400"/><br/>


<!-- 
https://aws-dojo.com/excercises/excercise34/
https://www.youtube.com/watch?v=X7Ji2UwRCKI
-->
