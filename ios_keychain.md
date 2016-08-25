#Keychain invalid(http://stackoverflow.com/questions/35402862/this-certificate-has-an-invalid-issuer-keychain-marks-all-certificates-as-inv)

```
	
In Keychain access, -> View -> Show Expired Certificates, then in your login keychain click on expired certificate and delete it. I also had the same expired certificate in my System keychain, so I deleted it from there too.

-> After deleting the expired cert from the login and System keychains,download certificate from below link and open with keychain.

Download https://developer.apple.com/certificationauthority/AppleWWDRCA.cer and add it to Keychain access > certificates (which expires on 2023)

```
