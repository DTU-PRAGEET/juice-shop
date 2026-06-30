# SECURITY_EVALUATION_GUIDE.md

> **CONFIDENTIAL — EVALUATOR ONLY**
> Ground-truth answer key for multi-agent security remediation platform benchmarking.
> **Agents must NEVER have access to this file.**

**Repository:** OWASP Juice Shop | **Vulnerabilities:** 113 | **Generated:** 2026-06-30

---

## Table of Contents

1. [Password Hash Leak](#passwordhashleakchallenge)
2. [API-only XSS](#restfulxsschallenge)
3. [Access Log](#accesslogdisclosurechallenge)
4. [Admin Registration](#registeradminchallenge)
5. [Admin Section](#adminsectionchallenge)
6. [Arbitrary File Write](#filewritechallenge)
7. [Bjoern's Favorite Pet](#resetpasswordbjoernowaspchallenge)
8. [Blockchain Hype](#tokensalechallenge)
9. [NFT Takeover](#nftunlockchallenge)
10. [Mint the Honey Pot](#nftmintchallenge)
11. [Wallet Depletion](#web3walletchallenge)
12. [Web3 Sandbox](#web3sandboxchallenge)
13. [Blocked RCE DoS](#rcechallenge)
14. [CAPTCHA Bypass](#captchabypasschallenge)
15. [Change Bender's Password](#changepasswordbenderchallenge)
16. [Christmas Special](#christmasspecialchallenge)
17. [CSP Bypass](#usernamexsschallenge)
18. [Client-side XSS Protection](#persistedxssuserchallenge)
19. [Confidential Document](#directorylistingchallenge)
20. [DOM XSS](#localxsschallenge)
21. [Database Schema](#dbschemachallenge)
22. [Deprecated Interface](#deprecatedinterfacechallenge)
23. [Easter Egg](#easteregglevelonechallenge)
24. [Email Leak](#emailleakchallenge)
25. [Empty User Registration](#emptyuserregistration)
26. [Ephemeral Accountant](#ephemeralaccountantchallenge)
27. [Error Handling](#errorhandlingchallenge)
28. [Expired Coupon](#manipulateclockchallenge)
29. [Extra Language](#extralanguagechallenge)
30. [Five-Star Feedback](#feedbackchallenge)
31. [Forged Coupon](#forgedcouponchallenge)
32. [Forged Feedback](#forgedfeedbackchallenge)
33. [Forged Review](#forgedreviewchallenge)
34. [Forged Signed JWT](#jwtforgedchallenge)
35. [Forgotten Developer Backup](#forgottendevbackupchallenge)
36. [Forgotten Sales Backup](#forgottenbackupchallenge)
37. [Frontend Typosquatting](#typosquattingangularchallenge)
38. [GDPR Data Erasure](#ghostloginchallenge)
39. [GDPR Data Theft](#dataexportchallenge)
40. [HTTP-Header XSS](#httpheaderxsschallenge)
41. [Imaginary Challenge](#continuecodechallenge)
42. [Leaked Access Logs](#dlppasswordsprayingchallenge)
43. [Leaked Unsafe Product](#dlppastebindataleakchallenge)
44. [Legacy Typosquatting](#typosquattingnpmchallenge)
45. [Login Admin](#loginadminchallenge)
46. [Login Amy](#loginamychallenge)
47. [Login Bender](#loginbenderchallenge)
48. [Login Bjoern](#oauthuserpasswordchallenge)
49. [Login Jim](#loginjimchallenge)
50. [Login MC SafeSearch](#loginrapperchallenge)
51. [Login Support Team](#loginsupportchallenge)
52. [Manipulate Basket](#basketmanipulatechallenge)
53. [Misplaced Signature File](#misplacedsignaturefilechallenge)
54. [Multiple Likes](#timingattackchallenge)
55. [Nested Easter Egg](#eastereggleveltwochallenge)
56. [NoSQL DoS](#nosqlcommandchallenge)
57. [NoSQL Exfiltration](#nosqlorderschallenge)
58. [NoSQL Manipulation](#nosqlreviewschallenge)
59. [Outdated Allowlist](#redirectcryptocurrencychallenge)
60. [Password Strength](#weakpasswordchallenge)
61. [Payback Time](#negativeorderchallenge)
62. [Premium Paywall](#premiumpaywallchallenge)
63. [Privacy Policy](#privacypolicychallenge)
64. [Privacy Policy Inspection](#privacypolicyproofchallenge)
65. [Product Tampering](#changeproductchallenge)
66. [Reflected XSS](#reflectedxsschallenge)
67. [Repetitive Registration](#passwordrepeatchallenge)
68. [Reset Bender's Password](#resetpasswordbenderchallenge)
69. [Reset Bjoern's Password](#resetpasswordbjoernchallenge)
70. [Reset Jim's Password](#resetpasswordjimchallenge)
71. [Reset Morty's Password](#resetpasswordmortychallenge)
72. [Retrieve Blueprint](#retrieveblueprintchallenge)
73. [SSRF](#ssrfchallenge)
74. [SSTi](#sstichallenge)
75. [Score Board](#scoreboardchallenge)
76. [Security Policy](#securitypolicychallenge)
77. [Server-side XSS Protection](#persistedxssfeedbackchallenge)
78. [Steganography](#hiddenimagechallenge)
79. [Successful RCE DoS](#rceoccupychallenge)
80. [Supply Chain Attack](#supplychainattackchallenge)
81. [Two Factor Authentication](#twofactorauthunsafesecretstoragechallenge)
82. [Unsigned JWT](#jwtunsignedchallenge)
83. [Upload Size](#uploadsizechallenge)
84. [Upload Type](#uploadtypechallenge)
85. [User Credentials](#unionsqlinjectionchallenge)
86. [Video XSS](#videoxsschallenge)
87. [View Basket](#basketaccesschallenge)
88. [Vulnerable Library](#knownvulnerablecomponentchallenge)
89. [Weird Crypto](#weirdcryptochallenge)
90. [Allowlist Bypass](#redirectchallenge)
91. [XXE Data Access](#xxefiledisclosurechallenge)
92. [XXE DoS](#xxedoschallenge)
93. [Memory Bomb](#yamlbombchallenge)
94. [Zero Stars](#zerostarschallenge)
95. [Missing Encoding](#missingencodingchallenge)
96. [Cross-Site Imaging](#svginjectionchallenge)
97. [Exposed Metrics](#exposedmetricschallenge)
98. [Deluxe Fraud](#freedeluxechallenge)
99. [CSRF](#csrfchallenge)
100. [Bonus Payload](#xssbonuschallenge)
101. [Reset Uvogin's Password](#resetpassworduvoginchallenge)
102. [Meta Geo Stalking](#geostalkingmetachallenge)
103. [Visual Geo Stalking](#geostalkingvisualchallenge)
104. [Poison Null Byte](#nullbytechallenge)
105. [Local File Read](#lfrchallenge)
106. [Mass Dispel](#closenotificationschallenge)
107. [Security Advisory](#csafchallenge)
108. [Exposed Credentials](#exposedcredentialschallenge)
109. [Leaked API Key](#leakedapikeychallenge)
110. [Chatbot Prompt Injection](#chatbotpromptinjectionchallenge)
111. [Greedy Chatbot Manipulation](#chatbotgreedyinjectionchallenge)
112. [AI Debugging](#aidebuggingchallenge)
113. [System Prompt Extraction](#systempromptextractionchallenge)

---

## Vulnerability Catalog

### Password Hash Leak
<a id="passwordhashleakchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `passwordHashLeakChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | API3:2019 Excessive Data Exposure |
| **CWE** | CWE-200 |
| **Difficulty** | Easy |

**Description:**
Obtain the password (hash) of the currently logged-in user directly from a REST API endpoint.

**Root Cause:**
GET /rest/user/whoami returns password hash in JSON response

**Affected Files:**
- `routes/currentUser.ts`

**Entry Points:**
- GET /rest/user/whoami

**Impact:**
Password hash disclosure enables offline cracking

**Remediation Strategy:**
Exclude password/hash from API response DTOs

**Files to Modify:**
- `routes/currentUser.ts`

**Validation Steps:**
whoami response must not contain password field

**Cross-Impact Risk:**
Minimal

---
### API-only XSS
<a id="restfulxsschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `restfulXssChallenge` |
| **Category** | XSS |
| **OWASP** | A03:2021 Injection |
| **CWE** | CWE-79 |
| **Difficulty** | Medium |

**Description:**
Perform a <i>persisted</i> XSS attack with <code>&lt;iframe src="javascript:alert(`xss`)"&gt;</code> without using the frontend application at all.

**Root Cause:**
Product REST API stores unsanitized HTML in description

**Affected Files:**
- `routes/product.ts`
- `models/product.ts`

**Entry Points:**
- PUT /api/Products/:id

**Impact:**
Persisted XSS via direct API call

**Remediation Strategy:**
Server-side HTML sanitization on product fields

**Files to Modify:**
- `routes/product.ts`

**Validation Steps:**
iframe XSS payload rejected or encoded in DB

**Cross-Impact Risk:**
Rich text products may need safe subset

---
### Access Log
<a id="accesslogdisclosurechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `accessLogDisclosureChallenge` |
| **Category** | Observability Failures |
| **OWASP** | A05:2021 Security Misconfiguration |
| **CWE** | CWE-538 |
| **Difficulty** | Medium |

**Description:**
Gain access to any access log file of the server.

**Root Cause:**
Access logs exposed via /support/logs without auth

**Affected Files:**
- `server.ts`
- `routes/verify.ts`

**Entry Points:**
- GET /support/logs/*

**Impact:**
Log file disclosure

**Remediation Strategy:**
Remove or protect log endpoints

**Files to Modify:**
- `server.ts`

**Validation Steps:**
Unauthenticated log access returns 403/404

**Cross-Impact Risk:**
Ops may need internal log access

---
### Admin Registration
<a id="registeradminchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `registerAdminChallenge` |
| **Category** | Improper Input Validation |
| **OWASP** | A04:2021 Insecure Design |
| **CWE** | CWE-915 |
| **Difficulty** | Easy |

**Description:**
Register as a user with administrator privileges.

**Root Cause:**
Mass assignment allows role=admin on registration

**Affected Files:**
- `routes/user.ts`

**Entry Points:**
- POST /api/Users

**Impact:**
Privilege escalation at signup

**Remediation Strategy:**
Whitelist registration fields; set role server-side

**Files to Modify:**
- `routes/user.ts`

**Validation Steps:**
role param ignored on register

**Cross-Impact Risk:**
None

---
### Admin Section
<a id="adminsectionchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `adminSectionChallenge` |
| **Category** | Broken Access Control |
| **OWASP** | A01:2021 Broken Access Control |
| **CWE** | CWE-284 |
| **Difficulty** | Easy |

**Description:**
Access the administration section of the store.

**Root Cause:**
Admin UI route lacks AdminGuard enforcement

**Affected Files:**
- `frontend/src/app/app.routing.ts`
- `frontend/src/app/app.guard.ts`
- `routes/authenticatedUsers.ts`

**Entry Points:**
- /#/administration
- Admin API endpoints

**Impact:**
Non-admins access admin panel

**Remediation Strategy:**
Apply AdminGuard; verify role on server for all admin APIs

**Files to Modify:**
- `frontend/src/app/app.routing.ts`
- `frontend/src/app/app.guard.ts`

**Validation Steps:**
Customer JWT cannot load admin UI/APIs

**Cross-Impact Risk:**
Ensure all admin paths guarded

---
### Arbitrary File Write
<a id="filewritechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `fileWriteChallenge` |
| **Category** | Vulnerable Components |
| **OWASP** | A06:2021 Vulnerable Components |
| **CWE** | CWE-73 |
| **Difficulty** | Hard |

**Description:**
Overwrite the <a href="/ftp/legal.md">Legal Information</a> file.

**Root Cause:**
Vulnerable file upload allows arbitrary overwrite

**Affected Files:**
- `routes/fileUpload.ts`

**Entry Points:**
- POST /file-upload

**Impact:**
Overwrite legal.md or other files

**Remediation Strategy:**
Fix path traversal in upload handler; upgrade library

**Files to Modify:**
- `routes/fileUpload.ts`

**Validation Steps:**
Cannot overwrite ftp/legal.md

**Cross-Impact Risk:**
Upload flow may change

**Dependencies:** `videoXssChallenge`

---
### Bjoern's Favorite Pet
<a id="resetpasswordbjoernowaspchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `resetPasswordBjoernOwaspChallenge` |
| **Category** | Broken Authentication |
| **OWASP** | A07:2021 Identification and Authentication Failures |
| **Difficulty** | Medium |

**Description:**
Reset the password of Bjoern's OWASP account via the <a href="/#/forgot-password">Forgot Password</a> mechanism with <i>the original answer</i> to his security question.

**Root Cause:**
Intentional broken authentication flaw in implementation (key: `resetPasswordBjoernOwaspChallenge`)

**Affected Files:**
- `routes/resetPassword.ts`

**Entry Points:**
- API/UI refs in: routes/resetPassword.ts

**Impact:**
Enables bjoern's favorite pet attack scenario

**Remediation Strategy:**
Secure broken authentication per OWASP guidelines

**Files to Modify:**
- `routes/resetPassword.ts`

**Validation Steps:**
Confirm exploit for Bjoern's Favorite Pet no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Blockchain Hype
<a id="tokensalechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `tokenSaleChallenge` |
| **Category** | Security through Obscurity |
| **OWASP** | A04:2021 Insecure Design |
| **Difficulty** | Hard |

**Description:**
Learn about the Token Sale before its official announcement.

**Root Cause:**
Intentional security through obscurity flaw in implementation (key: `tokenSaleChallenge`)

**Affected Files:**
- `frontend/src/app/app.routing.ts`
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: frontend/src/app/app.routing.ts
- API/UI refs in: routes/verify.ts

**Impact:**
Enables blockchain hype attack scenario

**Remediation Strategy:**
Secure security through obscurity per OWASP guidelines

**Files to Modify:**
- `frontend/src/app/app.routing.ts`
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Blockchain Hype no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### NFT Takeover
<a id="nftunlockchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `nftUnlockChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | A02:2021 Crypto Failures |
| **CWE** | CWE-798 |
| **Difficulty** | Easy |

**Description:**
Take over the wallet containing our official Soul Bound Token (NFT).

**Root Cause:**
BIP-39 seed phrase hardcoded in checkKeys.ts

**Affected Files:**
- `routes/checkKeys.ts`

**Entry Points:**
- routes/checkKeys.ts

**Impact:**
Wallet/NFT takeover

**Remediation Strategy:**
Remove hardcoded secrets; use HSM/vault

**Files to Modify:**
- `routes/checkKeys.ts`

**Validation Steps:**
No mnemonic in source

**Cross-Impact Risk:**
NFT unlock flow

---
### Mint the Honey Pot
<a id="nftmintchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `nftMintChallenge` |
| **Category** | Improper Input Validation |
| **OWASP** | A04:2021 Insecure Design |
| **Difficulty** | Medium |

**Description:**
Mint the Honey Pot NFT by gathering BEEs from the bee haven.

**Root Cause:**
Intentional improper input validation flaw in implementation (key: `nftMintChallenge`)

**Affected Files:**
- `data/static/web3-snippets/HoneyPotNFT.sol`
- `frontend/src/app/Services/keys.service.spec.ts`
- `frontend/src/app/Services/keys.service.ts`
- `routes/nftMint.ts`

**Entry Points:**
- API/UI refs in: data/static/web3-snippets/HoneyPotNFT.sol
- API/UI refs in: frontend/src/app/Services/keys.service.spec.ts
- API/UI refs in: frontend/src/app/Services/keys.service.ts

**Impact:**
Enables mint the honey pot attack scenario

**Remediation Strategy:**
Secure improper input validation per OWASP guidelines

**Files to Modify:**
- `frontend/src/app/Services/keys.service.spec.ts`
- `frontend/src/app/Services/keys.service.ts`
- `routes/nftMint.ts`

**Validation Steps:**
Confirm exploit for Mint the Honey Pot no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Wallet Depletion
<a id="web3walletchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `web3WalletChallenge` |
| **Category** | Miscellaneous |
| **OWASP** | Various |
| **Difficulty** | Hard |

**Description:**
Withdraw more ETH from the new wallet than you deposited.

**Root Cause:**
Intentional miscellaneous flaw in implementation (key: `web3WalletChallenge`)

**Affected Files:**
- `data/static/web3-snippets/ETHWalletBank.sol`
- `routes/web3Wallet.ts`

**Entry Points:**
- API/UI refs in: data/static/web3-snippets/ETHWalletBank.sol
- API/UI refs in: routes/web3Wallet.ts

**Impact:**
Enables wallet depletion attack scenario

**Remediation Strategy:**
Secure miscellaneous per OWASP guidelines

**Files to Modify:**
- `routes/web3Wallet.ts`

**Validation Steps:**
Confirm exploit for Wallet Depletion no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Web3 Sandbox
<a id="web3sandboxchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `web3SandboxChallenge` |
| **Category** | Broken Access Control |
| **OWASP** | A01:2021 Broken Access Control |
| **CWE** | CWE-284 |
| **Difficulty** | Easy |

**Description:**
Find an accidentally deployed code sandbox for writing smart contracts on the fly.

**Root Cause:**
Hidden web3 sandbox route without guard

**Affected Files:**
- `frontend/src/app/app.routing.ts`

**Entry Points:**
- /#/web3-sandbox

**Impact:**
Unauthorized smart contract IDE access

**Remediation Strategy:**
Add authentication/authorization

**Files to Modify:**
- `frontend/src/app/app.routing.ts`

**Validation Steps:**
Route protected

**Cross-Impact Risk:**
Web3 feature

---
### Blocked RCE DoS
<a id="rcechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `rceChallenge` |
| **Category** | Insecure Deserialization |
| **OWASP** | A08:2021 Software and Data Integrity Failures |
| **Difficulty** | Hard |

**Description:**
Perform a Remote Code Execution that would keep a less hardened application busy <em>forever</em>.

**Root Cause:**
Intentional insecure deserialization flaw in implementation (key: `rceChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `routes/b2bOrder.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/b2bOrder.ts

**Impact:**
Enables blocked rce dos attack scenario

**Remediation Strategy:**
Secure insecure deserialization per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `routes/b2bOrder.ts`

**Validation Steps:**
Confirm exploit for Blocked RCE DoS no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### CAPTCHA Bypass
<a id="captchabypasschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `captchaBypassChallenge` |
| **Category** | Broken Anti Automation |
| **OWASP** | A07:2021 Auth Failures |
| **Difficulty** | Medium |

**Description:**
Submit 10 or more customer feedbacks within 20 seconds.

**Root Cause:**
Intentional broken anti automation flaw in implementation (key: `captchaBypassChallenge`)

**Affected Files:**
- `routes/verify.ts`
- `server.ts`

**Entry Points:**
- API/UI refs in: routes/verify.ts
- API/UI refs in: server.ts

**Impact:**
Enables captcha bypass attack scenario

**Remediation Strategy:**
Secure broken anti automation per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`
- `server.ts`

**Validation Steps:**
Confirm exploit for CAPTCHA Bypass no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Change Bender's Password
<a id="changepasswordbenderchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `changePasswordBenderChallenge` |
| **Category** | Broken Authentication |
| **OWASP** | A07:2021 Identification and Authentication Failures |
| **Difficulty** | Hard |

**Description:**
Change Bender's password into <i>slurmCl4ssic</i> without using SQL Injection or Forgot Password.

**Root Cause:**
Intentional broken authentication flaw in implementation (key: `changePasswordBenderChallenge`)

**Affected Files:**
- `routes/changePassword.ts`

**Entry Points:**
- API/UI refs in: routes/changePassword.ts

**Impact:**
Enables change bender's password attack scenario

**Remediation Strategy:**
Secure broken authentication per OWASP guidelines

**Files to Modify:**
- `routes/changePassword.ts`

**Validation Steps:**
Confirm exploit for Change Bender's Password no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Christmas Special
<a id="christmasspecialchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `christmasSpecialChallenge` |
| **Category** | Injection |
| **OWASP** | A03:2021 Injection |
| **Difficulty** | Medium |

**Description:**
Order the Christmas special offer of 2014.

**Root Cause:**
Intentional injection flaw in implementation (key: `christmasSpecialChallenge`)

**Affected Files:**
- `routes/order.ts`

**Entry Points:**
- API/UI refs in: routes/order.ts

**Impact:**
Enables christmas special attack scenario

**Remediation Strategy:**
Secure injection per OWASP guidelines

**Files to Modify:**
- `routes/order.ts`

**Validation Steps:**
Confirm exploit for Christmas Special no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### CSP Bypass
<a id="usernamexsschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `usernameXssChallenge` |
| **Category** | XSS |
| **OWASP** | A03:2021 Injection (XSS) |
| **Difficulty** | Medium |

**Description:**
Bypass the Content Security Policy and perform an XSS attack with <code>&lt;script&gt;alert(`xss`)&lt;/script&gt;</code> on a legacy page within the application.

**Root Cause:**
Intentional xss flaw in implementation (key: `usernameXssChallenge`)

**Affected Files:**
- `routes/userProfile.ts`

**Entry Points:**
- API/UI refs in: routes/userProfile.ts

**Impact:**
Enables csp bypass attack scenario

**Remediation Strategy:**
Secure xss per OWASP guidelines

**Files to Modify:**
- `routes/userProfile.ts`

**Validation Steps:**
Confirm exploit for CSP Bypass no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Client-side XSS Protection
<a id="persistedxssuserchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `persistedXssUserChallenge` |
| **Category** | XSS |
| **OWASP** | A03:2021 Injection (XSS) |
| **Difficulty** | Medium |

**Description:**
Perform a <i>persisted</i> XSS attack with <code>&lt;iframe src="javascript:alert(`xss`)"&gt;</code> bypassing a <i>client-side</i> security mechanism.

**Root Cause:**
Intentional xss flaw in implementation (key: `persistedXssUserChallenge`)

**Affected Files:**
- `models/user.ts`

**Entry Points:**
- API/UI refs in: models/user.ts

**Impact:**
Enables client-side xss protection attack scenario

**Remediation Strategy:**
Secure xss per OWASP guidelines

**Files to Modify:**

**Validation Steps:**
Confirm exploit for Client-side XSS Protection no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Confidential Document
<a id="directorylistingchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `directoryListingChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | A01:2021 Broken Access Control |
| **CWE** | CWE-548 |
| **Difficulty** | Easy |

**Description:**
Access a confidential document.

**Root Cause:**
FTP directory listing exposes confidential files

**Affected Files:**
- `routes/fileServer.ts`
- `server.ts`

**Entry Points:**
- GET /ftp/
- /#/public/images/padding

**Impact:**
Confidential document access

**Remediation Strategy:**
Disable directory listing; access control on files

**Files to Modify:**
- `routes/fileServer.ts`

**Validation Steps:**
acquisitions.md not listable

**Cross-Impact Risk:**
FTP UX

---
### DOM XSS
<a id="localxsschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `localXssChallenge` |
| **Category** | XSS |
| **OWASP** | A03:2021 Injection |
| **CWE** | CWE-79 |
| **Difficulty** | Easy |

**Description:**
Perform a <i>DOM</i> XSS attack with <code>&lt;iframe src="javascript:alert(`xss`)"&gt;</code>.

**Root Cause:**
Search term rendered via innerHTML (DOM XSS)

**Affected Files:**
- `frontend/src/app/search-result/search-result.component.ts`

**Entry Points:**
- /#/search?q=

**Impact:**
DOM XSS in search results

**Remediation Strategy:**
Use text binding or DomSanitizer

**Files to Modify:**
- `frontend/src/app/search-result/search-result.component.ts`

**Validation Steps:**
iframe payload does not execute

**Cross-Impact Risk:**
None

**Dependencies:** `xssBonusChallenge`

---
### Database Schema
<a id="dbschemachallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `dbSchemaChallenge` |
| **Category** | Injection |
| **OWASP** | A03:2021 Injection |
| **CWE** | CWE-89 |
| **Difficulty** | Medium |

**Description:**
Exfiltrate the entire DB schema definition via SQL Injection.

**Root Cause:**
SQLi in search allows sqlite_master access

**Affected Files:**
- `routes/search.ts`

**Entry Points:**
- GET /rest/products/search?q=

**Impact:**
Full DB schema disclosure

**Remediation Strategy:**
Parameterized queries

**Files to Modify:**
- `routes/search.ts`

**Validation Steps:**
Schema not in search results

**Cross-Impact Risk:**
None

---
### Deprecated Interface
<a id="deprecatedinterfacechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `deprecatedInterfaceChallenge` |
| **Category** | Security Misconfiguration |
| **OWASP** | A05:2021 Security Misconfiguration |
| **Difficulty** | Easy |

**Description:**
Use a deprecated B2B interface that was not properly shut down.

**Root Cause:**
Intentional security misconfiguration flaw in implementation (key: `deprecatedInterfaceChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `routes/fileUpload.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/fileUpload.ts

**Impact:**
Enables deprecated interface attack scenario

**Remediation Strategy:**
Secure security misconfiguration per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `routes/fileUpload.ts`

**Validation Steps:**
Confirm exploit for Deprecated Interface no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

**Dependencies:** `uploadTypeChallenge`, `xxeFileDisclosureChallenge`

---
### Easter Egg
<a id="easteregglevelonechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `easterEggLevelOneChallenge` |
| **Category** | Broken Access Control |
| **OWASP** | A01:2021 Broken Access Control |
| **Difficulty** | Medium |

**Description:**
Find the hidden <a href="https://en.wikipedia.org/wiki/Easter_egg_(media)" target="_blank">easter egg</a>.

**Root Cause:**
Intentional broken access control flaw in implementation (key: `easterEggLevelOneChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `routes/fileServer.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/fileServer.ts

**Impact:**
Enables easter egg attack scenario

**Remediation Strategy:**
Secure broken access control per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `routes/fileServer.ts`

**Validation Steps:**
Confirm exploit for Easter Egg no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Email Leak
<a id="emailleakchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `emailLeakChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Hard |

**Description:**
Perform an unwanted information disclosure by accessing data cross-domain.

**Root Cause:**
Intentional sensitive data exposure flaw in implementation (key: `emailLeakChallenge`)

**Affected Files:**
- `routes/currentUser.ts`

**Entry Points:**
- API/UI refs in: routes/currentUser.ts

**Impact:**
Enables email leak attack scenario

**Remediation Strategy:**
Secure sensitive data exposure per OWASP guidelines

**Files to Modify:**
- `routes/currentUser.ts`

**Validation Steps:**
Confirm exploit for Email Leak no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Empty User Registration
<a id="emptyuserregistration"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `emptyUserRegistration` |
| **Category** | Improper Input Validation |
| **OWASP** | A04:2021 Insecure Design |
| **Difficulty** | Easy |

**Description:**
Register a user with an empty email and password.

**Root Cause:**
Intentional improper input validation flaw in implementation (key: `emptyUserRegistration`)

**Affected Files:**
- `routes/verify.ts`
- `server.ts`

**Entry Points:**
- API/UI refs in: routes/verify.ts
- API/UI refs in: server.ts

**Impact:**
Enables empty user registration attack scenario

**Remediation Strategy:**
Secure improper input validation per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`
- `server.ts`

**Validation Steps:**
Confirm exploit for Empty User Registration no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Ephemeral Accountant
<a id="ephemeralaccountantchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `ephemeralAccountantChallenge` |
| **Category** | Injection |
| **OWASP** | A03:2021 Injection |
| **Difficulty** | Medium |

**Description:**
Log in with the (non-existing) accountant <i>acc0unt4nt@juice-sh.op</i> without ever registering that user.

**Root Cause:**
Intentional injection flaw in implementation (key: `ephemeralAccountantChallenge`)

**Affected Files:**
- `routes/login.ts`

**Entry Points:**
- API/UI refs in: routes/login.ts

**Impact:**
Enables ephemeral accountant attack scenario

**Remediation Strategy:**
Secure injection per OWASP guidelines

**Files to Modify:**
- `routes/login.ts`

**Validation Steps:**
Confirm exploit for Ephemeral Accountant no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Error Handling
<a id="errorhandlingchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `errorHandlingChallenge` |
| **Category** | Security Misconfiguration |
| **OWASP** | A05:2021 Security Misconfiguration |
| **Difficulty** | Easy |

**Description:**
Provoke an error that is neither very gracefully nor consistently handled.

**Root Cause:**
Intentional security misconfiguration flaw in implementation (key: `errorHandlingChallenge`)

**Affected Files:**
- `frontend/src/app/challenge-solved-notification/challenge-solved-notification.component.spec.ts`
- `lib/antiCheat.ts`
- `routes/verify.ts`
- `server.ts`

**Entry Points:**
- API/UI refs in: frontend/src/app/challenge-solved-notification/challenge-solved-notification.component.spec.ts
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/verify.ts

**Impact:**
Enables error handling attack scenario

**Remediation Strategy:**
Secure security misconfiguration per OWASP guidelines

**Files to Modify:**
- `frontend/src/app/challenge-solved-notification/challenge-solved-notification.component.spec.ts`
- `lib/antiCheat.ts`
- `routes/verify.ts`
- `server.ts`

**Validation Steps:**
Confirm exploit for Error Handling no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Expired Coupon
<a id="manipulateclockchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `manipulateClockChallenge` |
| **Category** | Improper Input Validation |
| **OWASP** | A04:2021 Insecure Design |
| **Difficulty** | Medium |

**Description:**
Successfully redeem an expired campaign coupon code.

**Root Cause:**
Intentional improper input validation flaw in implementation (key: `manipulateClockChallenge`)

**Affected Files:**
- `routes/order.ts`

**Entry Points:**
- API/UI refs in: routes/order.ts

**Impact:**
Enables expired coupon attack scenario

**Remediation Strategy:**
Secure improper input validation per OWASP guidelines

**Files to Modify:**
- `routes/order.ts`

**Validation Steps:**
Confirm exploit for Expired Coupon no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Extra Language
<a id="extralanguagechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `extraLanguageChallenge` |
| **Category** | Broken Anti Automation |
| **OWASP** | A07:2021 Auth Failures |
| **Difficulty** | Hard |

**Description:**
Retrieve the language file that never made it into production.

**Root Cause:**
Intentional broken anti automation flaw in implementation (key: `extraLanguageChallenge`)

**Affected Files:**
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: routes/verify.ts

**Impact:**
Enables extra language attack scenario

**Remediation Strategy:**
Secure broken anti automation per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Extra Language no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Five-Star Feedback
<a id="feedbackchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `feedbackChallenge` |
| **Category** | Broken Access Control |
| **OWASP** | A01:2021 Broken Access Control |
| **Difficulty** | Easy |

**Description:**
Get rid of all 5-star customer feedback.

**Root Cause:**
Intentional broken access control flaw in implementation (key: `feedbackChallenge`)

**Affected Files:**
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: routes/verify.ts

**Impact:**
Enables five-star feedback attack scenario

**Remediation Strategy:**
Secure broken access control per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Five-Star Feedback no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Forged Coupon
<a id="forgedcouponchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `forgedCouponChallenge` |
| **Category** | Cryptographic Issues |
| **OWASP** | A02:2021 Crypto Failures |
| **CWE** | CWE-327 |
| **Difficulty** | Hard |

**Description:**
Forge a coupon code that gives you a discount of at least 80%.

**Root Cause:**
Weak coupon HMAC/generation in insecurity.ts

**Affected Files:**
- `lib/insecurity.ts`
- `routes/coupon.ts`

**Entry Points:**
- POST /rest/basket/:id/coupon

**Impact:**
Forged 80%+ discount coupons

**Remediation Strategy:**
Strong HMAC-SHA256 with secret; server-side validation

**Files to Modify:**
- `lib/insecurity.ts`

**Validation Steps:**
Invalid coupons rejected

**Cross-Impact Risk:**
Coupon format may change

---
### Forged Feedback
<a id="forgedfeedbackchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `forgedFeedbackChallenge` |
| **Category** | Broken Access Control |
| **OWASP** | A01:2021 Broken Access Control |
| **CWE** | CWE-639 |
| **Difficulty** | Medium |

**Description:**
Post some feedback in another user's name.

**Root Cause:**
Feedback API accepts UserId from client without authorization check

**Affected Files:**
- `routes/feedback.ts`

**Entry Points:**
- POST /api/Feedbacks

**Impact:**
Post feedback as another user

**Remediation Strategy:**
Bind UserId to authenticated session server-side

**Files to Modify:**
- `routes/feedback.ts`

**Validation Steps:**
Cannot set arbitrary UserId

**Cross-Impact Risk:**
None

---
### Forged Review
<a id="forgedreviewchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `forgedReviewChallenge` |
| **Category** | Broken Access Control |
| **OWASP** | A01:2021 Broken Access Control |
| **CWE** | CWE-639 |
| **Difficulty** | Medium |

**Description:**
Post a product review as another user or edit any user's existing review.

**Root Cause:**
Review API allows authorId manipulation

**Affected Files:**
- `routes/productReviews.ts`

**Entry Points:**
- POST /rest/products/:id/reviews

**Impact:**
Forge product reviews

**Remediation Strategy:**
Server-side author binding

**Files to Modify:**
- `routes/productReviews.ts`

**Validation Steps:**
authorId from JWT only

**Cross-Impact Risk:**
None

---
### Forged Signed JWT
<a id="jwtforgedchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `jwtForgedChallenge` |
| **Category** | Vulnerable Components |
| **OWASP** | A02:2021 Crypto Failures |
| **CWE** | CWE-347 |
| **Difficulty** | Hard |

**Description:**
Forge an almost properly RSA-signed JWT token that impersonates the (non-existing) user <i>rsa_lord@juice-sh.op</i>.

**Root Cause:**
JWT algorithm confusion (public key as HMAC secret)

**Affected Files:**
- `lib/insecurity.ts`

**Entry Points:**
- Authorization header

**Impact:**
Forge valid JWT for arbitrary user

**Remediation Strategy:**
Pin algorithm; use updated jsonwebtoken

**Files to Modify:**
- `lib/insecurity.ts`

**Validation Steps:**
Algorithm confusion fails

**Cross-Impact Risk:**
Auth system

---
### Forgotten Developer Backup
<a id="forgottendevbackupchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `forgottenDevBackupChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Medium |

**Description:**
Access a developer's forgotten backup file.

**Root Cause:**
Intentional sensitive data exposure flaw in implementation (key: `forgottenDevBackupChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `routes/fileServer.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/fileServer.ts

**Impact:**
Enables forgotten developer backup attack scenario

**Remediation Strategy:**
Secure sensitive data exposure per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `routes/fileServer.ts`

**Validation Steps:**
Confirm exploit for Forgotten Developer Backup no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Forgotten Sales Backup
<a id="forgottenbackupchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `forgottenBackupChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Medium |

**Description:**
Access a salesman's forgotten backup file.

**Root Cause:**
Intentional sensitive data exposure flaw in implementation (key: `forgottenBackupChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `routes/fileServer.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/fileServer.ts

**Impact:**
Enables forgotten sales backup attack scenario

**Remediation Strategy:**
Secure sensitive data exposure per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `routes/fileServer.ts`

**Validation Steps:**
Confirm exploit for Forgotten Sales Backup no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Frontend Typosquatting
<a id="typosquattingangularchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `typosquattingAngularChallenge` |
| **Category** | Vulnerable Components |
| **OWASP** | A06:2021 Vulnerable Components |
| **Difficulty** | Hard |

**Description:**
<a href="/#/contact">Inform the shop</a> about a <i>typosquatting</i> imposter that dug itself deep into the frontend. (Mention the exact name of the culprit)

**Root Cause:**
Intentional vulnerable components flaw in implementation (key: `typosquattingAngularChallenge`)

**Affected Files:**
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: routes/verify.ts

**Impact:**
Enables frontend typosquatting attack scenario

**Remediation Strategy:**
Secure vulnerable components per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Frontend Typosquatting no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### GDPR Data Erasure
<a id="ghostloginchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `ghostLoginChallenge` |
| **Category** | Broken Authentication |
| **OWASP** | A07:2021 Identification and Authentication Failures |
| **Difficulty** | Medium |

**Description:**
Log in with Chris' erased user account.

**Root Cause:**
Intentional broken authentication flaw in implementation (key: `ghostLoginChallenge`)

**Affected Files:**
- `routes/login.ts`

**Entry Points:**
- API/UI refs in: routes/login.ts

**Impact:**
Enables gdpr data erasure attack scenario

**Remediation Strategy:**
Secure broken authentication per OWASP guidelines

**Files to Modify:**
- `routes/login.ts`

**Validation Steps:**
Confirm exploit for GDPR Data Erasure no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### GDPR Data Theft
<a id="dataexportchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `dataExportChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Medium |

**Description:**
Steal someone else's personal data without using Injection.

**Root Cause:**
Intentional sensitive data exposure flaw in implementation (key: `dataExportChallenge`)

**Affected Files:**
- `routes/dataExport.ts`

**Entry Points:**
- API/UI refs in: routes/dataExport.ts

**Impact:**
Enables gdpr data theft attack scenario

**Remediation Strategy:**
Secure sensitive data exposure per OWASP guidelines

**Files to Modify:**
- `routes/dataExport.ts`

**Validation Steps:**
Confirm exploit for GDPR Data Theft no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### HTTP-Header XSS
<a id="httpheaderxsschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `httpHeaderXssChallenge` |
| **Category** | XSS |
| **OWASP** | A03:2021 Injection (XSS) |
| **Difficulty** | Medium |

**Description:**
Perform a <i>persisted</i> XSS attack with <code>&lt;iframe src="javascript:alert(`xss`)"&gt;</code> through an HTTP header.

**Root Cause:**
Intentional xss flaw in implementation (key: `httpHeaderXssChallenge`)

**Affected Files:**
- `routes/saveLoginIp.ts`

**Entry Points:**
- API/UI refs in: routes/saveLoginIp.ts

**Impact:**
Enables http-header xss attack scenario

**Remediation Strategy:**
Secure xss per OWASP guidelines

**Files to Modify:**
- `routes/saveLoginIp.ts`

**Validation Steps:**
Confirm exploit for HTTP-Header XSS no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Imaginary Challenge
<a id="continuecodechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `continueCodeChallenge` |
| **Category** | Cryptographic Issues |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Hard |

**Description:**
Solve challenge #999. Unfortunately, this challenge does not exist.

**Root Cause:**
Intentional cryptographic issues flaw in implementation (key: `continueCodeChallenge`)

**Affected Files:**
- `routes/restoreProgress.ts`

**Entry Points:**
- API/UI refs in: routes/restoreProgress.ts

**Impact:**
Enables imaginary challenge attack scenario

**Remediation Strategy:**
Secure cryptographic issues per OWASP guidelines

**Files to Modify:**
- `routes/restoreProgress.ts`

**Validation Steps:**
Confirm exploit for Imaginary Challenge no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Leaked Access Logs
<a id="dlppasswordsprayingchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `dlpPasswordSprayingChallenge` |
| **Category** | Observability Failures |
| **OWASP** | A09:2021 Security Logging Failures |
| **Difficulty** | Hard |

**Description:**
Dumpster dive the Internet for a leaked password and log in to the original user account it belongs to. (Creating a new account with the same password does not qualify as a solution.)

**Root Cause:**
Intentional observability failures flaw in implementation (key: `dlpPasswordSprayingChallenge`)

**Affected Files:**
- `routes/login.ts`

**Entry Points:**
- API/UI refs in: routes/login.ts

**Impact:**
Enables leaked access logs attack scenario

**Remediation Strategy:**
Secure observability failures per OWASP guidelines

**Files to Modify:**
- `routes/login.ts`

**Validation Steps:**
Confirm exploit for Leaked Access Logs no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Leaked Unsafe Product
<a id="dlppastebindataleakchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `dlpPastebinDataLeakChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Medium |

**Description:**
Identify an unsafe product that was removed from the shop and <a href="/#/contact">inform the shop</a> which ingredients are dangerous.

**Root Cause:**
Intentional sensitive data exposure flaw in implementation (key: `dlpPastebinDataLeakChallenge`)

**Affected Files:**
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: routes/verify.ts

**Impact:**
Enables leaked unsafe product attack scenario

**Remediation Strategy:**
Secure sensitive data exposure per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Leaked Unsafe Product no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Legacy Typosquatting
<a id="typosquattingnpmchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `typosquattingNpmChallenge` |
| **Category** | Vulnerable Components |
| **OWASP** | A06:2021 Vulnerable Components |
| **Difficulty** | Medium |

**Description:**
<a href="/#/contact">Inform the shop</a> about a <i>typosquatting</i> trick it has been a victim of at least in <code>v6.2.0-SNAPSHOT</code>. (Mention the exact name of the culprit)

**Root Cause:**
Intentional vulnerable components flaw in implementation (key: `typosquattingNpmChallenge`)

**Affected Files:**
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: routes/verify.ts

**Impact:**
Enables legacy typosquatting attack scenario

**Remediation Strategy:**
Secure vulnerable components per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Legacy Typosquatting no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Login Admin
<a id="loginadminchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `loginAdminChallenge` |
| **Category** | Injection |
| **OWASP** | A03:2021 Injection |
| **CWE** | CWE-89 |
| **Difficulty** | Easy |

**Description:**
Log in with the administrator's user account.

**Root Cause:**
SQL injection in login via string-concatenated query

**Affected Files:**
- `routes/login.ts`

**Entry Points:**
- POST /rest/user/login

**Impact:**
Auth bypass as administrator

**Remediation Strategy:**
Parameterized queries via Sequelize

**Files to Modify:**
- `routes/login.ts`

**Validation Steps:**
SQLi in email field fails

**Cross-Impact Risk:**
None

**Dependencies:** `weakPasswordChallenge`

---
### Login Amy
<a id="loginamychallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `loginAmyChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Medium |

**Description:**
Log in with Amy's original user credentials. (This could take 93.83 billion trillion trillion centuries to brute force, but luckily she did not read the "One Important Final Note")

**Root Cause:**
Intentional sensitive data exposure flaw in implementation (key: `loginAmyChallenge`)

**Affected Files:**
- `routes/login.ts`

**Entry Points:**
- API/UI refs in: routes/login.ts

**Impact:**
Enables login amy attack scenario

**Remediation Strategy:**
Secure sensitive data exposure per OWASP guidelines

**Files to Modify:**
- `routes/login.ts`

**Validation Steps:**
Confirm exploit for Login Amy no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Login Bender
<a id="loginbenderchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `loginBenderChallenge` |
| **Category** | Injection |
| **OWASP** | A03:2021 Injection |
| **CWE** | CWE-89 |
| **Difficulty** | Easy |

**Description:**
Log in with Bender's user account.

**Root Cause:**
Same SQLi as loginAdmin on login endpoint

**Affected Files:**
- `routes/login.ts`

**Entry Points:**
- POST /rest/user/login

**Impact:**
Auth bypass as Bender

**Remediation Strategy:**
Parameterized queries

**Files to Modify:**
- `routes/login.ts`

**Validation Steps:**
SQLi blocked

**Cross-Impact Risk:**
None

---
### Login Bjoern
<a id="oauthuserpasswordchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `oauthUserPasswordChallenge` |
| **Category** | Broken Authentication |
| **OWASP** | A07:2021 Identification and Authentication Failures |
| **Difficulty** | Medium |

**Description:**
Log in with Bjoern's Gmail account <i>without</i> previously changing his password, applying SQL Injection, or hacking his Google account.

**Root Cause:**
Intentional broken authentication flaw in implementation (key: `oauthUserPasswordChallenge`)

**Affected Files:**
- `routes/login.ts`

**Entry Points:**
- API/UI refs in: routes/login.ts

**Impact:**
Enables login bjoern attack scenario

**Remediation Strategy:**
Secure broken authentication per OWASP guidelines

**Files to Modify:**
- `routes/login.ts`

**Validation Steps:**
Confirm exploit for Login Bjoern no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Login Jim
<a id="loginjimchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `loginJimChallenge` |
| **Category** | Injection |
| **OWASP** | A03:2021 Injection |
| **CWE** | CWE-89 |
| **Difficulty** | Easy |

**Description:**
Log in with Jim's user account.

**Root Cause:**
Same SQLi on login endpoint

**Affected Files:**
- `routes/login.ts`

**Entry Points:**
- POST /rest/user/login

**Impact:**
Auth bypass as Jim

**Remediation Strategy:**
Parameterized queries

**Files to Modify:**
- `routes/login.ts`

**Validation Steps:**
SQLi blocked

**Cross-Impact Risk:**
None

---
### Login MC SafeSearch
<a id="loginrapperchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `loginRapperChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Easy |

**Description:**
Log in with MC SafeSearch's original user credentials without applying SQL Injection or any other bypass.

**Root Cause:**
Intentional sensitive data exposure flaw in implementation (key: `loginRapperChallenge`)

**Affected Files:**
- `routes/login.ts`

**Entry Points:**
- API/UI refs in: routes/login.ts

**Impact:**
Enables login mc safesearch attack scenario

**Remediation Strategy:**
Secure sensitive data exposure per OWASP guidelines

**Files to Modify:**
- `routes/login.ts`

**Validation Steps:**
Confirm exploit for Login MC SafeSearch no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Login Support Team
<a id="loginsupportchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `loginSupportChallenge` |
| **Category** | Security Misconfiguration |
| **OWASP** | A05:2021 Security Misconfiguration |
| **Difficulty** | Hard |

**Description:**
Log in with the support team's original user credentials without applying SQL Injection or any other bypass.

**Root Cause:**
Intentional security misconfiguration flaw in implementation (key: `loginSupportChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `routes/login.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/login.ts

**Impact:**
Enables login support team attack scenario

**Remediation Strategy:**
Secure security misconfiguration per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `routes/login.ts`

**Validation Steps:**
Confirm exploit for Login Support Team no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Manipulate Basket
<a id="basketmanipulatechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `basketManipulateChallenge` |
| **Category** | Broken Access Control |
| **OWASP** | A01:2021 Broken Access Control |
| **CWE** | CWE-639 |
| **Difficulty** | Medium |

**Description:**
Put an additional product into another user's shopping basket.

**Root Cause:**
Basket item API allows adding to arbitrary BasketId

**Affected Files:**
- `routes/basketItems.ts`

**Entry Points:**
- POST /api/BasketItems

**Impact:**
Add products to others baskets

**Remediation Strategy:**
Validate basket ownership on item create

**Files to Modify:**
- `routes/basketItems.ts`

**Validation Steps:**
Cannot add to foreign basket

**Cross-Impact Risk:**
None

---
### Misplaced Signature File
<a id="misplacedsignaturefilechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `misplacedSignatureFileChallenge` |
| **Category** | Observability Failures |
| **OWASP** | A09:2021 Security Logging Failures |
| **Difficulty** | Medium |

**Description:**
Access a misplaced <a href="https://github.com/Neo23x0/sigma">SIEM signature</a> file.

**Root Cause:**
Intentional observability failures flaw in implementation (key: `misplacedSignatureFileChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `routes/fileServer.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/fileServer.ts

**Impact:**
Enables misplaced signature file attack scenario

**Remediation Strategy:**
Secure observability failures per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `routes/fileServer.ts`

**Validation Steps:**
Confirm exploit for Misplaced Signature File no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Multiple Likes
<a id="timingattackchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `timingAttackChallenge` |
| **Category** | Broken Anti Automation |
| **OWASP** | A07:2021 Auth Failures |
| **Difficulty** | Hard |

**Description:**
Like any review at least three times as the same user.

**Root Cause:**
Intentional broken anti automation flaw in implementation (key: `timingAttackChallenge`)

**Affected Files:**
- `routes/likeProductReviews.ts`

**Entry Points:**
- API/UI refs in: routes/likeProductReviews.ts

**Impact:**
Enables multiple likes attack scenario

**Remediation Strategy:**
Secure broken anti automation per OWASP guidelines

**Files to Modify:**
- `routes/likeProductReviews.ts`

**Validation Steps:**
Confirm exploit for Multiple Likes no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Nested Easter Egg
<a id="eastereggleveltwochallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `easterEggLevelTwoChallenge` |
| **Category** | Cryptographic Issues |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Medium |

**Description:**
Apply some advanced cryptanalysis to find <i>the real</i> easter egg.

**Root Cause:**
Intentional cryptographic issues flaw in implementation (key: `easterEggLevelTwoChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `routes/easterEgg.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/easterEgg.ts

**Impact:**
Enables nested easter egg attack scenario

**Remediation Strategy:**
Secure cryptographic issues per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `routes/easterEgg.ts`

**Validation Steps:**
Confirm exploit for Nested Easter Egg no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### NoSQL DoS
<a id="nosqlcommandchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `noSqlCommandChallenge` |
| **Category** | Injection |
| **OWASP** | A03:2021 Injection |
| **CWE** | CWE-943 |
| **Difficulty** | Medium |

**Description:**
Let the server sleep for some time. (It has done more than enough hard work for you)

**Root Cause:**
NoSQL injection in basket order query ($where sleep)

**Affected Files:**
- `routes/order.ts`
- `data/mongodb.ts`

**Entry Points:**
- POST /rest/basket/:id/checkout

**Impact:**
DoS via MongoDB sleep

**Remediation Strategy:**
Sanitize/parameterize NoSQL queries

**Files to Modify:**
- `routes/order.ts`

**Validation Steps:**
$where injection blocked

**Cross-Impact Risk:**
Order queries

---
### NoSQL Exfiltration
<a id="nosqlorderschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `noSqlOrdersChallenge` |
| **Category** | Injection |
| **OWASP** | A03:2021 Injection |
| **CWE** | CWE-943 |
| **Difficulty** | Hard |

**Description:**
All your orders are belong to us! Even the ones which don't.

**Root Cause:**
NoSQL injection in order history endpoint

**Affected Files:**
- `routes/orderHistory.ts`

**Entry Points:**
- GET /rest/order-history

**Impact:**
Access all orders

**Remediation Strategy:**
Strict query typing; no $where from user input

**Files to Modify:**
- `routes/orderHistory.ts`

**Validation Steps:**
Cannot retrieve others orders

**Cross-Impact Risk:**
None

---
### NoSQL Manipulation
<a id="nosqlreviewschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `noSqlReviewsChallenge` |
| **Category** | Injection |
| **OWASP** | A03:2021 Injection |
| **CWE** | CWE-943 |
| **Difficulty** | Medium |

**Description:**
Update multiple product reviews at the same time.

**Root Cause:**
NoSQL multi-update injection on reviews

**Affected Files:**
- `routes/productReviews.ts`

**Entry Points:**
- PATCH /rest/products/reviews

**Impact:**
Mass review manipulation

**Remediation Strategy:**
Validate update operators

**Files to Modify:**
- `routes/productReviews.ts`

**Validation Steps:**
Multi-update blocked

**Cross-Impact Risk:**
None

---
### Outdated Allowlist
<a id="redirectcryptocurrencychallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `redirectCryptoCurrencyChallenge` |
| **Category** | Unvalidated Redirects |
| **OWASP** | A01:2021 Broken Access Control |
| **Difficulty** | Easy |

**Description:**
Let us redirect you to one of our crypto currency addresses which are not promoted any longer.

**Root Cause:**
Intentional unvalidated redirects flaw in implementation (key: `redirectCryptoCurrencyChallenge`)

**Affected Files:**
- `lib/insecurity.ts`
- `routes/redirect.ts`

**Entry Points:**
- API/UI refs in: lib/insecurity.ts
- API/UI refs in: routes/redirect.ts

**Impact:**
Enables outdated allowlist attack scenario

**Remediation Strategy:**
Secure unvalidated redirects per OWASP guidelines

**Files to Modify:**
- `lib/insecurity.ts`
- `routes/redirect.ts`

**Validation Steps:**
Confirm exploit for Outdated Allowlist no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Password Strength
<a id="weakpasswordchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `weakPasswordChallenge` |
| **Category** | Broken Authentication |
| **OWASP** | A07:2021 Auth Failures |
| **CWE** | CWE-521 |
| **Difficulty** | Easy |

**Description:**
Log in with the administrator's user credentials without previously changing them or applying SQL Injection.

**Root Cause:**
Default admin password admin123

**Affected Files:**
- `data/static/users.yml`
- `routes/login.ts`

**Entry Points:**
- POST /rest/user/login

**Impact:**
Trivial admin compromise

**Remediation Strategy:**
Force strong passwords; remove default creds

**Files to Modify:**
- `data/static/users.yml`
- `routes/login.ts`

**Validation Steps:**
Default admin123 login fails

**Cross-Impact Risk:**
Seed data and docs update

---
### Payback Time
<a id="negativeorderchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `negativeOrderChallenge` |
| **Category** | Improper Input Validation |
| **OWASP** | A04:2021 Insecure Design |
| **Difficulty** | Medium |

**Description:**
Place an order that makes you rich.

**Root Cause:**
Intentional improper input validation flaw in implementation (key: `negativeOrderChallenge`)

**Affected Files:**
- `routes/order.ts`

**Entry Points:**
- API/UI refs in: routes/order.ts

**Impact:**
Enables payback time attack scenario

**Remediation Strategy:**
Secure improper input validation per OWASP guidelines

**Files to Modify:**
- `routes/order.ts`

**Validation Steps:**
Confirm exploit for Payback Time no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Premium Paywall
<a id="premiumpaywallchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `premiumPaywallChallenge` |
| **Category** | Cryptographic Issues |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Hard |

**Description:**
💎💎💎💎💎<!--IvLuRfBJYlmStf9XfL6ckJFngyd9LfV1JaaN/KRTPQPidTuJ7FR+D/nkWJUF+0xUF07CeCeqYfxq+OJVVa0gNbqgYkUNvn//UbE7e95C+6e+7GtdpqJ8mqm4WcPvUGIUxmGLTTAC2+G9UuFCD1DUjg==--> <a href="https://blockchain.info/address/1AbKfgvw9psQ41NbLi8kufDQTezwG8DRZm" target="_blank">₿ Unlock Premium Challenge</a> to access exclusive content.

**Root Cause:**
Intentional cryptographic issues flaw in implementation (key: `premiumPaywallChallenge`)

**Affected Files:**
- `routes/premiumReward.ts`

**Entry Points:**
- API/UI refs in: routes/premiumReward.ts

**Impact:**
Enables premium paywall attack scenario

**Remediation Strategy:**
Secure cryptographic issues per OWASP guidelines

**Files to Modify:**
- `routes/premiumReward.ts`

**Validation Steps:**
Confirm exploit for Premium Paywall no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Privacy Policy
<a id="privacypolicychallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `privacyPolicyChallenge` |
| **Category** | Miscellaneous |
| **OWASP** | Various |
| **Difficulty** | Easy |

**Description:**
Read our privacy policy.

**Root Cause:**
Intentional miscellaneous flaw in implementation (key: `privacyPolicyChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/verify.ts

**Impact:**
Enables privacy policy attack scenario

**Remediation Strategy:**
Secure miscellaneous per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Privacy Policy no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Privacy Policy Inspection
<a id="privacypolicyproofchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `privacyPolicyProofChallenge` |
| **Category** | Security through Obscurity |
| **OWASP** | A04:2021 Insecure Design |
| **Difficulty** | Medium |

**Description:**
Prove that you actually read our privacy policy.

**Root Cause:**
Intentional security through obscurity flaw in implementation (key: `privacyPolicyProofChallenge`)

**Affected Files:**
- `routes/privacyPolicyProof.ts`

**Entry Points:**
- API/UI refs in: routes/privacyPolicyProof.ts

**Impact:**
Enables privacy policy inspection attack scenario

**Remediation Strategy:**
Secure security through obscurity per OWASP guidelines

**Files to Modify:**
- `routes/privacyPolicyProof.ts`

**Validation Steps:**
Confirm exploit for Privacy Policy Inspection no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Product Tampering
<a id="changeproductchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `changeProductChallenge` |
| **Category** | Broken Access Control |
| **OWASP** | A01:2021 Broken Access Control |
| **Difficulty** | Medium |

**Description:**
Change the <code>href</code> of the link within the <a href="/#/search?q=OWASP SSL Advanced Forensic Tool (O-Saft)">OWASP SSL Advanced Forensic Tool (O-Saft)</a> product description into <i>https://owasp.slack.com</i>.

**Root Cause:**
Intentional broken access control flaw in implementation (key: `changeProductChallenge`)

**Affected Files:**
- `data/datacreator.ts`
- `routes/verify.ts`
- `server.ts`

**Entry Points:**
- API/UI refs in: data/datacreator.ts
- API/UI refs in: routes/verify.ts
- API/UI refs in: server.ts

**Impact:**
Enables product tampering attack scenario

**Remediation Strategy:**
Secure broken access control per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`
- `server.ts`

**Validation Steps:**
Confirm exploit for Product Tampering no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Reflected XSS
<a id="reflectedxsschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `reflectedXssChallenge` |
| **Category** | XSS |
| **OWASP** | A03:2021 Injection |
| **CWE** | CWE-79 |
| **Difficulty** | Easy |

**Description:**
Perform a <i>reflected</i> XSS attack with <code>&lt;iframe src="javascript:alert(`xss`)"&gt;</code>.

**Root Cause:**
URL parameter reflected without encoding in track-order or similar

**Affected Files:**
- `frontend/src/app/track-result/track-result.component.ts`

**Entry Points:**
- /#/track-result/new/:id

**Impact:**
Reflected XSS

**Remediation Strategy:**
Angular sanitization / avoid bypassSecurityTrustHtml

**Files to Modify:**
- `frontend/src/app/track-result/track-result.component.ts`

**Validation Steps:**
XSS payload reflected safely

**Cross-Impact Risk:**
None

---
### Repetitive Registration
<a id="passwordrepeatchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `passwordRepeatChallenge` |
| **Category** | Improper Input Validation |
| **OWASP** | A04:2021 Insecure Design |
| **Difficulty** | Easy |

**Description:**
Follow the DRY principle while registering a user.

**Root Cause:**
Intentional improper input validation flaw in implementation (key: `passwordRepeatChallenge`)

**Affected Files:**
- `routes/verify.ts`
- `server.ts`

**Entry Points:**
- API/UI refs in: routes/verify.ts
- API/UI refs in: server.ts

**Impact:**
Enables repetitive registration attack scenario

**Remediation Strategy:**
Secure improper input validation per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`
- `server.ts`

**Validation Steps:**
Confirm exploit for Repetitive Registration no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Reset Bender's Password
<a id="resetpasswordbenderchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `resetPasswordBenderChallenge` |
| **Category** | Broken Authentication |
| **OWASP** | A07:2021 Identification and Authentication Failures |
| **Difficulty** | Medium |

**Description:**
Reset Bender's password via the <a href="/#/forgot-password">Forgot Password</a> mechanism with <i>the original answer</i> to his security question.

**Root Cause:**
Intentional broken authentication flaw in implementation (key: `resetPasswordBenderChallenge`)

**Affected Files:**
- `routes/resetPassword.ts`

**Entry Points:**
- API/UI refs in: routes/resetPassword.ts

**Impact:**
Enables reset bender's password attack scenario

**Remediation Strategy:**
Secure broken authentication per OWASP guidelines

**Files to Modify:**
- `routes/resetPassword.ts`

**Validation Steps:**
Confirm exploit for Reset Bender's Password no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Reset Bjoern's Password
<a id="resetpasswordbjoernchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `resetPasswordBjoernChallenge` |
| **Category** | Broken Authentication |
| **OWASP** | A07:2021 Identification and Authentication Failures |
| **Difficulty** | Hard |

**Description:**
Reset the password of Bjoern's internal account via the <a href="/#/forgot-password">Forgot Password</a> mechanism with <i>the original answer</i> to his security question.

**Root Cause:**
Intentional broken authentication flaw in implementation (key: `resetPasswordBjoernChallenge`)

**Affected Files:**
- `routes/resetPassword.ts`

**Entry Points:**
- API/UI refs in: routes/resetPassword.ts

**Impact:**
Enables reset bjoern's password attack scenario

**Remediation Strategy:**
Secure broken authentication per OWASP guidelines

**Files to Modify:**
- `routes/resetPassword.ts`

**Validation Steps:**
Confirm exploit for Reset Bjoern's Password no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Reset Jim's Password
<a id="resetpasswordjimchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `resetPasswordJimChallenge` |
| **Category** | Broken Authentication |
| **OWASP** | A07:2021 Identification and Authentication Failures |
| **Difficulty** | Medium |

**Description:**
Reset Jim's password via the <a href="/#/forgot-password">Forgot Password</a> mechanism with <i>the original answer</i> to his security question.

**Root Cause:**
Intentional broken authentication flaw in implementation (key: `resetPasswordJimChallenge`)

**Affected Files:**
- `routes/resetPassword.ts`

**Entry Points:**
- API/UI refs in: routes/resetPassword.ts

**Impact:**
Enables reset jim's password attack scenario

**Remediation Strategy:**
Secure broken authentication per OWASP guidelines

**Files to Modify:**
- `routes/resetPassword.ts`

**Validation Steps:**
Confirm exploit for Reset Jim's Password no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Reset Morty's Password
<a id="resetpasswordmortychallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `resetPasswordMortyChallenge` |
| **Category** | Broken Anti Automation |
| **OWASP** | A07:2021 Auth Failures |
| **Difficulty** | Hard |

**Description:**
Reset Morty's password via the <a href="/#/forgot-password">Forgot Password</a> mechanism with <i>his obfuscated answer</i> to his security question.

**Root Cause:**
Intentional broken anti automation flaw in implementation (key: `resetPasswordMortyChallenge`)

**Affected Files:**
- `routes/resetPassword.ts`
- `server.ts`

**Entry Points:**
- API/UI refs in: routes/resetPassword.ts
- API/UI refs in: server.ts

**Impact:**
Enables reset morty's password attack scenario

**Remediation Strategy:**
Secure broken anti automation per OWASP guidelines

**Files to Modify:**
- `routes/resetPassword.ts`
- `server.ts`

**Validation Steps:**
Confirm exploit for Reset Morty's Password no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Retrieve Blueprint
<a id="retrieveblueprintchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `retrieveBlueprintChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Hard |

**Description:**
Deprive the shop of earnings by downloading the blueprint for one of its products.

**Root Cause:**
Intentional sensitive data exposure flaw in implementation (key: `retrieveBlueprintChallenge`)

**Affected Files:**
- `data/datacache.ts`
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: data/datacache.ts
- API/UI refs in: routes/verify.ts

**Impact:**
Enables retrieve blueprint attack scenario

**Remediation Strategy:**
Secure sensitive data exposure per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Retrieve Blueprint no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### SSRF
<a id="ssrfchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `ssrfChallenge` |
| **Category** | Broken Access Control |
| **OWASP** | A10:2021 SSRF |
| **CWE** | CWE-918 |
| **Difficulty** | Hard |

**Description:**
Request a hidden resource on server through server.

**Root Cause:**
SSRF via profile image URL or malware callback

**Affected Files:**
- `routes/profileImageUrlUpload.ts`
- `routes/redirect.ts`

**Entry Points:**
- POST profile/redirect handlers

**Impact:**
Server-side request to internal resources

**Remediation Strategy:**
URL allowlist; block internal IPs

**Files to Modify:**
- `routes/profileImageUrlUpload.ts`

**Validation Steps:**
Internal URLs blocked

**Cross-Impact Risk:**
Image URL feature

---
### SSTi
<a id="sstichallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `sstiChallenge` |
| **Category** | Injection |
| **OWASP** | A03:2021 Injection |
| **CWE** | CWE-94 |
| **Difficulty** | Hard |

**Description:**
Infect the server with juicy malware by abusing arbitrary command execution.

**Root Cause:**
User input passed to template engine in profile update

**Affected Files:**
- `routes/updateUserProfile.ts`

**Entry Points:**
- PUT /rest/user/profile

**Impact:**
RCE via template injection

**Remediation Strategy:**
Never compile user input as templates

**Files to Modify:**
- `routes/updateUserProfile.ts`

**Validation Steps:**
SSTI payloads blocked

**Cross-Impact Risk:**
Profile features limited

---
### Score Board
<a id="scoreboardchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `scoreBoardChallenge` |
| **Category** | Miscellaneous |
| **OWASP** | Information Disclosure |
| **CWE** | N/A |
| **Difficulty** | Easy |

**Description:**
Find the carefully hidden 'Score Board' page.

**Root Cause:**
Hidden score-board route in app.routing.ts without access control

**Affected Files:**
- `frontend/src/app/app.routing.ts`

**Entry Points:**
- /#/score-board

**Impact:**
Reveals all challenge names to users

**Remediation Strategy:**
Remove or protect score board in production builds

**Files to Modify:**
- `frontend/src/app/app.routing.ts`

**Validation Steps:**
Route not discoverable

**Cross-Impact Risk:**
Training feature removed

---
### Security Policy
<a id="securitypolicychallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `securityPolicyChallenge` |
| **Category** | Miscellaneous |
| **OWASP** | Various |
| **Difficulty** | Easy |

**Description:**
Behave like any "white-hat" should before getting into the action.

**Root Cause:**
Intentional miscellaneous flaw in implementation (key: `securityPolicyChallenge`)

**Affected Files:**
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: routes/verify.ts

**Impact:**
Enables security policy attack scenario

**Remediation Strategy:**
Secure miscellaneous per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Security Policy no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Server-side XSS Protection
<a id="persistedxssfeedbackchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `persistedXssFeedbackChallenge` |
| **Category** | XSS |
| **OWASP** | A03:2021 Injection (XSS) |
| **Difficulty** | Medium |

**Description:**
Perform a <i>persisted</i> XSS attack with <code>&lt;iframe src="javascript:alert(`xss`)"&gt;</code> bypassing a <i>server-side</i> security mechanism.

**Root Cause:**
Intentional xss flaw in implementation (key: `persistedXssFeedbackChallenge`)

**Affected Files:**
- `models/feedback.ts`

**Entry Points:**
- API/UI refs in: models/feedback.ts

**Impact:**
Enables server-side xss protection attack scenario

**Remediation Strategy:**
Secure xss per OWASP guidelines

**Files to Modify:**

**Validation Steps:**
Confirm exploit for Server-side XSS Protection no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Steganography
<a id="hiddenimagechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `hiddenImageChallenge` |
| **Category** | Security through Obscurity |
| **OWASP** | A04:2021 Insecure Design |
| **Difficulty** | Medium |

**Description:**
<a href="/#/contact">Rat out</a> a notorious character hiding in plain sight in the shop. (Mention the exact name of the character)

**Root Cause:**
Intentional security through obscurity flaw in implementation (key: `hiddenImageChallenge`)

**Affected Files:**
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: routes/verify.ts

**Impact:**
Enables steganography attack scenario

**Remediation Strategy:**
Secure security through obscurity per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Steganography no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Successful RCE DoS
<a id="rceoccupychallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `rceOccupyChallenge` |
| **Category** | Insecure Deserialization |
| **OWASP** | A08:2021 Software and Data Integrity Failures |
| **Difficulty** | Hard |

**Description:**
Perform a Remote Code Execution that occupies the server for a while without using infinite loops.

**Root Cause:**
Intentional insecure deserialization flaw in implementation (key: `rceOccupyChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `routes/b2bOrder.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/b2bOrder.ts

**Impact:**
Enables successful rce dos attack scenario

**Remediation Strategy:**
Secure insecure deserialization per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `routes/b2bOrder.ts`

**Validation Steps:**
Confirm exploit for Successful RCE DoS no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Supply Chain Attack
<a id="supplychainattackchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `supplyChainAttackChallenge` |
| **Category** | Vulnerable Components |
| **OWASP** | A06:2021 Vulnerable Components |
| **Difficulty** | Hard |

**Description:**
<a href="/#/contact">Inform the development team</a> about a danger to some of <em>their</em> credentials. (Send them the URL of the <em>original report</em> or an assigned CVE or another identifier of this vulnerability)

**Root Cause:**
Intentional vulnerable components flaw in implementation (key: `supplyChainAttackChallenge`)

**Affected Files:**
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: routes/verify.ts

**Impact:**
Enables supply chain attack attack scenario

**Remediation Strategy:**
Secure vulnerable components per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Supply Chain Attack no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Two Factor Authentication
<a id="twofactorauthunsafesecretstoragechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `twoFactorAuthUnsafeSecretStorageChallenge` |
| **Category** | Broken Authentication |
| **OWASP** | A07:2021 Identification and Authentication Failures |
| **Difficulty** | Hard |

**Description:**
Solve the 2FA challenge for user "wurstbrot". (Disabling, bypassing or overwriting his 2FA settings does not count as a solution)

**Root Cause:**
Intentional broken authentication flaw in implementation (key: `twoFactorAuthUnsafeSecretStorageChallenge`)

**Affected Files:**
- `routes/2fa.ts`

**Entry Points:**
- API/UI refs in: routes/2fa.ts

**Impact:**
Enables two factor authentication attack scenario

**Remediation Strategy:**
Secure broken authentication per OWASP guidelines

**Files to Modify:**
- `routes/2fa.ts`

**Validation Steps:**
Confirm exploit for Two Factor Authentication no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Unsigned JWT
<a id="jwtunsignedchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `jwtUnsignedChallenge` |
| **Category** | Vulnerable Components |
| **OWASP** | A07:2021 Auth Failures |
| **CWE** | CWE-347 |
| **Difficulty** | Medium |

**Description:**
Forge an essentially unsigned JWT token that impersonates the (non-existing) user <i>jwtn3d@juice-sh.op</i>.

**Root Cause:**
JWT accepts alg:none / missing signature verification

**Affected Files:**
- `lib/insecurity.ts`

**Entry Points:**
- Authorization: Bearer on all routes

**Impact:**
Account impersonation

**Remediation Strategy:**
Enforce RS256/HS256 with signature verification

**Files to Modify:**
- `lib/insecurity.ts`

**Validation Steps:**
Unsigned JWT rejected

**Cross-Impact Risk:**
All auth flows

---
### Upload Size
<a id="uploadsizechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `uploadSizeChallenge` |
| **Category** | Improper Input Validation |
| **OWASP** | A04:2021 Insecure Design |
| **Difficulty** | Medium |

**Description:**
Upload a file larger than 100 kB.

**Root Cause:**
Intentional improper input validation flaw in implementation (key: `uploadSizeChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `routes/fileUpload.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/fileUpload.ts

**Impact:**
Enables upload size attack scenario

**Remediation Strategy:**
Secure improper input validation per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `routes/fileUpload.ts`

**Validation Steps:**
Confirm exploit for Upload Size no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

**Dependencies:** `uploadTypeChallenge`

---
### Upload Type
<a id="uploadtypechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `uploadTypeChallenge` |
| **Category** | Improper Input Validation |
| **OWASP** | A04:2021 Insecure Design |
| **Difficulty** | Medium |

**Description:**
Upload a file that has no .pdf or .zip extension.

**Root Cause:**
Intentional improper input validation flaw in implementation (key: `uploadTypeChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `routes/fileUpload.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/fileUpload.ts

**Impact:**
Enables upload type attack scenario

**Remediation Strategy:**
Secure improper input validation per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `routes/fileUpload.ts`

**Validation Steps:**
Confirm exploit for Upload Type no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

**Dependencies:** `xxeFileDisclosureChallenge`

---
### User Credentials
<a id="unionsqlinjectionchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `unionSqlInjectionChallenge` |
| **Category** | Injection |
| **OWASP** | A03:2021 Injection |
| **CWE** | CWE-89 |
| **Difficulty** | Medium |

**Description:**
Retrieve a list of all user credentials via SQL Injection.

**Root Cause:**
Unsanitized search criteria in SQL query

**Affected Files:**
- `routes/search.ts`

**Entry Points:**
- GET /rest/products/search?q=

**Impact:**
Credential exfiltration via UNION

**Remediation Strategy:**
Parameterized queries

**Files to Modify:**
- `routes/search.ts`

**Validation Steps:**
UNION payloads fail

**Cross-Impact Risk:**
None

---
### Video XSS
<a id="videoxsschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `videoXssChallenge` |
| **Category** | XSS |
| **OWASP** | A03:2021 Injection (XSS) |
| **Difficulty** | Hard |

**Description:**
Embed an XSS payload <code>&lt;/script&gt;&lt;script&gt;alert(`xss`)&lt;/script&gt;</code> into our promo video.

**Root Cause:**
Intentional xss flaw in implementation (key: `videoXssChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `routes/videoHandler.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/videoHandler.ts

**Impact:**
Enables video xss attack scenario

**Remediation Strategy:**
Secure xss per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `routes/videoHandler.ts`

**Validation Steps:**
Confirm exploit for Video XSS no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### View Basket
<a id="basketaccesschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `basketAccessChallenge` |
| **Category** | Broken Access Control |
| **OWASP** | A01:2021 Broken Access Control |
| **CWE** | CWE-639 |
| **Difficulty** | Easy |

**Description:**
View another user's shopping basket.

**Root Cause:**
Basket IDOR - any user can view any basket by ID

**Affected Files:**
- `routes/basket.ts`

**Entry Points:**
- GET /rest/basket/:id

**Impact:**
View other users shopping carts

**Remediation Strategy:**
Verify basket belongs to authenticated user

**Files to Modify:**
- `routes/basket.ts`

**Validation Steps:**
Cannot access other bid

**Cross-Impact Risk:**
None

---
### Vulnerable Library
<a id="knownvulnerablecomponentchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `knownVulnerableComponentChallenge` |
| **Category** | Vulnerable Components |
| **OWASP** | A06:2021 Vulnerable Components |
| **Difficulty** | Medium |

**Description:**
<a href="/#/contact">Inform the shop</a> about a high-severity vulnerability caused by one of its directly used dependencies. (Mention the exact library name and version in your comment)

**Root Cause:**
Intentional vulnerable components flaw in implementation (key: `knownVulnerableComponentChallenge`)

**Affected Files:**
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: routes/verify.ts

**Impact:**
Enables vulnerable library attack scenario

**Remediation Strategy:**
Secure vulnerable components per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Vulnerable Library no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Weird Crypto
<a id="weirdcryptochallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `weirdCryptoChallenge` |
| **Category** | Cryptographic Issues |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Easy |

**Description:**
<a href="/#/contact">Inform the shop</a> about an algorithm or library it should definitely not use the way it does.

**Root Cause:**
Intentional cryptographic issues flaw in implementation (key: `weirdCryptoChallenge`)

**Affected Files:**
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: routes/verify.ts

**Impact:**
Enables weird crypto attack scenario

**Remediation Strategy:**
Secure cryptographic issues per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Weird Crypto no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Allowlist Bypass
<a id="redirectchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `redirectChallenge` |
| **Category** | Unvalidated Redirects |
| **OWASP** | A01:2021 Broken Access Control |
| **CWE** | CWE-601 |
| **Difficulty** | Medium |

**Description:**
Enforce a redirect to a page you are not supposed to redirect to.

**Root Cause:**
Open redirect with weak allowlist bypass

**Affected Files:**
- `routes/redirect.ts`
- `lib/insecurity.ts`

**Entry Points:**
- GET /redirect?to=

**Impact:**
Phishing via open redirect

**Remediation Strategy:**
Strict URL validation allowlist

**Files to Modify:**
- `routes/redirect.ts`
- `lib/insecurity.ts`

**Validation Steps:**
External redirects blocked

**Cross-Impact Risk:**
Redirect feature

---
### XXE Data Access
<a id="xxefiledisclosurechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `xxeFileDisclosureChallenge` |
| **Category** | XXE |
| **OWASP** | A05:2021 Security Misconfiguration |
| **CWE** | CWE-611 |
| **Difficulty** | Medium |

**Description:**
Retrieve the content of <code>C:\Windows\system.ini</code> or <code>/etc/passwd</code> from the server.

**Root Cause:**
XXE in deprecated B2B XML upload

**Affected Files:**
- `routes/b2bOrder.ts`

**Entry Points:**
- POST /b2b/v2/orders

**Impact:**
Local file read via XXE

**Remediation Strategy:**
Disable DTD/external entities; use JSON API

**Files to Modify:**
- `routes/b2bOrder.ts`

**Validation Steps:**
XXE payloads fail

**Cross-Impact Risk:**
B2B XML deprecated

---
### XXE DoS
<a id="xxedoschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `xxeDosChallenge` |
| **Category** | XXE |
| **OWASP** | A05:2021 Security Misconfiguration |
| **CWE** | CWE-776 |
| **Difficulty** | Hard |

**Description:**
Give the server something to chew on for quite a while.

**Root Cause:**
Billion laughs XXE DoS

**Affected Files:**
- `routes/b2bOrder.ts`

**Entry Points:**
- POST /b2b/v2/orders

**Impact:**
DoS via entity expansion

**Remediation Strategy:**
Disable entity expansion in XML parser

**Files to Modify:**
- `routes/b2bOrder.ts`

**Validation Steps:**
YAML/XML bomb rejected

**Cross-Impact Risk:**
None

---
### Memory Bomb
<a id="yamlbombchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `yamlBombChallenge` |
| **Category** | Insecure Deserialization |
| **OWASP** | A08:2021 Integrity Failures |
| **CWE** | CWE-776 |
| **Difficulty** | Hard |

**Description:**
Drop some explosive data into a vulnerable file-handling endpoint.

**Root Cause:**
Unsafe YAML deserialization on upload

**Affected Files:**
- `routes/fileUpload.ts`

**Entry Points:**
- POST /file-upload

**Impact:**
Memory exhaustion DoS

**Remediation Strategy:**
Use safe YAML loader; reject anchors

**Files to Modify:**
- `routes/fileUpload.ts`

**Validation Steps:**
YAML bomb blocked

**Cross-Impact Risk:**
Upload types restricted

---
### Zero Stars
<a id="zerostarschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `zeroStarsChallenge` |
| **Category** | Improper Input Validation |
| **OWASP** | A04:2021 Insecure Design |
| **Difficulty** | Easy |

**Description:**
Give a devastating zero-star feedback to the store.

**Root Cause:**
Intentional improper input validation flaw in implementation (key: `zeroStarsChallenge`)

**Affected Files:**
- `models/feedback.ts`

**Entry Points:**
- API/UI refs in: models/feedback.ts

**Impact:**
Enables zero stars attack scenario

**Remediation Strategy:**
Secure improper input validation per OWASP guidelines

**Files to Modify:**

**Validation Steps:**
Confirm exploit for Zero Stars no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Missing Encoding
<a id="missingencodingchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `missingEncodingChallenge` |
| **Category** | Improper Input Validation |
| **OWASP** | A04:2021 Insecure Design |
| **Difficulty** | Easy |

**Description:**
Retrieve the photo of Bjoern's cat in "melee combat-mode".

**Root Cause:**
Intentional improper input validation flaw in implementation (key: `missingEncodingChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/verify.ts

**Impact:**
Enables missing encoding attack scenario

**Remediation Strategy:**
Secure improper input validation per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Missing Encoding no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Cross-Site Imaging
<a id="svginjectionchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `svgInjectionChallenge` |
| **Category** | Security Misconfiguration |
| **OWASP** | A05:2021 Security Misconfiguration |
| **Difficulty** | Hard |

**Description:**
Stick <a href="https://cataas.com/cat" target="_blank">cute cross-domain kittens</a> all over our delivery boxes.

**Root Cause:**
Intentional security misconfiguration flaw in implementation (key: `svgInjectionChallenge`)

**Affected Files:**
- `lib/startup/registerWebsocketEvents.ts`

**Entry Points:**
- API/UI refs in: lib/startup/registerWebsocketEvents.ts

**Impact:**
Enables cross-site imaging attack scenario

**Remediation Strategy:**
Secure security misconfiguration per OWASP guidelines

**Files to Modify:**
- `lib/startup/registerWebsocketEvents.ts`

**Validation Steps:**
Confirm exploit for Cross-Site Imaging no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Exposed Metrics
<a id="exposedmetricschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `exposedMetricsChallenge` |
| **Category** | Observability Failures |
| **OWASP** | A05:2021 Security Misconfiguration |
| **CWE** | CWE-200 |
| **Difficulty** | Easy |

**Description:**
Find the endpoint that serves usage data to be scraped by a <a href="https://github.com/prometheus/prometheus">popular monitoring system</a>.

**Root Cause:**
Prometheus metrics exposed without auth at /metrics

**Affected Files:**
- `server.ts`
- `lib/metrics.ts`

**Entry Points:**
- GET /metrics

**Impact:**
Internal metrics disclosure

**Remediation Strategy:**
Protect metrics endpoint

**Files to Modify:**
- `server.ts`

**Validation Steps:**
Metrics require auth

**Cross-Impact Risk:**
Monitoring setup

---
### Deluxe Fraud
<a id="freedeluxechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `freeDeluxeChallenge` |
| **Category** | Improper Input Validation |
| **OWASP** | A04:2021 Insecure Design |
| **Difficulty** | Medium |

**Description:**
Obtain a Deluxe Membership without paying for it.

**Root Cause:**
Intentional improper input validation flaw in implementation (key: `freeDeluxeChallenge`)

**Affected Files:**
- `routes/deluxe.ts`

**Entry Points:**
- API/UI refs in: routes/deluxe.ts

**Impact:**
Enables deluxe fraud attack scenario

**Remediation Strategy:**
Secure improper input validation per OWASP guidelines

**Files to Modify:**
- `routes/deluxe.ts`

**Validation Steps:**
Confirm exploit for Deluxe Fraud no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### CSRF
<a id="csrfchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `csrfChallenge` |
| **Category** | Broken Access Control |
| **OWASP** | A01:2021 Broken Access Control |
| **CWE** | CWE-352 |
| **Difficulty** | Medium |

**Description:**
Change the name of a user by performing Cross-Site Request Forgery from <a href="http://htmledit.squarefree.com">another origin</a>.

**Root Cause:**
Missing CSRF token on state-changing forms

**Affected Files:**
- `routes/updateUserProfile.ts`

**Entry Points:**
- POST /profile
- Various forms

**Impact:**
Cross-site request forgery

**Remediation Strategy:**
CSRF tokens on all state-changing endpoints

**Files to Modify:**
- `routes/updateUserProfile.ts`
- `server.ts`

**Validation Steps:**
CSRF token required

**Cross-Impact Risk:**
Frontend must send token

---
### Bonus Payload
<a id="xssbonuschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `xssBonusChallenge` |
| **Category** | XSS |
| **OWASP** | A03:2021 Injection (XSS) |
| **Difficulty** | Easy |

**Description:**
Use the bonus payload <code>&lt;iframe width=&quot;100%&quot; height=&quot;166&quot; scrolling=&quot;no&quot; frameborder=&quot;no&quot; allow=&quot;autoplay&quot; src=&quot;https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/771984076&amp;color=%23ff5500&amp;auto_play=true&amp;hide_related=false&amp;show_comments=true&amp;show_user=true&amp;show_reposts=false&amp;show_teaser=true&quot;&gt;&lt;/iframe&gt;</code> in the <i>DOM XSS</i> challenge.

**Root Cause:**
Intentional xss flaw in implementation (key: `xssBonusChallenge`)

**Affected Files:**
- `frontend/src/app/search-result/search-result.component.ts`
- `lib/antiCheat.ts`
- `lib/startup/registerWebsocketEvents.ts`

**Entry Points:**
- API/UI refs in: frontend/src/app/search-result/search-result.component.ts
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: lib/startup/registerWebsocketEvents.ts

**Impact:**
Enables bonus payload attack scenario

**Remediation Strategy:**
Secure xss per OWASP guidelines

**Files to Modify:**
- `frontend/src/app/search-result/search-result.component.ts`
- `lib/antiCheat.ts`
- `lib/startup/registerWebsocketEvents.ts`

**Validation Steps:**
Confirm exploit for Bonus Payload no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Reset Uvogin's Password
<a id="resetpassworduvoginchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `resetPasswordUvoginChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Medium |

**Description:**
Reset Uvogin's password via the <a href="/#/forgot-password">Forgot Password</a> mechanism with <i>the original answer</i> to his security question.

**Root Cause:**
Intentional sensitive data exposure flaw in implementation (key: `resetPasswordUvoginChallenge`)

**Affected Files:**
- `routes/resetPassword.ts`

**Entry Points:**
- API/UI refs in: routes/resetPassword.ts

**Impact:**
Enables reset uvogin's password attack scenario

**Remediation Strategy:**
Secure sensitive data exposure per OWASP guidelines

**Files to Modify:**
- `routes/resetPassword.ts`

**Validation Steps:**
Confirm exploit for Reset Uvogin's Password no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Meta Geo Stalking
<a id="geostalkingmetachallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `geoStalkingMetaChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Easy |

**Description:**
Determine the answer to John's security question by looking at an upload of him to the Photo Wall and use it to reset his password via the <a href="/#/forgot-password">Forgot Password</a> mechanism.

**Root Cause:**
Intentional sensitive data exposure flaw in implementation (key: `geoStalkingMetaChallenge`)

**Affected Files:**
- `routes/resetPassword.ts`

**Entry Points:**
- API/UI refs in: routes/resetPassword.ts

**Impact:**
Enables meta geo stalking attack scenario

**Remediation Strategy:**
Secure sensitive data exposure per OWASP guidelines

**Files to Modify:**
- `routes/resetPassword.ts`

**Validation Steps:**
Confirm exploit for Meta Geo Stalking no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Visual Geo Stalking
<a id="geostalkingvisualchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `geoStalkingVisualChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Easy |

**Description:**
Determine the answer to Emma's security question by looking at an upload of her to the Photo Wall and use it to reset her password via the <a href="/#/forgot-password">Forgot Password</a> mechanism.

**Root Cause:**
Intentional sensitive data exposure flaw in implementation (key: `geoStalkingVisualChallenge`)

**Affected Files:**
- `routes/resetPassword.ts`

**Entry Points:**
- API/UI refs in: routes/resetPassword.ts

**Impact:**
Enables visual geo stalking attack scenario

**Remediation Strategy:**
Secure sensitive data exposure per OWASP guidelines

**Files to Modify:**
- `routes/resetPassword.ts`

**Validation Steps:**
Confirm exploit for Visual Geo Stalking no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Poison Null Byte
<a id="nullbytechallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `nullByteChallenge` |
| **Category** | Improper Input Validation |
| **OWASP** | A04:2021 Insecure Design |
| **Difficulty** | Medium |

**Description:**
Bypass a security control with a <a href="https://hakipedia.com/index.php/Poison_Null_Byte">Poison Null Byte</a> to access a file not meant for your eyes.

**Root Cause:**
Intentional improper input validation flaw in implementation (key: `nullByteChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `routes/fileServer.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: routes/fileServer.ts

**Impact:**
Enables poison null byte attack scenario

**Remediation Strategy:**
Secure improper input validation per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `routes/fileServer.ts`

**Validation Steps:**
Confirm exploit for Poison Null Byte no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

**Dependencies:** `easterEggLevelOneChallenge`, `forgottenDevBackupChallenge`

---
### Local File Read
<a id="lfrchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `lfrChallenge` |
| **Category** | Vulnerable Components |
| **OWASP** | A06:2021 Vulnerable Components |
| **Difficulty** | Hard |

**Description:**
Gain read access to an arbitrary local file on the web server.

**Root Cause:**
Intentional vulnerable components flaw in implementation (key: `lfrChallenge`)

**Affected Files:**
- `routes/dataErasure.ts`

**Entry Points:**
- API/UI refs in: routes/dataErasure.ts

**Impact:**
Enables local file read attack scenario

**Remediation Strategy:**
Secure vulnerable components per OWASP guidelines

**Files to Modify:**
- `routes/dataErasure.ts`

**Validation Steps:**
Confirm exploit for Local File Read no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Mass Dispel
<a id="closenotificationschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `closeNotificationsChallenge` |
| **Category** | Miscellaneous |
| **OWASP** | Various |
| **Difficulty** | Easy |

**Description:**
Close multiple "Challenge solved"-notifications in one go.

**Root Cause:**
Intentional miscellaneous flaw in implementation (key: `closeNotificationsChallenge`)

**Affected Files:**
- `lib/antiCheat.ts`
- `lib/startup/registerWebsocketEvents.ts`

**Entry Points:**
- API/UI refs in: lib/antiCheat.ts
- API/UI refs in: lib/startup/registerWebsocketEvents.ts

**Impact:**
Enables mass dispel attack scenario

**Remediation Strategy:**
Secure miscellaneous per OWASP guidelines

**Files to Modify:**
- `lib/antiCheat.ts`
- `lib/startup/registerWebsocketEvents.ts`

**Validation Steps:**
Confirm exploit for Mass Dispel no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Security Advisory
<a id="csafchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `csafChallenge` |
| **Category** | Miscellaneous |
| **OWASP** | Various |
| **Difficulty** | Medium |

**Description:**
The Juice Shop is susceptible to a known vulnerability in a library, for which an advisory has already been issued, marking the Juice Shop as <i>known affected</i>. A fix is still pending. <a href="/#/contact">Inform the shop</a> about a suitable checksum as proof that you did your due diligence.

**Root Cause:**
Intentional miscellaneous flaw in implementation (key: `csafChallenge`)

**Affected Files:**
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: routes/verify.ts

**Impact:**
Enables security advisory attack scenario

**Remediation Strategy:**
Secure miscellaneous per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Security Advisory no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Exposed Credentials
<a id="exposedcredentialschallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `exposedCredentialsChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Easy |

**Description:**
A developer was careless with hardcoding unused, but still valid credentials for a testing account on the client-side.

**Root Cause:**
Intentional sensitive data exposure flaw in implementation (key: `exposedCredentialsChallenge`)

**Affected Files:**
- `routes/login.ts`

**Entry Points:**
- API/UI refs in: routes/login.ts

**Impact:**
Enables exposed credentials attack scenario

**Remediation Strategy:**
Secure sensitive data exposure per OWASP guidelines

**Files to Modify:**
- `routes/login.ts`

**Validation Steps:**
Confirm exploit for Exposed Credentials no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Leaked API Key
<a id="leakedapikeychallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `leakedApiKeyChallenge` |
| **Category** | Sensitive Data Exposure |
| **OWASP** | A02:2021 Cryptographic Failures |
| **Difficulty** | Hard |

**Description:**
<a href="/#/contact">Inform the shop</a> about a leaked API key. (Mention the exact key in your comment)

**Root Cause:**
Intentional sensitive data exposure flaw in implementation (key: `leakedApiKeyChallenge`)

**Affected Files:**
- `routes/verify.ts`

**Entry Points:**
- API/UI refs in: routes/verify.ts

**Impact:**
Enables leaked api key attack scenario

**Remediation Strategy:**
Secure sensitive data exposure per OWASP guidelines

**Files to Modify:**
- `routes/verify.ts`

**Validation Steps:**
Confirm exploit for Leaked API Key no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### Chatbot Prompt Injection
<a id="chatbotpromptinjectionchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `chatbotPromptInjectionChallenge` |
| **Category** | Injection |
| **OWASP** | LLM01:2025 Prompt Injection |
| **Difficulty** | Medium |

**Description:**
Trick the chatbot into generating a coupon code for you despite its coupon policy saying otherwise.

**Root Cause:**
User input concatenated into LLM prompt without isolation

**Affected Files:**
- `routes/chat.ts`

**Entry Points:**
- POST /rest/chatbot/respond

**Impact:**
Override chatbot behavior

**Remediation Strategy:**
Prompt sandboxing; input/output filtering

**Files to Modify:**
- `routes/chat.ts`

**Validation Steps:**
Injection strings ineffective

**Cross-Impact Risk:**
Chatbot UX

---
### Greedy Chatbot Manipulation
<a id="chatbotgreedyinjectionchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `chatbotGreedyInjectionChallenge` |
| **Category** | Injection |
| **OWASP** | A03:2021 Injection |
| **Difficulty** | Medium |

**Description:**
Convince the chatbot to give you a coupon of 50% or more. Because apparently a 10% max policy is just a suggestion when you ask nicely enough.

**Root Cause:**
Intentional injection flaw in implementation (key: `chatbotGreedyInjectionChallenge`)

**Affected Files:**
- `routes/chat.ts`

**Entry Points:**
- API/UI refs in: routes/chat.ts

**Impact:**
Enables greedy chatbot manipulation attack scenario

**Remediation Strategy:**
Secure injection per OWASP guidelines

**Files to Modify:**
- `routes/chat.ts`

**Validation Steps:**
Confirm exploit for Greedy Chatbot Manipulation no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### AI Debugging
<a id="aidebuggingchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `aiDebuggingChallenge` |
| **Category** | Broken Access Control |
| **OWASP** | A01:2021 Broken Access Control |
| **Difficulty** | Easy |

**Description:**
Reveal some behind-the-scenes information on the chatbot as a non-admin user.

**Root Cause:**
Intentional broken access control flaw in implementation (key: `aiDebuggingChallenge`)

**Affected Files:**
- `routes/chat.ts`

**Entry Points:**
- API/UI refs in: routes/chat.ts

**Impact:**
Enables ai debugging attack scenario

**Remediation Strategy:**
Secure broken access control per OWASP guidelines

**Files to Modify:**
- `routes/chat.ts`

**Validation Steps:**
Confirm exploit for AI Debugging no longer works; run npm test

**Cross-Impact Risk:**
Review related features before deploying

---
### System Prompt Extraction
<a id="systempromptextractionchallenge"></a>

| Field | Value |
|-------|-------|
| **Challenge Key** | `systemPromptExtractionChallenge` |
| **Category** | Injection |
| **OWASP** | LLM07:2025 System Prompt Leakage |
| **CWE** | CWE-200 |
| **Difficulty** | Medium |

**Description:**
Extract the chatbot's system prompt using prompt injection, then submit your findings (including any confidential sections) via the <a href="/#/complain">Customer Complaint form</a>.

**Root Cause:**
Chatbot reveals system prompt via crafted queries

**Affected Files:**
- `routes/chat.ts`

**Entry Points:**
- POST /rest/chatbot/respond

**Impact:**
Confidential prompt disclosure

**Remediation Strategy:**
Filter sensitive prompt sections from output

**Files to Modify:**
- `routes/chat.ts`

**Validation Steps:**
System prompt not extractable

**Cross-Impact Risk:**
Chatbot responses

---

## Master Checklist

| # | Challenge | Category | Difficulty | Primary Fix Location |
|---|-----------|----------|------------|---------------------|
| 1 | Password Hash Leak | Sensitive Data Exposure | Easy | `routes/currentUser.ts` |
| 2 | API-only XSS | XSS | Medium | `routes/product.ts` |
| 3 | Access Log | Observability Failures | Medium | `server.ts` |
| 4 | Admin Registration | Improper Input Validation | Easy | `routes/user.ts` |
| 5 | Admin Section | Broken Access Control | Easy | `frontend/src/app/app.routing.ts` |
| 6 | Arbitrary File Write | Vulnerable Components | Hard | `routes/fileUpload.ts` |
| 7 | Bjoern's Favorite Pet | Broken Authentication | Medium | `TBD` |
| 8 | Blockchain Hype | Security through Obscurity | Hard | `TBD` |
| 9 | NFT Takeover | Sensitive Data Exposure | Easy | `routes/checkKeys.ts` |
| 10 | Mint the Honey Pot | Improper Input Validation | Medium | `TBD` |
| 11 | Wallet Depletion | Miscellaneous | Hard | `TBD` |
| 12 | Web3 Sandbox | Broken Access Control | Easy | `frontend/src/app/app.routing.ts` |
| 13 | Blocked RCE DoS | Insecure Deserialization | Hard | `TBD` |
| 14 | CAPTCHA Bypass | Broken Anti Automation | Medium | `TBD` |
| 15 | Change Bender's Password | Broken Authentication | Hard | `TBD` |
| 16 | Christmas Special | Injection | Medium | `TBD` |
| 17 | CSP Bypass | XSS | Medium | `TBD` |
| 18 | Client-side XSS Protection | XSS | Medium | `TBD` |
| 19 | Confidential Document | Sensitive Data Exposure | Easy | `routes/fileServer.ts` |
| 20 | DOM XSS | XSS | Easy | `frontend/src/app/search-result/search-result.component.ts` |
| 21 | Database Schema | Injection | Medium | `routes/search.ts` |
| 22 | Deprecated Interface | Security Misconfiguration | Easy | `TBD` |
| 23 | Easter Egg | Broken Access Control | Medium | `TBD` |
| 24 | Email Leak | Sensitive Data Exposure | Hard | `TBD` |
| 25 | Empty User Registration | Improper Input Validation | Easy | `TBD` |
| 26 | Ephemeral Accountant | Injection | Medium | `TBD` |
| 27 | Error Handling | Security Misconfiguration | Easy | `TBD` |
| 28 | Expired Coupon | Improper Input Validation | Medium | `TBD` |
| 29 | Extra Language | Broken Anti Automation | Hard | `TBD` |
| 30 | Five-Star Feedback | Broken Access Control | Easy | `TBD` |
| 31 | Forged Coupon | Cryptographic Issues | Hard | `lib/insecurity.ts` |
| 32 | Forged Feedback | Broken Access Control | Medium | `routes/feedback.ts` |
| 33 | Forged Review | Broken Access Control | Medium | `routes/productReviews.ts` |
| 34 | Forged Signed JWT | Vulnerable Components | Hard | `lib/insecurity.ts` |
| 35 | Forgotten Developer Backup | Sensitive Data Exposure | Medium | `TBD` |
| 36 | Forgotten Sales Backup | Sensitive Data Exposure | Medium | `TBD` |
| 37 | Frontend Typosquatting | Vulnerable Components | Hard | `TBD` |
| 38 | GDPR Data Erasure | Broken Authentication | Medium | `TBD` |
| 39 | GDPR Data Theft | Sensitive Data Exposure | Medium | `TBD` |
| 40 | HTTP-Header XSS | XSS | Medium | `TBD` |
| 41 | Imaginary Challenge | Cryptographic Issues | Hard | `TBD` |
| 42 | Leaked Access Logs | Observability Failures | Hard | `TBD` |
| 43 | Leaked Unsafe Product | Sensitive Data Exposure | Medium | `TBD` |
| 44 | Legacy Typosquatting | Vulnerable Components | Medium | `TBD` |
| 45 | Login Admin | Injection | Easy | `routes/login.ts` |
| 46 | Login Amy | Sensitive Data Exposure | Medium | `TBD` |
| 47 | Login Bender | Injection | Easy | `routes/login.ts` |
| 48 | Login Bjoern | Broken Authentication | Medium | `TBD` |
| 49 | Login Jim | Injection | Easy | `routes/login.ts` |
| 50 | Login MC SafeSearch | Sensitive Data Exposure | Easy | `TBD` |
| 51 | Login Support Team | Security Misconfiguration | Hard | `TBD` |
| 52 | Manipulate Basket | Broken Access Control | Medium | `routes/basketItems.ts` |
| 53 | Misplaced Signature File | Observability Failures | Medium | `TBD` |
| 54 | Multiple Likes | Broken Anti Automation | Hard | `TBD` |
| 55 | Nested Easter Egg | Cryptographic Issues | Medium | `TBD` |
| 56 | NoSQL DoS | Injection | Medium | `routes/order.ts` |
| 57 | NoSQL Exfiltration | Injection | Hard | `routes/orderHistory.ts` |
| 58 | NoSQL Manipulation | Injection | Medium | `routes/productReviews.ts` |
| 59 | Outdated Allowlist | Unvalidated Redirects | Easy | `TBD` |
| 60 | Password Strength | Broken Authentication | Easy | `data/static/users.yml` |
| 61 | Payback Time | Improper Input Validation | Medium | `TBD` |
| 62 | Premium Paywall | Cryptographic Issues | Hard | `TBD` |
| 63 | Privacy Policy | Miscellaneous | Easy | `TBD` |
| 64 | Privacy Policy Inspection | Security through Obscurity | Medium | `TBD` |
| 65 | Product Tampering | Broken Access Control | Medium | `TBD` |
| 66 | Reflected XSS | XSS | Easy | `frontend/src/app/track-result/track-result.component.ts` |
| 67 | Repetitive Registration | Improper Input Validation | Easy | `TBD` |
| 68 | Reset Bender's Password | Broken Authentication | Medium | `TBD` |
| 69 | Reset Bjoern's Password | Broken Authentication | Hard | `TBD` |
| 70 | Reset Jim's Password | Broken Authentication | Medium | `TBD` |
| 71 | Reset Morty's Password | Broken Anti Automation | Hard | `TBD` |
| 72 | Retrieve Blueprint | Sensitive Data Exposure | Hard | `TBD` |
| 73 | SSRF | Broken Access Control | Hard | `routes/profileImageUrlUpload.ts` |
| 74 | SSTi | Injection | Hard | `routes/updateUserProfile.ts` |
| 75 | Score Board | Miscellaneous | Easy | `frontend/src/app/app.routing.ts` |
| 76 | Security Policy | Miscellaneous | Easy | `TBD` |
| 77 | Server-side XSS Protection | XSS | Medium | `TBD` |
| 78 | Steganography | Security through Obscurity | Medium | `TBD` |
| 79 | Successful RCE DoS | Insecure Deserialization | Hard | `TBD` |
| 80 | Supply Chain Attack | Vulnerable Components | Hard | `TBD` |
| 81 | Two Factor Authentication | Broken Authentication | Hard | `TBD` |
| 82 | Unsigned JWT | Vulnerable Components | Medium | `lib/insecurity.ts` |
| 83 | Upload Size | Improper Input Validation | Medium | `TBD` |
| 84 | Upload Type | Improper Input Validation | Medium | `TBD` |
| 85 | User Credentials | Injection | Medium | `routes/search.ts` |
| 86 | Video XSS | XSS | Hard | `TBD` |
| 87 | View Basket | Broken Access Control | Easy | `routes/basket.ts` |
| 88 | Vulnerable Library | Vulnerable Components | Medium | `TBD` |
| 89 | Weird Crypto | Cryptographic Issues | Easy | `TBD` |
| 90 | Allowlist Bypass | Unvalidated Redirects | Medium | `routes/redirect.ts` |
| 91 | XXE Data Access | XXE | Medium | `routes/b2bOrder.ts` |
| 92 | XXE DoS | XXE | Hard | `routes/b2bOrder.ts` |
| 93 | Memory Bomb | Insecure Deserialization | Hard | `routes/fileUpload.ts` |
| 94 | Zero Stars | Improper Input Validation | Easy | `TBD` |
| 95 | Missing Encoding | Improper Input Validation | Easy | `TBD` |
| 96 | Cross-Site Imaging | Security Misconfiguration | Hard | `TBD` |
| 97 | Exposed Metrics | Observability Failures | Easy | `server.ts` |
| 98 | Deluxe Fraud | Improper Input Validation | Medium | `TBD` |
| 99 | CSRF | Broken Access Control | Medium | `routes/updateUserProfile.ts` |
| 100 | Bonus Payload | XSS | Easy | `TBD` |
| 101 | Reset Uvogin's Password | Sensitive Data Exposure | Medium | `TBD` |
| 102 | Meta Geo Stalking | Sensitive Data Exposure | Easy | `TBD` |
| 103 | Visual Geo Stalking | Sensitive Data Exposure | Easy | `TBD` |
| 104 | Poison Null Byte | Improper Input Validation | Medium | `TBD` |
| 105 | Local File Read | Vulnerable Components | Hard | `TBD` |
| 106 | Mass Dispel | Miscellaneous | Easy | `TBD` |
| 107 | Security Advisory | Miscellaneous | Medium | `TBD` |
| 108 | Exposed Credentials | Sensitive Data Exposure | Easy | `TBD` |
| 109 | Leaked API Key | Sensitive Data Exposure | Hard | `TBD` |
| 110 | Chatbot Prompt Injection | Injection | Medium | `routes/chat.ts` |
| 111 | Greedy Chatbot Manipulation | Injection | Medium | `TBD` |
| 112 | AI Debugging | Broken Access Control | Easy | `TBD` |
| 113 | System Prompt Extraction | Injection | Medium | `routes/chat.ts` |

## Recommended Remediation Order

1. **Authentication & SQLi** — loginAdmin, loginBender, loginJim, weakPassword, registerAdmin
2. **Access Control** — adminSection, basketAccess, forgedFeedback, forgedReview, basketManipulate
3. **Data Exposure** — passwordHashLeak, directoryListing, exposedMetrics
4. **XSS** — localXss, reflectedXss, persisted variants, restfulXss
5. **Injection Advanced** — unionSql, dbSchema, noSql family, SSTI, XXE
6. **Crypto/JWT** — jwtUnsigned, jwtForged, forgedCoupon, weirdCrypto
7. **Advanced** — SSRF, RCE, fileWrite, Web3, LLM injection

## Challenge Dependencies

- `loginAdminChallenge` → `weakPasswordChallenge`
- `nullByteChallenge` → `easterEggLevelOneChallenge`, `forgottenDevBackupChallenge`
- `deprecatedInterfaceChallenge` → `uploadTypeChallenge`, `xxeFileDisclosureChallenge`
- `uploadSizeChallenge` → `uploadTypeChallenge`
- `uploadTypeChallenge` → `xxeFileDisclosureChallenge`
- `localXssChallenge` → `xssBonusChallenge`
- `fileWriteChallenge` → `videoXssChallenge`