# 🌐 TSPANN (The Subdomain Project for Assigned Names and Numbers)

> **Standardising, decentralising, and safeguarding registration data for the modern developer web.**

---

## 📌 What is TSPANN?

In the modern internet ecosystem, community-driven subdomain providers (like `is-a.dev`, `stusite.me`, and `eu.org`) give millions of developers access to the web. However, because these systems exist outside traditional ICANN governance, they lack standard tools for open data lookup. Traditional WHOIS and IANA/ICANN RDAP servers do not index subdomains.

**TSPANN** is an open-source, community-led project designed to mirror the structural architecture of IANA for alternative, developer-focused subdomain registries. 

By utilizing the standard **Registration Data Access Protocol (RDAP)**, TSPANN provides a federated, decentralized network mapping system. This allows developers to host their own static or dynamic data points, which can then be instantly discovered and queried by any compliant TSPANN client.

---

## 🛠️ Architecture & How It Works

TSPANN operates exactly like the global IANA bootstrap root, scaled down for subdomains:

1. **The Topology Central Directory (`bootstrap.json`):** This repository maintains the master root registry file. It contains the operational mapping between a community subdomain suffix (e.g., `is-a.dev`) and its authoritative RDAP server base URL.
2. **Authoritative Subdomain Registries:** Suffix managers host their own standardized RDAP endpoints (following **RFC 9083** data structures) via static setups (like Jekyll or GitHub Pages) or dynamic web microservices.
3. **The TSPANN Resolution Chain:** When a user queries a domain via a TSPANN client, the engine reads the central `bootstrap.json` map, identifies the correct host, and fetches the data directly from the authoritative source.

---

## 📂 Repository Layout

```text
├── .github/              # Automation workflows
├── domain/               # Authoritative local domain records (Example registry data)
│   └── deniskuizinas.is-a.dev.json
├── bootstrap.json        # The master TSPANN routing registry (Central directory)
├── index.html            # Web-based TSPANN lookup dashboard utility
└── README.md             # Project manifesto and integration documentation
```

---

## 🚀 How to Join the TSPANN Network

If you operate a community subdomain provider or want to register an authoritative lookup service for your developer domain, you can join the federated network via a **GitHub Pull Request**.

### 1. Host your RDAP Endpoints
Ensure you are serving valid JSON payloads according to standard protocol guidelines. For instance, your endpoint should map to `/domain/yourname.suffix.json` and contain the proper structural classes:

```json
{
  "rdapConformance": ["rdap_level_0"],
  "objectClassName": "domain",
  "handle": "YOUR-UNIQUE-HANDLE",
  "ldhName": "yourname.is-a.dev",
  "status": ["active"],
  "entities": [
    {
      "objectClassName": "entity",
      "handle": "YOUR-NAME-HANDLE",
      "roles": ["registrant"],
      "vcardArray": [
        "vcard",
        [["version", {}, "text", "4.0"], ["fn", {}, "text", "Your Display Name"]]
      ]
    }
  ]
}
```

### 2. Update the Bootstrap File
Submit a Pull Request adding your subdomain suffix and your base endpoint URL to the `bootstrap.json` block:

```json
{
  "domainSuffix": "(sd).(suffix).(tld)",
  "rdapBaseUrl": "./domain/(yourdomain).json"
}
```

---

## 🛡️ Privacy & Code of Conduct

Because TSPANN encourages deployment on public web infrastructures like GitHub Pages, privacy is built directly into our specification philosophy:
* **Obfuscation Encouraged:** Registrants are actively discouraged from publishing highly sensitive personal tracking data (such as home addresses or primary mobile phone numbers) in public JSON payloads. 
* **Role-Based Data:** We advise using generic contact proxies, corporate domains, or public social handles within the `vcardArray` metadata blocks.
* **Open Source Integrity:** Malicious data formatting, intentionally broken routing payloads, or domain squatting maps will be rejected during peer code review.
* **Privatize Data:** If you need to use a private email address or phone number for the subdomain whois, don't be afraid to contact me as I will be able to get you a private email or phone number for free or cheap that will reroute to your phone number or forward to your email privately, you can also read our privacy policy here: https://d08689390-byte.github.io/TSPANN/Privacy-Policy

---

## Become a Maintainer

If you would like to become a Maintainer, you have to follow the eligibility criteria:
* **Have a Subdomain** This is one of the most basic things here, you need a subdomain, you can get one either for free or for cheap, I recommend is-a.dev.
* **Your Subdomain works** Your Subdomain must have an actual page on it, it **Cannot** have an error page (e.g 404)
* **Help Out!** You must have some experience first either helping out with TSPANN Pull Requests or Other Things (Include Screenshots!) Things like commenting on PRs to Help me and The User wanting to get on the system or helping me code by sending me ideas! Be creative or inspiring is the Focus!
* **Applying** If you have met all of the criteria, Please don't hesitate to use the form on my personal website (https://d08689390-byte.github.io/Main) and get in touch!

## 📄 Compliance Reference Specifications

TSPANN builds strictly upon open internet standards formalized by the IETF:
* **RFC 9082:** Registration Data Access Protocol (RDAP) Query Format
* **RFC 9083:** JSON Responses for the Registration Data Access Protocol (RDAP)
* **RFC 9224:** Finding Authoritative Registration Data (RDAP) Services

---

*Maintained by the TSPANN Community. Open to all independent web developers.*
