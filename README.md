# Lamba-CSV-To-Parquet

# Table of Contents

● [Overview](#overview)<br/>

● [Using Lambda On Your Local Machine](#usinglambda)<br/>
&emsp;◌ [AWS Toolkit for Visual Studio Code](#awstoolkit)<br/>

● [Using Lambda in AWS Console](#lambdaconsole)<br/>
&emsp;◌ [Settig up Layers](#settinguplayers)<br/>
&emsp;◌ [Creating Lambda Function](#creatinglambdafunction)<br/>


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

1. Give a name to your layer; for example, aws-data-wrangler.
2. Select Upload a .zip file. (This AWS Data Wrangler zip.file is shared in this repository, but if you can get the most recent version, [here](https://github.com/awslabs/aws-data-wrangler/releases) 
3. Click on Upload, and select the path where the zip file is
4. For Compatible runtimes, choose Python 3.6.
5. Click on Create.

<img src="https://user-images.githubusercontent.com/69978184/145730774-a0bf70c6-f088-4c4c-b2e3-962e396b15f8.png" width="400" height="400"/>

<img src="https://user-images.githubusercontent.com/69978184/145730818-e68db881-2e59-4acc-85b7-bff22eb36736.png" width="1000" height="400"/>

<img src="https://user-images.githubusercontent.com/69978184/145730861-8aaf878f-9514-42b2-bfd4-c127961408f7.png" width="1000" height="400"/>

### Creating Lambda Function <a name="creatinglambdafunction"></a>

For this step you must click on "Functions" which is on the left side

<img src="https://user-images.githubusercontent.com/69978184/145731091-e219edec-b0c8-42e1-af8e-dc461383b650.png" width="800" height="400"/>

and then, click on "Create function"

<img src="https://user-images.githubusercontent.com/69978184/145731207-4d0e833d-6f06-40bf-b84a-3aeaa96e9c6f.png" width="1000" height="400"/>

To create a Lambda function and trigger an Amazon S3 event, complete the following steps:

1. Give a name to your function; for example, conversion-csv-to-parquet.
2. For Runtime, choose Python 3.6.
3. Select "Create a new role with basic Lambda Permissions" on default execution role
4. Click on Create function.

<img src="https://user-images.githubusercontent.com/69978184/145731382-fecd87da-3db0-4987-83b0-4554931088bc.png" width="1000" height="600"/>

<img src="https://user-images.githubusercontent.com/69978184/145731621-6d5a7d03-5f02-4883-b921-56f6632ef1fe.png" width="1000" height="600"/>

<img src="https://user-images.githubusercontent.com/69978184/145731675-f3876ff5-175e-4b57-ae35-bc283ceb97aa.png" width="1000" height="600"/>

<img src="https://user-images.githubusercontent.com/69978184/145731722-a54a1648-e3ad-4781-9525-59ec95d720b2.png" width="1000" height="300"/>

To increase the lambda timeout setting, complete the following steps

1. Go to the Configuration tab, under General configuration, choose edit
2. For Runtime, choose Python 3.6.
3. Select "Create a new role with basic Lambda Permissions" on default execution role
4. Click on Create function.

<img src="https://user-images.githubusercontent.com/69978184/145731890-76fe61bf-792e-44aa-acfd-50a7fea82793.png" width="1000" height="400"/>

<!-- 
https://aws-dojo.com/excercises/excercise34/
https://www.youtube.com/watch?v=X7Ji2UwRCKI
-->
