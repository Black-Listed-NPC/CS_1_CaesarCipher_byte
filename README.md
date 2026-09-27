# CS_1_CaesarCipher_byte

Caesar Cipher — Text Encryption/Decryption Tool (Web App)
**AVIP 2026 | CyberSecurity Track | Task 1**

🔗 **Live demo:** https://cs-1-caesarcipher-byte-rjqp.onrender.com
*(hosted on Render's free tier — may take 30–50s to wake up on first load)*

## What it does
A web app that encrypts and decrypts text using the classic Caesar Cipher
(letter-shift substitution). Non-alphabet characters — numbers, punctuation,
spaces — pass through unchanged, and letter case is preserved. The shift/key
is fully configurable. A command-line version is also included.

## Files
| File | Purpose |
|---|---|
| `app.py` | Flask backend — encrypt/decrypt logic + API route |
| `templates/index.html` | Web app page |
| `static/style.css` | Styling |
| `static/app.js` | Frontend logic (calls the API, updates output live) |
| `requirements.txt` | Python dependencies |
| `Procfile` | Start command for Render |
| `caesar_cipher.py` | Original CLI version (encrypt/decrypt logic + argparse CLI) |
| `sample_input.txt` | Example plaintext input |
| `sample_output.txt` | Corresponding ciphertext output (shift = 3) |
| `demo_transcript.txt` | Sample terminal session (CLI) |

## Usage

### Web app
Open the live link above, type or paste text, choose Encrypt/Decrypt, set a
shift value, and the output updates automatically.

### Command line
Encrypt text directly:
```bash
python caesar_cipher.py encrypt "Hello World" 3
# Output: Khoor Zruog
```

Decrypt text directly:
```bash
python caesar_cipher.py decrypt "Khoor Zruog" 3
# Output: Hello World
```

Process a file and save the result:
```bash
python caesar_cipher.py encrypt -f sample_input.txt 3 -o sample_output.txt
```

## How it works
- Each letter is shifted forward (`encrypt`) or backward (`decrypt`) by the
  given key, wrapping around the alphabet (A→Z, Z→A).
- Uppercase and lowercase are preserved.
- Any negative or >26 shift value is automatically normalized (`shift % 26`).
- Non-alphabetic characters are returned unchanged.
- The web app calls a Flask `/api/process` endpoint that runs this exact
  same logic and returns the result as JSON.

## Sample run
See `demo_transcript.txt` for a full terminal session showing encryption,
decryption, and file-based processing.

## Running locally
```bash
pip install -r requirements.txt
python app.py
# then open http://127.0.0.1:5000
```

## Deployment
Deployed on [Render](https://render.com) as a Python web service:
- **Build command:** `pip install -r requirements.txt`
- **Start command:** `gunicorn app:app`

## Tech stack
Python 3, Flask, gunicorn — no database, no external APIs.

---
*Task 1 — CyberSecurity Track — [Arithmatrix Virtual Internship Program (AVIP) 2026](https://arithmatrix.co) — [@B.Y.T.E by Arithmatrix](https://linkedin.com)*
