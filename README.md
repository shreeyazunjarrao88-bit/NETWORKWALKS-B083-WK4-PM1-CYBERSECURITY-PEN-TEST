# NETWORKWALKS-B083-WK4-PM1-CYBERSECURITY-PEN-TEST
PENETRATION TESTING 
# Mediroza General Hospital — Penetration Testing Lab (Week 4)

Program: Cybersecurity at Networkwalks | Batch B083
Target: https://medirozahospital.com (lab/training environment)
Type: Black-box Pentest | Duration: 5 Days
Authorization: Written permission granted for this controlled training engagement.

> Educational use only. Never run these techniques against a system without
> explicit written permission from its owner.

## 1. Reconnaissance
- whois-lookup.png       → WHOIS registration data
- nslookup.png           → DNS resolution
- nmap-portscan.png      → Port scan / service & OS fingerprinting
- wafw00f-scan.png       → WAF detection

## 2. Initial Access (M1)
- robots-txt-and-login-endpoint.png
  → robots.txt disclosed /patient/, /staff/, /old/ as restricted paths;
    /patient/login.php confirmed as a live PHP 8.2.34 login portal.

## 3. Data Extraction (M2)
- pdf-password-crack.png
  → Dictionary attack on PDF (R3/128-bit), password recovered from a
    100-entry wordlist — weak/default password reused on the file.
- retrieved-lab-report-sample.png
  → Decrypted patient pathology lab report (confidential PHI).

## 4. Further Data Exposure (M3) — pending
Goal: find staff salaries and shareholder details via a further exposure
pointed to by file metadata on the retrieved PDFs. No evidence captured yet
— add exiftool/pdfinfo output and findings here.

## 5. Report (M4)
- WK4_Mediroza_v1.pdf → original project brief

### Draft findings table
| # | Finding | Evidence | Risk | Status |
|---|---|---|---|---|
| 1 | Sensitive dirs disclosed via robots.txt | robots-txt-and-login-endpoint.png | Low-Med | Done |
| 2 | Patient login portal exposed, PHP version disclosed | robots-txt-and-login-endpoint.png | Medium | Done |
| 3 | Weak/default password on confidential PDF | pdf-password-crack.png | High | Done |
| 4 | PHI exposed via weak PDF protection | retrieved-lab-report-sample.png | High | Done |
| 5 | Salary/shareholder data exposure | TBD | TBD | Pending |

Source project brief: [`WK4_Mediroza_v1.pdf`](./WK4_Mediroza_v1.pdf)

## Required Report Structure

1. **Executive Summary** — concise overview of engagement, key findings, overall risk.
2. **Scope and Methodology** — target, tools used, approach, limitations.
3. **Findings and Proof of Exploitation** — each vulnerability with screenshots/evidence per milestone (link back to `01-04` folders).
4. **Risk Rating** — Critical / High / Medium / Low with justification per finding.
5. **Recommendations and Remediation** — actionable fixes for each issue.

## Draft Findings Table (fill in as milestones complete)

| # | Finding | Evidence | Risk | Status |
|---|---|---|---|---|
| 1 | Sensitive directories disclosed via `robots.txt` | `02-initial-access/robots-txt-and-login-endpoint.png` | Low–Medium | ✅ |
| 2 | Patient login portal exposed, PHP version disclosed | `02-initial-access/robots-txt-and-login-endpoint.png` | Medium | ✅ |
| 3 | Weak/default password on confidential PDF (dictionary-crackable) | `03-data-extraction/pdf-password-crack.png` | High | ✅ |
| 4 | PHI (patient lab results) exposed via weak PDF protection | `03-data-extraction/retrieved-lab-report-sample.png` | High | ✅ |
| 5 | Further data exposure (salaries/shareholder info) | TBD — see `04-attack-cracking/` | TBD | ⏳ |
