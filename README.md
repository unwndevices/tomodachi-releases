# Tomodachi System updates

What a Tomodachi downloads when it updates itself over Wi-Fi. Everything here is
built and signed by the release pipeline of the source repository; nothing is
edited by hand.

- `tomodachi/core/stable.json`, `tomodachi/core/dev.json`: one signed manifest per
  Update channel, served at `https://update.unwn.dev/tomodachi/core/<channel>.json`.
- Releases: the two images of each version (the firmware and the applets).

A manifest is `{"manifest": base64, "signature": base64}`: the signature is ECDSA
P-256 over SHA-256 of the decoded manifest bytes, which name each image by
address, length and SHA-256. A device installs nothing that does not verify
against this public key, whoever serves it:

```
-----BEGIN PUBLIC KEY-----
MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAE1L1iD2HP/eCJHVsB4/qGpYDbvexc
Z+d0TbIRUZke1wOlQ5+v2R1UEaxDIZGuwK1Oxnbfd6dkkgamnqXTMOHFeQ==
-----END PUBLIC KEY-----
```
