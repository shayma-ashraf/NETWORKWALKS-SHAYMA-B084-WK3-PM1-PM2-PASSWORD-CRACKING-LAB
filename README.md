# 🔑 Password Cracking: Networkwalks Tools + John the Ripper (JTR)

**My Week 3 project for Networkwalks cybersecurity: recovering a weak PDF password two different ways to see how dictionary attacks work.**

---

## 📌 Project Overview

For Week 3, I cracked the password on a protected PDF file (`My Locked PDF1.pdf`) provided by the course, using two completely different approaches that land on the same idea: extract a hash, then dictionary-attack it. First with two free Networkwalks browser tools, then with John the Ripper and its GUI, Johnny.

## 🎯 Objectives

- Understand the difference between encryption (two-way) and hashing (one-way)
- Extract a crackable hash from a password-protected PDF
- Run a dictionary attack against that hash using the Networkwalks Hash Calculator + Password Cracker
- Install and configure John the Ripper (JTR) and Johnny on Windows
- Crack the same PDF's password with JTR and compare results

---

## 🪜 What I Did

### W3-PM2: Networkwalks Hash Calculator + Password Cracker

1. Downloaded `My Locked PDF1.pdf` from the course lab page.
2. Uploaded it to the **Hash Calculator** (`networkwalks.com/hash-calculator`), which extracted a `$pdf$...` hash entirely in-browser (no upload to a server).
3. Pasted that hash into the **Password Cracker**, left the built-in 100-word list selected, and clicked Start Cracking.
4. It matched **`password1`** after trying 91 of 100 words.

![Hash Calculator](w3-pm2-networkwalks-tools/screenshots/01_hash_calculator.png)
![Password Cracker](w3-pm2-networkwalks-tools/screenshots/02_password_cracker.png)

### W3-PM1: John the Ripper (JTR) + Johnny

1. Downloaded John the Ripper (jumbo, Windows) from openwall.com and extracted it with 7-Zip.
2. Downloaded and installed Johnny (the JTR GUI), then pointed it at `john.exe` in Settings.
3. Extracted the PDF's hash using onlinehashcrack.com's PDF Hash Extractor, saved it as `hash1.txt`.
4. Loaded `hash1.txt` into Johnny and clicked **Start new attack**.
5. Johnny cracked it to **`password1`** as well, matching the first method exactly.
6. Opened the PDF with the password and captured the flag.

![Johnny cracked password](w3-pm1-jtr-johnny/screenshots/03_johnny.png)
![Unlocked PDF flag](w3-pm1-jtr-johnny/screenshots/04_unlocked_flag.png)

---

## 🐞 Problems I Ran Into and How I Fixed Them

### Problem 1. My downloaded John the Ripper file wouldn't "Extract All"
The file was a `.7z` archive, and Windows only offered "Extract All", which doesn't open `.7z` files properly, because 7-Zip wasn't installed yet.

**Fix:** Installed 7-Zip from 7-zip.org, after which right-clicking the file showed a proper 7-Zip extract option.

### Problem 2. Wasn't sure the hash loaded into Johnny
After pointing Johnny at `john.exe`, I was still on the Settings screen and didn't see a password row, so I assumed nothing had loaded.

**Fix:** The password list lives under the **Passwords** tab on the left, not Settings. Once I clicked over, the loaded hash (format: PDF) was right there, and the status bar had already confirmed "1 left" the whole time.

---

## 💡 What I Learned

- **Encryption vs. hashing:** encryption is reversible with the right key; hashing is one-way, so "cracking" a password hash means guessing candidates and hashing each one until it matches, never reversing the hash directly.
- **Dictionary attacks are fast against weak passwords:** a 100-word list was enough to break this PDF's password in seconds.
- **Two completely different tools agreeing is strong evidence:** getting `password1` from both a browser tool and John the Ripper confirmed the result.
- **Where things live matters:** a tool loading data doesn't always mean you're looking at the right screen to see it.

## 📄 Full Report

The complete penetration testing report, with risk analysis and recommendations, is in the [`report`](report/) folder.

## 🔐 Ethical Use

This file was provided specifically for this exercise by the course. I will only attempt to recover passwords on files I own or have explicit permission to test.

## 🔗 Tools and Resources

- Networkwalks Hash Calculator: https://networkwalks.com/hash-calculator/
- Networkwalks Password Cracker: https://networkwalks.com/password-cracker/
- John the Ripper: https://www.openwall.com/john/
- Johnny (JTR GUI): https://openwall.info/wiki/john/johnny

## 👤 Author

**Shayma Ashraf**
Networkwalks Cybersecurity, Batch B084
LinkedIn: www.linkedin.com/in/shayma-ashraf-4b1135233

**Program:** Cybersecurity at Networkwalks | **Week:** 3 | **Project:** Password Cracking (WK3-PM1, WK3-PM2)
