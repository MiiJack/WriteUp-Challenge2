# WriteUp-Challenge2
site : root-me.org

CHALLENGES/NETWORK

---

Wireshark was utilized to successfully address all of the following challenges by opening the corresponding file whenever possible.
## FTP - authentification
On the GUI, we can just use ``Ctrl+Shift+Alt+T`` (Analyze - Follow - TCP Stream). We just have to extract the password by looking at the keyword : ``PASS``
```sh
PASS : c******0
```
## TELNET - authentification
Same as above, we just have to follow the TCP Stream and analyze it's content. We can see that there's a password.
```sh
PASS : ****
```
## ETHERNET - trame 
We can see that it looks like an hexadecimal. So let's convert it into a text.
Extract of said text : ``Authorization: Basic Y*****************==``, the string after the ``Basic`` contains Letters and Numbers with only ``=`` as special character. This tells us it might be encoded in base64. By decoding said string, we will get the password
```sh
PASS : c***********l
```
## TWITTER - authentification
We can observe that it's an HTTP, by going into the ``Authorization`` section, we can get the ``Credentials`` = ``usertest:********``
```sh
PASS : p******d
```
## BLUETOOTH - Unknown file
On the app, go to the tab ``Wireless`` & ``Bluetooth Device``, we can get the name of the device under ``Name``: ``GT-S7390G`` and its MAC ``0*:**:**:**:**:*6`` under ``BD_ADDR``.
We can get the sha-1 hash checksum of the level by following the example ``AB:CD:EF:12:34:56myPhone``. So we will have to concatenate the MAC address ``in capitals`` with the name of the device, and then calculate the resulting sha-1.
```sh
PASS : c**************************************b
```
## SIP - authentification
We can see in the first line that there is a plain text
```sh
"PLAIN" ****
```
```sh
PASS : ****
```
