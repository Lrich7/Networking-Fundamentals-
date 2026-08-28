# Lesson 34 — PowerShell Networking Tools

## Learning Objectives

By the end of this lesson, you will be able to:

- Explain and use Get-NetAdapter.
- Explain and use Get-NetIPConfiguration.
- Explain and use Get-NetRoute.
- Explain and use Test-NetConnection.
- Explain and use Resolve-DnsName.
- Explain and use Get-NetTCPConnection.

---

# Troubleshooting Mindset

The goal is not to try commands until something works.

Use a repeatable process:

```text
Identify the symptom
        ↓
Determine the scope
        ↓
Establish a known-good baseline
        ↓
Collect evidence
        ↓
Form a theory
        ↓
Test one theory
        ↓
Correct the root cause
        ↓
Verify
        ↓
Document
```

---

# Core Topics

## Get-Netadapter

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Get-Netipconfiguration

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Get-Netroute

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Test-Netconnection

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Resolve-Dnsname

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Get-Nettcpconnection

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


# Work from Simple to Specific

A useful network sequence is:

```text
Physical link
    ↓
Local adapter
    ↓
IP configuration
    ↓
Local subnet
    ↓
Default gateway
    ↓
Routing path
    ↓
DNS
    ↓
Transport port
    ↓
Application/service
```

Not every incident follows this exact order, but it prevents random changes.

---

# Scope Is a Major Clue

Always ask:

```text
One device?
Several devices?
One VLAN?
One subnet?
One switch?
One site?
One service?
Everyone?
```

The larger the scope, the more likely the shared infrastructure deserves attention.

---

# Documentation Standard

For each issue, capture:

```text
Reported symptom
Affected scope
Expected behavior
Evidence collected
Commands/tools used
Root cause
Change made
Verification
Prevention/follow-up
```

---

# Knowledge Check

1. Why should you determine scope before making changes?
2. What is the value of a known-good baseline?
3. Why should you test one theory at a time?
4. Why can ping alone be insufficient?
5. What should be documented after a repair?
6. Why should required business functionality be verified after a fix?

---

# Hands-On Lab

➡️ **[Lab 34 — PowerShell Networking Tools](../labs/lab-34-powershell-networking-tools.md)**
