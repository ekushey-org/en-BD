# `en-BD` - English (Bangladesh) Locale Proposal

A formal **Unicode Common Locale Data Repository (CLDR) proposal** and reference implementation for the **English (Bangladesh) [`en-BD`]** locale, designed for adoption across operating systems, financial platforms, and open-source ecosystems (`glibc`, ICU).

---

## Overview & Purpose of This Proposal

This repository documents the technical specification, linguistic rationale, and real-world usage evidence required to establish **`en-BD`** as a standard locale in **Unicode CLDR** and GNU/Linux distributions. 

While Bengali (`bn-BD`) is supported globally, Bangladesh currently lacks an official English regional locale (`en-BD`). Consequently, users, banks, and software vendors are forced to rely on mismatched foreign locales (`en-US`, `en-GB`, or `en-IN`). This proposal defines a clean, non-patched regional standard tailored to Bangladesh's institutional and everyday conventions.

---

## Locale Specification Summary

| Attribute | Standard for `en-BD` | Notes / Reference |
| :--- | :--- | :--- |
| **Language & Spelling** | British English (`en-GB` / `en-001`) | Follows Commonwealth English orthography (*colour*, *centre*, *metre*, *cheque*, *licence*) |
| **Currency Symbol** | `৳` | Bangladeshi Taka sign (`U+09F3`) |
| **Currency Code** | `BDT` | ISO 4217 currency code for Bangladeshi Taka |
| **Number & Currency Grouping** | `00,00,00,000.00` (`#,##,##0.00`) | South Asian numbering system (Lakh & Crore) |
| **Measurement System** | Metric (`Metre`, `Kilometre`, `Celsius`) | Standard SI/Metric units |
| **Time Format** | 12-hour clock (`AM` / `PM`) | Standard civil and commercial usage |
| **Date Format** | `DD/MM/YYYY` | Day-Month-Year ordering |
| **Weekend** | Friday & Saturday | Official government and banking weekend in Bangladesh |
| **Default Paper Size** | `A4` | ISO 216 standard used across offices and institutions |

---

## Why `en-BD` is Essential

A vast majority of computer, smartphone, banking, and enterprise software users in Bangladesh operate their digital devices in English. Without a dedicated **`en-BD`** locale, users encounter persistent friction in daily financial and administrative tasks.

### 1. Language vs. Practical Habit (`bn-BD` Alone is Not Enough)
While the Bengali locale (`bn-BD`) accurately provides the Taka sign (`৳`), Lakh/Crore comma grouping, and metric units, selecting it translates the entire user interface into Bengali:
- In Bangladesh, users are accustomed to reading bank and credit card statements, invoices, accounting ledgers, and software menus in English.
- Complex technical terminology in translated interfaces often creates usability barriers rather than solving them.
- Shifting an entire population's daily digital workflow into a translated UI overnight is impractical. Users need **an English interface paired with Bangladeshi regional conventions**—a requirement only `en-BD` can fulfil.

### 2. Real-World Friction with Existing Foreign Locales

- **Banking & Financial Grouping (`00,00,00,000.00` vs. `000,000,000.00`):**  
  Because `en-US` or `en-GB` is typically set as the default English locale, local banking apps, statements, and ERP systems frequently format currency in the Western million/billion style (`000,000,000.00`). In Bangladesh, financial figures are universally counted in **Lakh** and **Crore** (`00,00,00,000.00`). This mismatch makes reading financial statements error-prone for everyday citizens and accountants alike.
- **Currency Symbol Mismatch (`৳` vs. `₹`, `$`, `£`):**  
  To get Lakh/Crore comma grouping, many users switch to Indian English (`en-IN`), which incorrectly displays the Indian Rupee (`₹`) instead of the Bangladeshi Taka (`৳`). Conversely, `en-US` and `en-GB` default to `$` and `£`. No existing English locale pairs the `৳` (`BDT`) symbol with South Asian digit grouping.
- **Measurement Units (`Celsius` & `Kilometre` vs. `Fahrenheit` & `Mile`):**  
  Major operating systems built in the United States default to `en-US`, displaying weather temperatures in Fahrenheit and distances in Miles. Bangladesh strictly follows the metric system (Celsius, Metre, Kilometre), making imperial units unintuitive and unhelpful.
- **Date Format Ambiguity (`DD/MM/YYYY` vs. `MM/DD/YYYY`):**  
  Official documents, financial records, and everyday correspondence in Bangladesh follow the `DD/MM/YYYY` format. Defaulting to `en-US` (`MM/DD/YYYY`) regularly causes confusion over whether `04/05` refers to 4 May or 5 April on tickets, invoices, and forms.
- **Spelling & Dictionary Standards:**  
  Bangladesh's education system, legal framework, government administration, and press follow British English spelling conventions (*programme*, *standardised*, *cheque*, *organisation*). American spell-checkers (`en-US`) flag standard local usage as errors.
- **12-Hour Time (`AM/PM`) & Local Weekend:**  
  While `en-GB` provides British spelling and metric units, many systems default it to a 24-hour clock and a Saturday–Sunday weekend. In Bangladesh, the 12-hour `AM/PM` format is universal, and the official weekend is **Friday and Saturday**.
- **Default Paper Size (`A4` vs. `US Letter`):**  
  Offices, courts, and educational institutions across Bangladesh use **A4** paper exclusively. American locale defaults force print dialogues to **US Letter**, causing layout shifts and printer tray errors.

---

## Repository Structure

```text
en-bd/
├── README.md                              # English proposal & specification (en-GB)
├── README_BN.md                           # Bengali proposal & rationale
├── LICENSE
├── cldr/
│   └── common/
│       ├── main/
│       │   └── en_BD.xml                  # CLDR LDML locale definition
│       └── supplemental/
│           └── parentLocale-snippet.xml   # Parent locale inheritance (en-001)
├── glibc/
│   └── en_BD                              # Reference glibc locale source file
└── evidence/                              # Institutional & banking usage evidence
