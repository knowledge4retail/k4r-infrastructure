# Accessing K4R DEV/Sandbox Deployment


- [Accessing K4R DEV Deployment](#accessing-k4r-dev-deployment)
  - [Attached Files](#attached-files)
  - [Configuring the Certificates](#configuring-the-certificates)
    - [__Linux (Ubuntu)__](#linux-ubuntu)
      - [Adding PKCS12 Client Certificate](#adding-pkcs12-client-certificate)
    - [__Windows__](#windows)
      - [Adding PKCS12 Client Certificate](#adding-pkcs12-client-certificate-1)
    - [__for FireFox on Windows or Linux__](#for-firefox-on-windows-or-linux)
      - [Adding Client Certificate](#adding-client-certificate)
    - [__For Postman__](#for-postman)
  - [ENDPOINTS](#endpoints)
## Attached Files

- `k4r-dev-keystore.p12` Client Certificate in PKCS12 Format for Linux/Windows for the DEV environment
- `k4r-sandbox-client.p12` Client Certificate in PKCS12 Format for Linux/Windows for the Sandbox environment

## Configuring the Certificates


_**Repeat the same steps below using the `k4r-sandbox-client.p12` file in order to get access to the sandbox environment**_


### __Linux (Ubuntu)__

#### Adding PKCS12 Client Certificate

Chrome:
Follow Instructions [here](https://support.globalsign.com/digital-certificates/digital-certificate-installation/install-pkcs12-file-linux-ubuntu-using-chrome)

Restart the browser (Chrome/Edge ...)

Special instructions for Firefox and Postman below.

### __Windows__

#### Adding PKCS12 Client Certificate

double click on the `k4r-dev-keystore.p12` and install it for the local user


Restart the browser (Chrome/Edge/IE)

Special instructions for Firefox and Postman below.

### __for FireFox on Windows or Linux__

#### Adding Client Certificate

Type in the URL Bar `about:preferences#privacy` (Or from Options Menu => Privacy & Security)
and then look for Certificates => View Certificates => and import the client certificate `k4r-dev-keystore.p12` manually

Or programmatically: 

``` bash
# Find the path of your Firefox profile
find ~/.mozilla/firefox -name "cert8.db"

# Assuming that your DB path is ~/.mozilla/firefox/xxxxx.default/cert8.db
pk12util -i path/to/bundle.p12 -d ~/.mozilla/firefox/xxxxx.default/cert8.db -W theProvidedPasswordInTheEmail

```

Close the browser and reopen it.

### __For Postman__

- Client Certificate

File => Settings => Certificates Tab => Client Certificates => Add Certificate => PSX => Choose `k4r-dev-keystore.p12` then add the passphrase (password) and save

## ENDPOINTS

- [Hetida Designer DEV](https://hetida.dev.knowledge4retail.org/)

- [Hetida Designer Sandbox](https://hetida.sandbox.knowledge4retail.org/)

- [Digital-Twin-api DEV](https://dt-api.dev.knowledge4retail.org/k4r/swagger-ui.html)

- [Digital-Twin-api Sandbox](https://dt-api.sandbox.knowledge4retail.org/k4r/swagger-ui.html)
  
- [Distance-Matrix-api DEV](https://distance-matrix-api.dev.knowledge4retail.org/distancematrixapi/swagger-ui.html)

- [Distance-Matrix-api Sandbox](https://distance-matrix-api.sandbox.knowledge4retail.org/distancematrixapi/swagger-ui.html)

- [KnowRob DEV ](https://knowrob.dev.knowledge4retail.org/)

- [KnowRob Sandbox](https://knowrob.sandbox.knowledge4retail.org/)
