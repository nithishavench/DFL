# Device Fleet Provisioning with AWS IoTCore
Updates:

Now with the ability to respond to cert rotation requests. When the device has been informed it needs to rotate certificates, simply set an additional (optional) attribute isRotation = True. This update is used in conjunction with a cert_rotation policy specified below. This solution relies on setting a cert_issuance date in the registry when the certificate is registered. This is handled by the provisioning template. Once the device is notified, it can process the rotation through setting the flag below.
provisioner.get_official_certs(callback, isRotation=True)
It can often be difficult to manage the secure provisioning of myriad IoT devices in the field. This process can often involve invasive workflow measures, qualified personnel, secure handling of sensitive information, and management of dispensed credentials. Through
IoT Core, AWS Fleet Provisioning provides a service oriented, api approach to managing credentials. To learn more about these rich capabilities, read here:
To aid in the adoption and utilization of the functionality mentioned above, this repo provides a reference client to illustrate how device(s) might interact with the provided services to deliver the desired experience. Specifically, the client demonstrates how a common "bootstrap" certificate (placed on n devices) can, upon a first-run experience:

Connect to IoTCore with stringent bootstrap credentials
Obtain a unique private key and "production" certificate
Present proof of ownership of the production credentials
Prompt the execution of a provisioning template (custom provisioning logic)
Rotate the certificates (decommission bootstrap, promote new cert)
Test the rights of the newly acquired certificate.
Dependencies of the solution
Intended to be compatible with AWS Greengrass ... this solution depends on a python library (asyncio) which is only available w/ python 3.7 and above. Please ensure your solution has at least this version.

A .NET Core port of the reference client application is available within the dotnet-core folder - this does not currently support certificate rotation feature available on the Python version.
