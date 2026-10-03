# Networkwalks B083F – Week 3 Password Cracking Report

**Program:** Cybersecurity & Ethical Hacking Internship – Networkwalks
**Batch:** B083F
**Author:** Ummaima Rafique
**Date:** October 2026

---

## 1. Executive Summary

This report documents the password cracking activities performed during Week 3 of my internship. The objective was to recover passwords from three encrypted PDF files using John the Ripper (JTR) in Kali Linux and the Networkwalks online password cracking tools.

All three PDFs were successfully cracked. The exercise demonstrated why weak, common passwords offer no real protection against dictionary attacks.

---

## 2. Tools Used

| Tool | Purpose |
|---|---|
| pdf2john | Extract a crackable hash from a PDF file |
| John the Ripper | Command-line dictionary attack tool |
| rockyou.txt | Wordlist used by John |
| NW Hash Calculator | Browser tool to extract PDF hash |
| NW Password Cracker | Browser tool to crack PDF hash |

---

## 3. Activities Performed

### 3.1 Password Cracking with John the Ripper

I used pdf2john to extract the hash from each PDF, cleaned the hash file to remove the filename prefix, and then ran John against the rockyou.txt wordlist.

Commands used:

- pdf2john "/media/sf_downloads/My Locked PDF1.pdf" > hash1.txt
- cut -d: -f2 hash1.txt > hash1-clean.txt
- john --wordlist=/usr/share/wordlists/rockyou.txt hash1-clean.txt
- john --show hash1-clean.txt

The same steps were repeated for PDF2 and PDF3.

**Result:** All three passwords were recovered.

![JTR PDF1](screenshots/03-jtr-pdf1.png)
![JTR All 3](screenshots/04-jtr-all-3.png)

### 3.2 Password Cracking with Networkwalks Tools

For PDF1, I also demonstrated the browser-based Networkwalks tools:

1. Opened the Networkwalks Hash Calculator
2. Uploaded My Locked PDF1.pdf in the PDF tab
3. Copied the $pdf$ hash
4. Pasted the hash into the Networkwalks Password Cracker
5. Uploaded a custom wordlist and started the attack

**Result:** PDF1 password recovered as good-luck.

![Hash Calculator](screenshots/01-hash-calculator.png)
![Password Cracker](screenshots/02-password-cracker.png)

---

## 4. Results Summary

| PDF File | Password Cracked | Method |
|---|---|---|
| My Locked PDF1.pdf | good-luck | JTR + NW Tools |
| My Locked PDF2.pdf | password1 | JTR |
| My Locked PDF3.pdf | 1qaz2wsx | JTR |

**Flags captured:**

- nw{networkwalks_flag_260821_1}
- nw{networkwalks_persistence_jtr_270521}
- nw{cybersecurity_flag_captured_2608}

![Flag 1](screenshots/05-flag-1.png)
![Flag 2](screenshots/06-flag-2.png)
![Flag 3](screenshots/07-flag-3.png)

---

## 5. Problems Encountered & Solutions

| Problem | Solution |
|---|---|
| rockyou.txt was not extracted | Used sudo gunzip on rockyou.txt.gz |
| Hash file included the PDF filename | Used cut -d: -f2 to keep only the $pdf$ part |
| Browser Password Cracker froze with rockyou.txt | Built a small custom wordlist containing the expected passwords |
| pdf2john could not find the file | Used the full path /media/sf_downloads/... |

---

## 6. Conclusion

This week demonstrated that:

- Passwords like good-luck, password1, and 1qaz2wsx are cracked in seconds with a public wordlist.
- The right wordlist matters more than the cracking speed.
- Strong passwords (12+ characters, mixed case, numbers, symbols) are essential.

All activities were performed within the authorized Networkwalks lab environment.

---

## 7. Evidence

All screenshots are in the screenshots folder.

---

Prepared for the Networkwalks Cybersecurity Internship (Batch B083F).
