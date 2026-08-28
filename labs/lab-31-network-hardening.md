# Lab 31 — Network Hardening

## Lab Objective

Apply the concepts from Lesson 31 in a safe, isolated training environment and practice security-focused troubleshooting.

---

# Safety Rules

- Use only systems and networks you own or are explicitly authorized to test.
- Keep Packet Tracer exercises inside the simulated lab.
- Do not scan, attack, intercept, or bypass controls on real networks.
- Do not upload company IP addresses, configurations, packet captures, credentials, or security details to a public repository.
- Prefer read-only inspection on real Windows systems.

---

# Part 1 — Establish the Baseline

Before changing anything, document:

```text
Topology
IP addressing
VLANs/subnets
Expected communication
Relevant services/ports
Current security control
```

Verify the network works as expected.

---

# Part 2 — Hands-On Exercise

Take the Section 5 business topology and harden it. Disable unused switch ports in Packet Tracer, document secure management recommendations, review VLAN separation, identify required vs. unnecessary services, create a logging/monitoring plan, and save a known-good configuration baseline. Verify that required business traffic still works.

---

# Part 3 — Verify the Control

Record:

```text
Traffic that should work:
Traffic that should fail:
Command/tool used:
Observed result:
```

A security control is not validated until both permitted and restricted behavior are tested.

---

# Part 4 — Create a Safe Misconfiguration

In Packet Tracer or another isolated lab, create one configuration error related to this lesson.

Examples:

```text
Required traffic accidentally blocked
Wrong network/VLAN referenced
Incorrect rule placement
Missing authentication/configuration
Overly broad permission
```

Do not create real-world offensive traffic.

---

# Part 5 — Troubleshoot

Use:

```text
1. Define the symptom
2. Determine the scope
3. Verify Layers 1–3
4. Identify required service/port
5. Inspect the relevant security control
6. Review available evidence/logs
7. Correct only the root cause
8. Retest allowed and denied traffic
```

---

# Part 6 — Ticket Documentation

Complete:

```text
Issue:
Affected systems:
Expected behavior:
Actual behavior:
Evidence:
Security control involved:
Root cause:
Correction:
Verification:
Prevention:
```

---

# Knowledge Check

1. What security risk does this lesson's control address?
2. How did you prove permitted traffic still worked?
3. How did you prove restricted traffic was blocked?
4. What symptom did the misconfiguration create?
5. Why is disabling a security control a poor default troubleshooting method?

---

# Challenge

Improve the lab design using **least privilege**.

Your final design should permit only what is required for the scenario and should include a short explanation for every security decision.

---

# Lab Completion Checklist

- [ ] Established baseline
- [ ] Completed hands-on exercise
- [ ] Verified required traffic
- [ ] Verified restricted traffic
- [ ] Created safe lab fault
- [ ] Troubleshot systematically
- [ ] Documented ticket
- [ ] Applied least privilege
- [ ] Completed knowledge check
- [ ] Completed challenge

---

# Lab Complete

You have completed **Lab 31 — Network Hardening**.

# 🛠️ Project 06 — Secure the Network

You have completed **Section 6 — Network Security**.

Now apply the security concepts from Lessons 25–31.

➡️ **[Project 06 — Secure the Network](../projects/project-06-secure-the-network.md)**

➡️ **[Begin Project 06 — Secure the Network](../projects/project-06-secure-the-network.md)**

