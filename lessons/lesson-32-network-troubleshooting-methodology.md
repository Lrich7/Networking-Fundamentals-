# Lesson 32 — Network Troubleshooting Methodology

## Learning Objectives

By the end of this lesson, you will be able to:

- Explain and use define the problem and determine scope.
- Explain and use establish a theory of probable cause.
- Explain and use test the theory with evidence.
- Explain and use create and implement a safe action plan.
- Explain and use verify full functionality.
- Explain and use document findings and preventive actions.

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

## Define The Problem And Determine Scope

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Establish A Theory Of Probable Cause

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Test The Theory With Evidence

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Create And Implement A Safe Action Plan

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Verify Full Functionality

Use this concept as part of an evidence-driven troubleshooting workflow. Record what you expected, what you observed, and what the result tells you about the next test.


## Document Findings And Preventive Actions

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

➡️ **[Lab 32 — Network Troubleshooting Methodology](../labs/lab-32-network-troubleshooting-methodology.md)**
