# Let's create a README.txt file with the key points we outlined earlier.

readme_content = """\
README - UDP Secure Communication (Alice & Bob)

1. Purpose
----------
This project implements a UDP-based authentication and secure communication system between Alice (host) and Bob (client).
The program follows the assignment's two main steps:
1) Authentication & Key Establishment (RSA + SHA-1)
2) Secure Chat (RC4 encryption + SHA-1 integrity check)

2. File Structure
-----------------
key_setup.py               # Generates RSA keys, password file, and fingerprint

Alice/
  host_step1.py             # Step 1 only (handshake)
  host.py                   # Step 1 + Step 2 (full secure chat)
  password.txt              # Auto-generated user credentials
  private.pem               # Alice's RSA private key
  public.pem                # Alice's RSA public key

Bob/
  client_step1.py           # Step 1 only (handshake)
  client.py                 # Step 1 + Step 2 (full secure chat)
  alice_fingerprint.txt     # SHA-1 fingerprint of Alice's public key

3. Setup Instructions
----------------------
1) Install dependencies:
   pip install pycryptodome

2) Run key_setup.py to generate all necessary keys and files:
   python key_setup.py

This will create:
- Alice's RSA keys (private.pem, public.pem)
- password.txt with username & SHA-1 hashed password
- Bob's alice_fingerprint.txt

4. Running Step 1 (Handshake Only)
----------------------------------
Terminal 1 (Alice):
    python Alice/host_step1.py

Terminal 2 (Bob):
    python Bob/client_step1.py

Input:
    Username: Bob
    Password: ALICE123

Expected Result:
- Both sides display "Connection Okay"
- Both print the same session key (ssk)

5. Running Step 1 + Step 2 (Full Secure Chat)
---------------------------------------------
Terminal 1 (Alice):
    python Alice/host.py

Terminal 2 (Bob):
    python Bob/client.py

Input:
    Username: Bob
    Password: ABC12345

After handshake:
- Chat messages are encrypted with RC4
- Messages are verified using SHA-1 integrity check
- Bob can end the chat by typing "exit"

6. Notes
--------
- Works on 127.0.0.1 for local testing
- No GUI; all interaction is in terminal
- Password in key_setup.py can be changed, must be exactly 8 characters
- If fingerprint does not match, Bob aborts connection
"""

# Save README.txt
readme_path = "/mnt/data/README.txt"
with open(readme_path, "w") as f:
    f.write(readme_content)

readme_path
