# Lamba-CSV-To-Parquet

# Table of Contents

● [Overview](#overview)<br/>

● [Using Lambda On Your Local Machine](#usinglambda)<br/>
&emsp;◌ [AWS Toolkit for Visual Studio Code](#awstoolkit)<br/>

● [Using Lambda in AWS Console](#lambdaconsole)<br/>
&emsp;◌ [Settig up Layers](#settinguplayers)<br/>

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

Once you've already accessed the Lambda section, you must click on layers which is on the right side

<img src="https://user-images.githubusercontent.com/69978184/145729461-9c11b1e3-a45b-4b7e-9cbf-791e95916c3d.png" width="800" height="400"/>

A [Lambda layer](https://aws.amazon.com/blogs/compute/using-lambda-layers-to-simplify-your-development-process/) is an archive containing additional code, such as libraries, dependencies, or even custom runtimes. When you include a layer in a function, the contents are extracted to the /opt directory in the execution environment.

<img src="https://user-images.githubusercontent.com/69978184/145729578-b04030cb-6ff0-4956-a431-cf11defd3b92.png" width="800" height="400"/>


<!-- 
https://aws-dojo.com/excercises/excercise34/
https://www.youtube.com/watch?v=X7Ji2UwRCKI
-->
