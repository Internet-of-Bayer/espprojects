## Configuring ESP and AWS IoT Core

### Editing AWS IoT Shadow 
In this session, we will configure the AWS Shadow State (To check and update the shadow of our object) at AWS IoT Core to permite the connection and communication between AWS and our device
At first, let's search in AWS Console, IoT Core.
So with IoT Core Open: <b><i>Manage>Things>Select your ThingName created with Stack earlier</i></b>
Navigate in tabs at <b><i>Device Shadow</i></b>
Now:
<ul>
  <li><i>Create Shadow>Unnamed (classic) Shadow>Edit</i></li>
  <li>Copy the code below and replace all in the code area</li>
  <b>{ "state": { "desired": { "status": "off" }, "reported": { "status": "off" } } } </b>
  <li>Update</li>
</ul>

### Finally, let's generate our certificate and attach policy to our thing
Returning to our Thing open, click in: Certificates>Create Certificate<br>
Now:
<ul>
  <li>At Device Certificate: Active Certificate>Download (save the certificate)</li> 
  <li>At Public Key: Download (don't need to save)</li> 
  <li>At Private key: Download (save the certificate)</li> 
  <li>Done</li> 
  <li>Click in the certificate created>Policies>Attach Policies>Policy_{ThingName}</li>
</ul>

### Configuring ESP32
Finally, let's configure the device.
Open the folder "iot_switch_esp_code">iot_switch_esp_code.ino<br>
<b>At iot_switch_esp_code.ino file</b>
<ul>
  There are two lines that we will need to modificate as follow
  The first line, change the ThingName to created: #define AWS_IOT_PUBLISH_TOPIC   "$aws/things/<b><i>THINGNAME</i></b>/shadow/update"
  The second line, change the ThingName to created: #define AWS_IOT_SUBSCRIBE_TOPIC   "$aws/things/<b><i>THINGNAME</i></b>/shadow/update/delta"
</ul>
<b>At secrets.h file</b>
<ul>
  <li>Change the ThingName to created: #define THINGNAME <b><i>"THINGNAME"</i></b></li>
  <li>You’d have to replace the values of <WIFI NAME>, AWSEnDPOINT (your AWS IoT Host Endpoint), and <WIFI PASSWORD> depending on your setup</li>
    <ul>
      <li>To find your AWSENDPOINT: IoT Core>Settings(in the end of left Menu)>Endpoint</li>
    </ul>
</ul>

<ul>
  <b>Now let's replace the certificates that we downloaded earlier</b>
  <li>At AWS_CERT_CRT[], replace the certificate.perm</li>
  <li>At AWS_CERT_PRIVATE[], replace the certificate.perm</li>
</ul>
    
## Writing the Code to our Device
Plug your ESP32 in Desktop/Notebook
In the left upside, click in right arrow. Wait the written and when the console show "Connecting....___" Press the right button at ESP named: boot, until the code start flash. Wait 1 minute and well done!
