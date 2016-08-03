## Def Con 2016 Linux Wpa_supplicant DefCon-Secure

* Register a username and password at wifireg.defcon.org.
* Download the DigiCert Root Certificate and install locally
	* https://wifireg.defcon.org/digicertca.crt
	* /etc/ssl/certs/digicertca.crt
* Run the following command to change the certificate into a supported format
	* `openssl x509 -in digicertca.crt -out digicertca.pem -outform PEM`
* Create a new wpa_supplicant profile or add to your existing one at /etc/wpa_supplicant.conf
* Enter the following as a base configuration (plaintext password)
```
network={
	ssid="DefCon"
	captive_check=0
	boost_flags=0
	key_mgmt=WPA-EAP IEEE8021X
	eap=PEAP
	identity="INSERT USER"
	password="INSERT PASSWORD"
	ca_cert="/etc/ssl/certs/digicertca.pem"
	phase2="auth=MSCHAPV2"
	proactive_key_caching=0
}
```
* Start wpa_supplicant via your choosen method.
