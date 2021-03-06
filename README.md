# decred-release
Decred Release

This repository contains the decred installers and the installer manifests.

For the binary archives, binary manifests and release notes please 
go to [decred-binaries](https://github.com/decred/decred-binaries).

## Verifying dcrinstall

Each release contains a manifest file with sha256 hashes for the
installers in that release.  To verify these, you will need:

* SHA256 - Once you download your file(s), you need to check their
  SHA256 hashes, so you may need to download a tool to do this,
  depending on your OS.
* GnuPG or PGP - This is required to import public keys and verify
  signatures. Examples below use GnuPG.

The steps to verify the binaries are as follows:

1. Download the file manifest (manifest-dcrinstall-vX.X.X.txt), the signature for the file manifest (manifest-dcrinstall-vX.X.X.txt.asc), and the installer for your OS from [here](https://github.com/decred/decred-release/releases).
2. Obtain the SHA256 value for the installer for your OS and check that it matches the value in the file manifest, e.g. for 64-bit Linux

   ```
   $ sha256sum dcrinstall-linux-amd64-v0.3.0
   a53004599daeab51c0e86af026748b7aa55ff9e5d4844bef3b7d8ccf8a5d72a9  dcrinstall-linux-amd64-v0.3.0
   ```

3. Import the Decred Release Signing Key in GnuPG.
   ```
   $ gpg --keyserver pgp.mit.edu --recv-keys 0x518A031D
      gpg: requesting key 518A031D from hkp server pgp.mit.edu
      gpg: /home/user/.gnupg/trustdb.gpg: trustdb created
      gpg: key 7608AF04: public key "Decred Release <release@decred.org>" imported
      gpg: Total number processed: 1
      gpg: imported: 1 (RSA: 1)
   ```
4. Verify the signature for the file manifest is valid and created by
the Decred Release Signing Key.

	```
   $ gpg --verify manifest-dcrinstall-v0.3.0.txt.asc
      gpg: assuming signed data in `manifest-dcrinstall-v0.3.0.txt'
      gpg: Signature made Wed 27 Jan 2016 08:56:59 PM UTC using RSA key ID 518A031D
      gpg: Good signature from "Decred Release <release@decred.org>"
      gpg: WARNING: This key is not certified with a trusted signature!
      gpg: There is no indication that the signature belongs to the owner.
          Primary key fingerprint: FD13 B683 5E24 8FAF 4BD1 838D 6DF6 34AA 7608 AF04
           Subkey fingerprint: F516 ADB7 A069 852C 7C28 A02D 6D89 7EDF 518A 031D
   ```

The installer for your platform is now verified and you can be confident
it was generated by the Decred team.
