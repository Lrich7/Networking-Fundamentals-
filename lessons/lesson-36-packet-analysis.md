# Lesson 36 — Packet Analysis

## Learning Objectives

By the end of this lesson, you will be able to:

- Explain and use establishing a normal traffic baseline.
- Explain and use reading Ethernet and IP headers.
- Explain and use analyzing TCP handshakes and flags.
- Explain and use analyzing DNS queries and responses.
- Explain and use identifying retransmissions and failures.
- Explain and use correlating packets with symptoms.

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

## Establishing A Normal Traffic Baseline

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Reading Ethernet And Ip Headers

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Analyzing Tcp Handshakes And Flags

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Analyzing Dns Queries And Responses

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Identifying Retransmissions And Failures

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Correlating Packets With Symptoms

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

➡️ **[Lab 36 — Packet Analysis](../labs/lab-36-packet-analysis.md)**
