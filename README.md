# WEEK 3 | PROJECT MODULE 1 — Password Cracking with John the Ripper

## 📌 Project Overview

As part of my Cybersecurity Internship at **Networkwalks**, Week 3 focused on understanding password security and password recovery techniques using **John the Ripper (JTR)** and **Johnny**, its graphical user interface.

The objective of this practical lab was to recover the password of protected PDF files by extracting their password hashes and performing controlled password-cracking attacks (dictionary attacks) in a legal and authorized laboratory environment — both through Networkwalks' browser-based Dictionary Attack Lab and through the desktop JTR/Johnny workflow.

This project provided hands-on experience with password hashes, password-cracking methodologies, wordlist-based attacks, and the importance of strong password policies.

---

## 🎯 Objectives

- Understand how password-protected files store password hashes.
- Extract a password hash from an encrypted PDF file.
- Use an online hash-extraction tool to convert a locked PDF into a crackable hash format.
- Use John the Ripper to perform password recovery.
- Use the Johnny GUI to interact with John the Ripper more easily.
- Understand the relationship between password complexity/wordlist size and cracking success.
- Demonstrate why strong passwords are essential for security.

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| **John the Ripper (JTR)** | Password hash cracking and password recovery |
| **Johnny** | Graphical interface for John the Ripper |
| **Windows** | Testing environment |
| **Online HashCrack** | Extracting the `$pdf$` password hash from a protected PDF |
| **Networkwalks Password Cracker (Dictionary Attack Lab)** | Browser-based simulation of a wordlist/dictionary attack against a PDF hash |
| **Notepad** | Saving and preparing the extracted hash |

---

## 🔬 Methodology

### 1. Extracting the PDF Hash

A password-protected PDF was used as the target file in the authorized lab environment. The PDF was uploaded to an online hash-extraction utility to obtain the `$pdf$` password hash required by John the Ripper.

<p align="center">
  <img src="SCREENSHOTS/Screenshot%202026-08-28%20012523.png" alt="Uploading a locked PDF to the hash extraction tool" width="700">
</p>

<p align="center">
  <img src="SCREENSHOTS/Screenshot%202026-08-28%20012449.png" alt="Extracted PDF hash output" width="700">
</p>

The hash was verified to ensure that unnecessary characters were removed and that it was stored in the correct `$pdf$…` format for John the Ripper.

### 2. Dictionary Attack Simulation (Networkwalks Lab)

Before moving to the desktop tool, the extracted hash was tested against the Networkwalks **Password Cracker — Dictionary Attack Lab**, which hashes every word in a wordlist and matches it against the target PDF hash, mirroring the logic John the Ripper uses internally.

The first attempt used the built-in 100-password list, which was insufficient:

<p align="center">
  <img src="SCREENSHOTS/Screenshot%202026-08-28%20012309.png" alt="Dictionary attack in progress — access denied with small wordlist" width="700">
</p>

<p align="center">
  <img src="SCREENSHOTS/Screenshot%20%28231%29.png" alt="Full browser view of the dictionary attack lab" width="700">
</p>

Loading a larger, more targeted wordlist (`fasttrack.txt`, 221 words) allowed the attack to succeed:

<p align="center">
  <img src="SCREENSHOTS/Screenshot%202026-08-28%20012140.png" alt="Password cracked successfully — good-luck" width="700">
</p>

This step reinforced a key lesson: **cracking success depends directly on wordlist quality and coverage**, not just raw attempt count.

### 3. Configuring Johnny

Johnny was installed and configured as the graphical interface for John the Ripper, pointed at the `john.exe` executable inside the John the Ripper (Jumbo) installation directory.

<p align="center">
  <img src="SCREENSHOTS/Screenshot%202026-08-28%20011321.png" alt="Johnny settings pointing to the John the Ripper executable" width="700">
</p>

### 4. Loading the Hash and Running the Attack

The extracted `$pdf$` hash was imported into Johnny, and a new password-cracking attack was started against several target PDFs. John the Ripper processed each hash and successfully recovered the original passwords:

<p align="center">
  <img src="SCREENSHOTS/Screenshot%202026-08-28%20012056.png" alt="Johnny — password1 cracked" width="700">
