# Lesson 38 — Troubleshooting DNS and DHCP

## Learning Objectives

By the end of this lesson, you will be able to:

- Explain and use DNS server and record troubleshooting.
- Explain and use testing by IP versus name.
- Explain and use DHCP DORA and lease troubleshooting.
- Explain and use scope exhaustion and bad options.
- Explain and use DHCP relay concepts.
- Explain and use distinguishing DNS, DHCP and routing symptoms.

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

## Dns Server And Record Troubleshooting

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Testing By Ip Versus Name

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Dhcp Dora And Lease Troubleshooting

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Scope Exhaustion And Bad Options

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Dhcp Relay Concepts

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Distinguishing Dns, Dhcp And Routing Symptoms

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

➡️ **[Lab 38 — Troubleshooting DNS and DHCP](../labs/lab-38-troubleshooting-dns-and-dhcp.md)**
