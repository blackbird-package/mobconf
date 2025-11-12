```
pacman -S systemd-ukify
```
```
cp /usr/lib/kernel/uki.conf /etc/kernel/
```
```
nvim /etc/kernel/uki.conf
```
```
[UKI]
#Initrd=
#Microcode=
#Splash=
#PCRPKey=
#PCRBanks=
SecureBootSigningTool=systemd-sbsign
SecureBootPrivateKey=/etc/kernel/secure-boot-private-key.pem
SecureBootCertificate=/etc/kernel/secure-boot-certificate.pem
#SecureBootCertificateDir=
#SecureBootCertificateName=
#SecureBootCertificateValidity=
#SigningEngine=
SignKernel=true

#[PCRSignature:NAME]
#PCRPrivateKey=/etc/systemd/tpm2-pcr-private-key.pem
#PCRPublicKey=/etc/systemd/tpm2-pcr-public-key.pem
#Phases=
```
```
ukify genkey --config /etc/kernel/uki.conf
```
```
mkinitcpio -P
```
