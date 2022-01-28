# Web Switch
<div align="center">
  <br>
  <a href="https://signin.aws.amazon.com/signin?redirect_uri=https%3A%2F%2Faws.amazon.com%2Fmarketplace%2Fmanagement%2Fsignin%3Fstate%3DhashArgs%2523%26isauthcode%3Dtrue&client_id=arn%3Aaws%3Aiam%3A%3A015428540659%3Auser%2Faws-mp-seller-management-portal&forceMobileApp=0&code_challenge=aob9N8uqf0Ig-0kp2wj_HVSqGtE6HKHFv23ub_2Cqaw&code_challenge_method=SHA-256">
  <img height="100em" src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/93/Amazon_Web_Services_Logo.svg/512px-Amazon_Web_Services_Logo.png"></img>
</a>
</div>
<br>
<br>
Step by Step to buildling an AWS Archtecture to switch a relay from website.

## Let's put our hands-on in Amazon Web Server!

### Login in AWS Account

We will need to login in our AWS Account to make all this happen! So, <a href="https://signin.aws.amazon.com/signin?redirect_uri=https%3A%2F%2Faws.amazon.com%2Fmarketplace%2Fmanagement%2Fsignin%3Fstate%3DhashArgs%2523%26isauthcode%3Dtrue&client_id=arn%3Aaws%3Aiam%3A%3A015428540659%3Auser%2Faws-mp-seller-management-portal&forceMobileApp=0&code_challenge=aob9N8uqf0Ig-0kp2wj_HVSqGtE6HKHFv23ub_2Cqaw&code_challenge_method=SHA-256">click here</a> to sign in.

#### Creating Lambda Functions
In console of AWS, type Lambda and click in button to open the space to create our Lambda Functions.
Now, we are starting our project! We will create two Lambda Functions. The first will be responsable to <b>Check</b> if our switch are <i>ON</i> or <i>OFF</i>.
So take a note of the both Lambda Functions Names, it will be important later.

### For the first Lambda
Follow Step inside Shadow Status Check folder
### For the second Lambda
Follow Step inside Shadow Status Update folder
### Launching our stack

Click in button Below<br>
[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=buildkite)

Select: <i>Template is ready>Upload a template file>select .yml file downloaded>next</i>
Now:
<ul>
  <li>Type any stack name</li>
  <li>Insert your first Lambda Function Created</li>
  <li>Insert your second Lambda Function Created</li>
  <li>Type your ThingName (Capital letters and special carachteres, are not allowed)</li>
  <li>Select "REGIONAL", in apiRegion</li>
  <li>Next</li>
  <li>Scroll the website to the end and press Next button</li>
  <li>Scroll the website to the end and select <i><b>I acknowledge that AWS CloudFormation might create IAM resources with custom names</b></i></li>
  <li>Create Stack</i>
</ul>
At this time, wait the stack name be with status: "CREATE_COMPLETE", to check this out, just press the reload button inside AWS
Congratulations!!

### Uploading WebSite
Before we Update the html to our bucket, we need to configure the URL to be invoked when requisited.<br>
Open <b><i>API Gateway>API_{ThingName}>Stage>Click in arrow to show options>Click in Get Method and copy the URL.</i></b><br>
<ul>
  <li>Open <b>iot_lamp.txt</b></li>
    <ul>
      <li>There are three lines inside that you need to paste the URL copied inside single quotes</li>
    </ul>
  <li> save as iot_lamp.html</li>
  <li>In AWS Console Type: S3 > Search by your thingname> upload> Select iot_lamp.html>upload</li>
</ul>

### Configuring ESP and AWS IoT Core
Follow the steps inside "iot_switch_esp_code" folder

## Let's test
Open <b><i>API Gateway>API_{ThingName}>Stage>Click in link
Now, type your ThingName>Check>Press to Turn Off/On