</p>

<p align="center">
  <img src="SCREENSHOTS/Screenshot%202026-08-28%20011719.png" alt="Johnny — 1qaz2wsx cracked" width="700">
</p>

<p align="center">
  <img src="SCREENSHOTS/Screenshot%202026-08-28%20011652.png" alt="Johnny — good-luck cracked" width="700">
</p>

Once each password was recovered, it was used to unlock the corresponding protected PDF.

### 5. Flags Captured

Successfully completing each stage of the lab returned a unique flag, confirming the exercise was completed correctly:

<p align="center">
  <img src="SCREENSHOTS/Screenshot%202026-08-28%20013637.png" alt="Flag captured: networkwalks_persistence_jtr" width="450">
  &nbsp;&nbsp;
  <img src="SCREENSHOTS/Screenshot%202026-08-28%20013133.png" alt="Flag captured: networkwalks_flag" width="450">
</p>

<p align="center">
  <img src="SCREENSHOTS/Screenshot%202026-08-28%20012244.png" alt="Flag captured: cybersecurity_flag_captured" width="450">
</p>

---

## 💻 Example Workflow

```
Protected PDF
     │
     ▼
Extract PDF Hash (Online HashCrack)
     │
     ▼
Save Hash → hash1.txt
     │
     ▼
Test with Dictionary Attack Lab (wordlist sizing)
     │
     ▼
Load Hash into Johnny
     │
     ▼
Start Password Attack (John the Ripper)
     │
     ▼
Password Recovered
     │
     ▼
Unlock Protected PDF
```

---

## 🧠 Key Cybersecurity Concepts Learned

**Password Hashing**
A password hash is a one-way representation of a password. Instead of storing the original password directly, systems store its hash. Weak passwords, however, can potentially be recovered through password-cracking techniques.

**Password Cracking**
Password cracking involves attempting to discover the original password from a password hash. Tools such as John the Ripper automate this process using different attack techniques (dictionary, brute-force, rule-based, hybrid).

**Wordlist Quality Over Brute Force**
The 100-password built-in list failed, while a 221-word targeted list (`fasttrack.txt`) succeeded. This demonstrated that a well-curated, context-relevant wordlist can outperform a larger but generic one.

**Password Complexity**
Short and predictable passwords (`password1`, `1qaz2wsx`, `good-luck`) were recovered quickly, reinforcing why length and randomness matter far more than superficial complexity rules.

**Security Awareness**
The exercise highlighted why organizations should implement:
- Strong password policies
- Long and random passwords (not just predictable substitutions)
- Multi-factor authentication (MFA)
- Secure password hashing algorithms
- Account lockout and rate-limiting mechanisms
- Regular security assessments

---

## 📚 Skills Developed

- Password security fundamentals
- Hash extraction and analysis (`$pdf$` format)
- Password recovery workflows
- John the Ripper (JTR)
- Johnny GUI
- Dictionary/wordlist-based attacks
- PDF password protection mechanics
- Cybersecurity laboratory methodology
- Security assessment techniques

---

## ⚠️ Ethical & Legal Considerations

This activity was performed strictly for **educational and cybersecurity training purposes** within an authorized laboratory environment (Networkwalks Academy labs and test files created for this exercise).

Password-cracking tools should only ever be used against systems, files, or hashes for which explicit authorization has been obtained. Unauthorized password cracking or access to protected information may violate organizational policies and applicable laws.

---

## ✅ Project Outcome

Successfully completed a practical password-security exercise using John the Ripper, Johnny, and a browser-based dictionary attack simulator — gaining hands-on experience in extracting password hashes, performing controlled password-recovery attacks, and understanding the security implications of weak passwords and wordlist selection.

This project strengthened my practical understanding of offensive security techniques and defensive password-security practices as part of my Cybersecurity Internship at Networkwalks.

---

## 🏷️ Topics

`Cybersecurity` `Ethical Hacking` `Password Cracking` `John the Ripper` `JTR` `Johnny` `Password Security` `Hashing` `Penetration Testing` `Security Testing` `Networkwalks` `Cybersecurity Internship`
