# Paranoid Qrypto: XRP Airgap Bridge

![Apache 2.0 License](https://img.shields.io/badge/License-Apache_2.0-ffd700.svg)
![Version](https://img.shields.io/badge/Version-1.0.0-informational.svg)
![Maintained](https://img.shields.io/badge/Maintained-Yes-green.svg)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)

<p align="center">
  <img src="docs/logo.png" alt="Paranoid Qrypto Logo" width="128">
</p>

A 100% client-side, single-file HTML tool for securely managing the online parts of an air-gapped XRP transaction workflow. This tool allows you to fetch account information and broadcast a signed transaction to the XRP Ledger without ever exposing your private keys to an online machine.

---

## Security-First Philosophy

This tool was built with a "paranoid" mindset, prioritizing security and transparency above all else.

*   **100% Client-Side:** All operations happen directly in your web browser. No data, keys, or transaction information is ever sent to any server, except for the final, signed transaction blob which is broadcast directly to the public XRP Ledger nodes.
*   **Works Completely Offline:** The tool is a single HTML file with no external dependencies. You can download it and run it on a completely air-gapped computer to generate QR codes from signed transaction data.
*   **Fully Auditable:** The entire source code is contained within a single, human-readable file. There are no hidden packages or compiled code. What you see is what you get.

## Key Features

*   **Fetch Account Info:** Safely get your account's current `Sequence` number and a suggested `LastLedgerSequence` from the live network to prepare for an offline transaction.
*   **Submit Signed Transaction:** Broadcast a signed transaction blob (pasted or scanned via QR code) to the XRP Ledger.
*   **Generate QR Code:** A general-purpose utility to create a QR code from any text or data, useful for moving a signed transaction blob from an offline machine.
*   **Regenerate QR Code:** A robust "lifesaver" utility that can decode blurry, low-quality, or difficult-to-read QR codes and regenerate them as clean, scannable images.

## How to Use: The Air-Gapped Workflow

This tool acts as the secure online interface for your offline cold wallet.

#### Step 1: On Your **Online** Machine

1.  Open the `XRP-Airgap-Bridge.html` file.
2.  Go to the **"Fetch Account Info"** tab.
3.  Enter your public XRP address (`r...`) and click "Fetch Account Info".
4.  Securely transfer the `Sequence` and `LastLedgerSequence` numbers to your offline machine (e.g., by writing them down).

#### Step 2: On Your **Offline** (Air-Gapped) Machine

1.  Using your preferred offline wallet software, construct your transaction (e.g., a payment with destination, amount, etc.).
2.  Use the `Sequence` and `LastLedgerSequence` you just transferred.
3.  Sign the transaction with your private key. This will produce a long hexadecimal string (the "signed transaction blob").
4.  (Optional if you dont have ability to turn your signed transaction blob with your wallet) Use a copy of this tool on your offline machine to turn the long transaction blob into a QR code using the "Generate QR" tab.

#### Step 3: Back on Your **Online** Machine

1.  Go to the **"Submit Signed TX"** tab.
2.  Either paste the hexadecimal blob directly into the text box or click **"Scan Signed TX QR"** to use your camera.
3.  Verify the network selection and click **"Submit Transaction"**.
4.  The tool will broadcast your transaction to the XRP Ledger and show you the final response.

---

## Dependencies & Verification

This tool is designed to be a secure, self-contained HTML file. The following third-party libraries have been downloaded and included locally in the `js/` directory.

To ensure transparency and allow for independent verification, the exact versions, source links, and SHA-256 file hashes are provided below.

### 1. xrpl.js

*   **Version:** `4.3.0`
*   **Purpose:** The official library for interacting with the XRP Ledger.
*   **Source of Truth (NPM):** [https://www.npmjs.com/package/xrpl/v/4.3.0](https://www.npmjs.com/package/xrpl/v/4.3.0)
*   **Direct Download Link:** [https://cdn.jsdelivr.net/npm/xrpl@4.3.0/build/xrpl-latest-min.js](https://cdn.jsdelivr.net/npm/xrpl@4.3.0/build/xrpl-latest-min.js)
*   **SHA-256 Hash:** `d4814cdd1fe22421169c51dbdf2dadc84f48d0fc0dba96bb49e1e1d10158c642`

### 2. jsQR.js

*   **Version:** `1.4.0`
*   **Purpose:** QR code decoding library used for scanning.
*   **Source of Truth (NPM):** [https://www.npmjs.com/package/jsqr/v/1.4.0](https://www.npmjs.com/package/jsqr/v/1.4.0)
*   **Direct Download Link:** [https://cdn.jsdelivr.net/npm/jsqr@1.4.0/dist/jsQR.js](https://cdn.jsdelivr.net/npm/jsqr@1.4.0/dist/jsQR.js)
*   **SHA-256 Hash:** `aec81b459d4e3856885fca04b497474227396ab793daedf402fd80f7b9fcc337`

### 3. qrcode-generator

*   **Version:** `1.4.4`
*   **Purpose:** QR code generation library used for the "Regenerate QR" feature.
*   **Source of Truth (NPM):** [https://www.npmjs.com/package/qrcode-generator/v/1.4.4](https://www.npmjs.com/package/qrcode-generator/v/1.4.4)
*   **Direct Download Link:** [https://cdn.jsdelivr.net/npm/qrcode-generator@1.4.4/qrcode.min.js](https://cdn.jsdelivr.net/npm/qrcode-generator@1.4.4/qrcode.min.js)
*   **SHA-256 Hash:** `514f978a588b2eda0f942d8957dbab047c9b7eb68e723118fa2cbab6028d41e4`

---

## License

This project is licensed under the **Apache License 2.0**. Please see the `LICENSE` file for full details. A `NOTICE` file is also included for attribution purposes.

## Disclaimer

This tool is provided "AS IS", WITHOUT WARRANTY OF ANY KIND, either express or implied. The user assumes all risks associated with its use. Always verify critical information and test with small amounts before performing significant transactions.

## Bug Reports & Feedback

If you find a bug or have a feature request, please open an issue on the [GitHub Issues page](https://github.com/paranoid-qrypto/xrp-airgap-bridge/issues).
