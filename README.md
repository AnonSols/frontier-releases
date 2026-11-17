# Frontier releases

Signed release files for **Frontier**, a coding agent for your terminal that works with many AI providers and checks every action before it runs. Frontier is in private beta.

This repository holds only the files a release is made of. The source code lives in a private repository.

## Install

1. Install Node.js 20 or newer.
2. Open the latest release on the Releases page and download `rabahh-frontier-<version>.tgz`.
3. In a terminal, run:

   ```
   npm install -g ./rabahh-frontier-<version>.tgz --ignore-scripts
   ```

4. Run `frontier setup` and follow the questions. You bring your own provider keys.

You can check the download first. Each release lists the file's SHA-256 fingerprint. Compare it with the fingerprint of your download:

- Windows PowerShell: `Get-FileHash .\rabahh-frontier-<version>.tgz -Algorithm SHA256`
- macOS or Linux: `shasum -a 256 rabahh-frontier-<version>.tgz`

## How updates work

Every release includes `manifest.json`, a small file that names the new version, the address of the package and the package's SHA-256 fingerprint. It carries an Ed25519 signature made with a private key that never leaves the maintainer's machine. The matching public key is built into Frontier.

At most every 6 hours, an installed Frontier reads `manifest.json`, checks the signature, downloads the package, checks the fingerprint and installs it with install scripts turned off. It never installs an older version, and it installs nothing if any check fails. You can turn automatic installs off with `"update": { "auto": false }` in `~/.frontier/settings.json`.

## Licence

Frontier is private beta software, provided to invited testers. The full terms are in the `LICENSE` file inside the package.
