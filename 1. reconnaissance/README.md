# M1 | Reconnaissance and Application Mapping

This folder contains the evidence collected during the initial black-box reconnaissance and application-mapping phase of the NetworkWalks Week 4 exercise.

**Target:** Mediroza General Hospital training target  
**Environment:** Kali Linux VM in VMware (NAT)  
**Primary tools:** WHOIS, WhatWeb, nslookup, cURL, Wafw00f, DNSRecon and Burp Suite

> **Evidence handling:** Screenshots 8–11 relate to authentication testing and access to restricted portal content. Review and redact them before public sharing. Do not publish session cookies, authentication material or patient-style record details.

## 1. Objectives

- Establish basic domain-registration and DNS context.
- Identify observable web-server and application technologies.
- Review HTTP response behaviour and available security headers.
- Observe whether automated requests receive consistent responses.
- Map visible application routes using Burp Suite.
- Document the patient login workflow and the observed authentication weakness.

## 2. Reconnaissance activities

| Evidence | Screenshot | Activity | Recorded observation |
|---|---|---|---|
| E-01 | 1. recon whois.png | WHOIS lookup | Registrar and domain-registration context were recorded; registrant details were privacy-protected |
| E-02 | 2. recon whatweb.png | WhatWeb fingerprinting | LiteSpeed was identified; one HTTPS fingerprinting request received a 403 response |
| E-03 | 3. recon nslookup.png | DNS lookup | A, MX, TXT and NS information was reviewed |
| E-04 | 4. recon curl -I -L.png | HTTP response headers | HTTP redirected to HTTPS; the HTTPS response returned successfully and disclosed LiteSpeed |
| E-05 | 5. recon wafw00f.png | WAF identification attempt | Results varied between runs; the result was treated as inconclusive rather than proof of effective protection |
| E-06 | 6. recon dnsrecon -d.png | DNS enumeration | Additional DNS records, including mail and service-discovery records, were observed |

### Selected reconnaissance screenshots

The following screenshots are the basic reconnaissance evidence. Check each image for sensitive information before sharing it outside the training group.

![WHOIS lookup](1.%20recon%20whois.png)

![WhatWeb fingerprinting](2.%20recon%20whatweb.png)

![nslookup results](3.%20recon%20nslookup.png)

![cURL response headers](4.%20recon%20curl%20-I%20-L.png)

![Wafw00f results](5.%20recon%20wafw00f.png)

![DNSRecon results](6.%20recon%20dnsrecon%20-d.png)

## 3. Interpretation

The recorded responses identified LiteSpeed as the web server. The HTTP endpoint redirected to HTTPS, and the captured HTTPS response returned a successful status. The captured headers did not include several commonly recommended browser security headers. This is documented as a hardening observation in the main M4 report, not as proof of a directly exploitable vulnerability.

WhatWeb and Wafw00f did not produce fully consistent results. A 403 response from one automated fingerprinting request and differing WAF identification results suggest that request handling may be filtered or variable. The available evidence is not sufficient to claim that the WAF blocks all automated testing or that it provides effective protection.

DNS records also referenced mail and hosting-related services. These were treated as contextual information only. Third-party mail and hosting infrastructure were outside the assigned testing scope and were not tested.

## 4. Burp Suite application mapping

Burp Suite was used to browse the assigned web application and review the site map. The evidence records the discovery of separate patient and staff login routes and a custom CMS identifier in the page response.

| Evidence | Screenshot | Purpose |
|---|---|---|
| E-07 | 7. recon burpsuite sitemap.png | Application route and site-map review |
| E-08 | 8. recon burpsuite phplogin to repeater.png | Captured patient-login request for controlled inspection |
| E-09 | 9. recon burpsuite sql injection.png | Database error observed during input testing |
| E-10 | 10. recon sql injection live portal.png | Authentication-bypass response and portal redirect |
| E-11 | 11. recon live site accessed records.png | Subsequent portal access recorded in the exercise |

The login workflow returned a database syntax error when unexpected input was submitted. A subsequent controlled test returned an HTTP 302 redirect to the patient portal without a valid password. This behaviour was recorded as SQL injection leading to authentication bypass.

The exact request manipulation and any authentication material are intentionally not reproduced in this public README. Refer to the main M4 report for the finding, impact and remediation.

## 5. Key outcome

The reconnaissance phase established the observable web stack, identified application routes and provided the context for the authentication testing documented in finding F-01 of the main report.

## 6. Scope reminder

Only the assigned training target was in scope. DNS references to mail providers, control-panel services and other third-party infrastructure were not permission to test those systems.

Return to the [main M4 report](../README.md).
