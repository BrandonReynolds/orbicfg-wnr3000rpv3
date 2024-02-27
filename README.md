### This is a fork of the original tool by https://github.com/Fysac/orbicfg

 - A single modification was made to support the WNR3000RPv3. This change may break support for other devices. Goal was to quickly decrypt and encrypt the file format.

# orbicfg
This tool was designed to decrypt Netgear Orbi configuration backups. It has been tested against the RBR50 (firmware version 2.3.5.30).

Usage
./orbicfg <config backup (e.g. NETGEAR_Orbi.cfg)>

Details
Configuration backups and restores are handled by /bin/datalib. When creating a backup, datalib encrypts the raw key-value pairs of the router's configuration using a XOR cipher. It generates the keystream by seeding uClibc's rand(3) implementation with a hardcoded integer and successively calling rand() for every 4 bytes of the plaintext. The seed value is also included in the header of the encrypted backup, giving end users all the information they need to decrypt it.
