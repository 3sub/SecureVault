# SecureVault — Encrypted File Manager

A client-side file vault that encrypts your files and their metadata directly in the browser. Nothing ever leaves your device.

## What it does

SecureVault lets you store files of any type (documents, images, audio, video, PDFs) in an encrypted container. The vault is a single `.vault` file you can save locally or move between devices. Decryption requires your secret key — without it, neither the file contents nor their names, types, or sizes are recoverable.

## Security

- **AES-256-GCM** encryption for all file content
- **PBKDF2-SHA256** key derivation with 600,000 iterations
- **Metadata encryption** — filenames, extensions, sizes, and dates are encrypted alongside the content
- No server, no network request, no telemetry — everything runs locally in the browser
- A random secure key generator is built in (estimator shows bit entropy)

## Usage

1. Open `vault_encrypted.html` in any modern browser
2. Enter or generate a secret key (minimum 64 bits of entropy recommended)
3. Add files by drag-and-drop or file picker
4. Click **Export .vault** to save your encrypted container
5. To restore: open the app, enter your key, then import the `.vault` file

## File format

The `.vault` file is a JSON document containing:
- The KDF parameters (algorithm, iterations, salt)
- One encrypted entry per file, each containing the metadata and content fused and encrypted together

Supported file types include text, Markdown, JSON, images, audio, video, PDF, and any binary format.

## Compatibility

Works in any browser that supports the [Web Crypto API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Crypto_API) (all modern browsers). No dependencies, no build step — a single HTML file.

## License

MIT — see `LICENSE` for details.  
The visual style is not included in this license and may not be reused.
