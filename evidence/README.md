# Empirical Evidence for `en-BD` Locale Conventions

This directory documents real-world usage across government institutions and commercial banks in Bangladesh, demonstrating both the established national standard and the formatting fragmentation caused by the absence of an official `en-BD` locale.

---

## 1. Official Government Standard (National Board of Revenue)

* **Source:** Government of the People's Republic of Bangladesh — National Board of Revenue (NBR), eReturn Income Tax Acknowledgement Certificate (`etaxnbr.gov.bd`)
* **Observed Conventions:**
  * **South Asian Digit Grouping (Lakh/Crore):** `7,20,667 Taka` (correctly placing separators at thousand and lakh positions)
  * **Date Format (`DD/MM/YYYY`):** `03/09/2026`
  * **Language & Orthography:** Official administrative English

---

## 2. Fragmentation Across Commercial Banks (Impact of Missing `en-BD`)

Because core banking engines, email notification templates, and operating systems lack a standard `en-BD` locale, major scheduled banks in Bangladesh fall back to conflicting foreign defaults:

| Institution | Currency / Amount Formatting | Date & Time Formatting | Underlying Locale Mismatch |
| :--- | :--- | :--- | :--- |
| **Mutual Trust Bank PLC (MTB)** | `BDT 484,846.50` | `17-NOV-2026 22:30` | Uses Western thousand-grouping (`484,846.50`) instead of Lakh/Crore (`4,84,846.50`) |
| **Eastern Bank PLC (EBL)** | `287545.14` (`BDT`) | `11/24/2026 10:22:04 AM` | Defaults to US `MM/DD/YYYY` date order (`11/24/2026`) with 12-hour `AM/PM` and ungrouped digits |
| **Prime Bank PLC** | `290342.47` (`BDT`) | `21/11/2026 20:53:43` | Uses `DD/MM/YYYY` date order with 24-hour time and ungrouped digits |

---

## Conclusion for Unicode CLDR

Official Bangladeshi government systems (such as NBR) strictly follow **Lakh/Crore digit grouping (`#,##,##0.00`)** and **`DD/MM/YYYY`** dates in English-language documents, whereas private-sector software defaults inconsistently to `en-US` or `en-GB` patterns due to the absence of `en-BD` in Unicode CLDR and OS locale libraries.
