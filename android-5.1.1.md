## Def Con 2016 Android 5.1.1 DefCon-Secure

* Register a username and password at wifireg.defcon.org.
* Download the DigiCert Root Certificate and install locally
	* https://wifireg.defcon.org/digicertca.crt
	* Open phone settings
		* Security
		* Certificate Management
		* Install from storage
		* Navigate to and select digicertca.cer
		* Enter `Digicert DefCon CA` for a certificate name
		* Select Wi-Fi for credential use
		* Answer yes or ok if prompted to accept the certificate
* Connect and verify DefCon network and intermidiary certificate
	* Open phone settings
		* Wi-Fi
		* Select the `DefCon` network
		* EAP method = PEAP
		* Phase 2 Authentication = MSCHAPv2
		* CA certificate = Digicert DefCon CA
		* Identity = YOUR USERNAME
		* Anonymous Identity, leave blank
		* Password = YOUR PASSWORD
	* Select Connect
