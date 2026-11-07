# Milestone 3: A Guided Password-Hashing Experiment

## 1. Aim

The aim of this experiment is to understand how password hashing works using Python. It demonstrates how random salts generate different hashes, how correct and incorrect passwords are verified, and how hashing differs from encryption.

## 2. Tools and Technologies Used

- Python 3
- hashlib library
- secrets library
- hmac library
- PBKDF2-HMAC-SHA256 algorithm
- Visual Studio Code
- Windows PowerShell

## 3. Introduction

Password hashing is an important cybersecurity technique used to protect user passwords.

Instead of storing passwords directly, systems store their password hashes. During login, the entered password is hashed again and compared with the stored hash.

This experiment uses PBKDF2-HMAC-SHA256 with 100,000 iterations and a randomly generated 16-byte salt.

## 4. Working Procedure

1. Opened the supplied Python file in Visual Studio Code.
2. Used the provided dummy password: `dummy-practice-value`.
3. Generated two random salts using `secrets.token_bytes(16)`.
4. Generated two password hashes using PBKDF2-HMAC-SHA256.
5. Compared the two salts and hashes.
6. Verified the correct and incorrect dummy password values.
7. Performed empty-input and long-input boundary tests.
8. Executed the script using Windows PowerShell.

## 5. Experimental Results

### A. Salt and Hash Generation

Two different random salts were generated for the same dummy password.

- Salt 1: `ffe9489c26152291be53abe1c5233fa0`
- Salt 2: `43876219eece388c723ddf98605cce00`

The generated hashes were:

- Stored Hash 1: `8cb4a314924623a0e35eb91c487b2ff69dfd93b3b65d04904f40411432279e27`
- Stored Hash 2: `5106c942596a433b79bbe9722b9cd073a77c7fe68093fd64c506f746cc16a367`

**Observation:** The same password generated different hashes because different random salts were used.

### B. Password Verification

| Test | Expected result | Actual result |
|---|---|---|
| Different salts | True | True |
| Different hashes | True | True |
| Correct password | True | True |
| Wrong password | False | False |

**Observation:** The correct password matched the stored hash, while the wrong password did not match.

### C. Boundary and Failure Tests

| Test | Input | Actual result |
|---|---|---|
| Empty input | Empty byte string | False |
| Long input | 10,000 bytes | True |

**Observation:**

- The empty input did not match the stored password hash.
- The long input was successfully processed, and the derived hash length was 32 bytes.

The long-input test checks successful hash generation, not password-length validation.

## 6. Why Are Salts Important?

A salt is a random value added during password hashing.

Salts are important because:

- They make hashes different even when passwords are identical.
- They help protect against precomputed hash attacks.
- They make it harder for attackers to identify users with identical passwords.

A salt does not need to be kept secret.

## 7. Hashing vs Encryption

**Hashing:**
- A one-way process.
- Cannot normally be reversed to obtain the original password.
- Used for password verification.

**Encryption:**
- A reversible process when the correct decryption key is available.
- Used to protect data that must later be recovered.

Therefore, password hashing is not the same as encryption.

## 8. Security Observation

The experiment demonstrates password hashing using PBKDF2-HMAC-SHA256.

However, this educational script is not a complete production authentication system. Real applications also need secure password handling, appropriate password policies, rate limiting, and other authentication protections.

Only dummy values were used in this experiment. No real passwords or personal credentials were tested.

## 9. Conclusion

This experiment helped me understand the importance of password hashing and random salts in cybersecurity.

I successfully generated two different salts and hashes using the same dummy password. I also verified correct and incorrect password values and performed empty-input and long-input boundary tests.

The experiment demonstrated that password hashing is a one-way process and is different from encryption.

**Result:** The password-hashing experiment was successfully completed using Python.
