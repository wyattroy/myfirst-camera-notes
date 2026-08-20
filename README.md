# Notes for MyFirst

A private, password-gated document. Published with GitHub Pages.

The page body is encrypted at rest. `payload.js` holds AES-256-GCM ciphertext
keyed by PBKDF2-SHA256 (250,000 iterations) over the password; `index.html`
derives the key in the browser and injects the decrypted markup. There is no
plaintext of the document, and no copy of the images, anywhere in this repo.

## Rebuilding

The source (`src/content.html`, `src/img/`) is deliberately not committed.
With it in place:

```
node src/build.mjs <password>
```

That inlines the images as data URIs, encrypts everything, and rewrites
`payload.js`. Commit and push to publish.
