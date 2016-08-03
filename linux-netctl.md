## Def Con 2016 Linux Netctl DefCon-Secure

* Register a username and password at wifireg.defcon.org.
* Download the DigiCert Root Certificate and install locally
	* https://wifireg.defcon.org/digicertca.crt
	* /etc/ssl/certs/digicertca.crt
* Run the following command to change the certificate into a supported format
	* `openssl x509 -in digicertca.crt -out digicertca.pem -outform PEM`
* Create a new netctl profile, generally in /etc/netctl/defcon-secure
* Enter the following as a base configuration (plaintext password)
```
Description="Def Con Secure Wifi"
Interface="YOUR INTERFACE HERE"
Connection=wireless
Security=wpa-configsection
IP=dhcp
WPAConfigSection=(
	'priority=1'
	'ssid="DefCon"'
	'key_mgmt=WPA-PEAP'
	'eap=PEAP'
	'proto=RSN'
	'pairwise=CCMP'
	'group=CCMP'
	'phase2="auth=MSCHAPV2"'
	'identity="INSERT USERNAME"'
	'password="INSERT PLAINTEXT PASSWORD"'
	'ca_cert2="/etc/ssl/certs/digicert.pem"'
)
```
* Encrypted password (optional, but suggested)
	* `tr -d '\n' | iconv -t utf16le | openssl md4`
	* Enter your password, press Enter, followed by immediately Ctrl+d to exit
	* Copy text after =
	* Alter your netctl configuration from above, and replace "password="
	* `'password="xxx"'` to `'password=hash:<INSERT HASH>'`
* Execute `netctl start defcon-secure` to start the new profile.
	* You will need to stop any existing configs, such as the hotel or your hotspot.
