# ArcLedger downloads

This repository publishes the signed Windows installers for [ArcLedger](https://getarcledger.com). It contains release
files only; ArcLedger's source code isn't published here.

Each release has:
- `ArcLedger.Setup.<version>.exe`: the Windows installer, signed by **ArcanEdge LLC**;
- `SHA256SUMS.txt`: the SHA-256 of every file in the release;
- release notes.

## Check a download

In PowerShell, from the folder you downloaded to:

```powershell
Get-FileHash .\ArcLedger.Setup.0.1.2.exe -Algorithm SHA256
Get-AuthenticodeSignature .\ArcLedger.Setup.0.1.2.exe | Select-Object Status, @{n='Signer';e={$_.SignerCertificate.Subject}}
```

The hash must match the installer's line in that release's `SHA256SUMS.txt`. The signature must say `Valid`, with the
signer `CN=ArcanEdge LLC`.

Support: see [getarcledger.com/support.html](https://getarcledger.com/support.html).
