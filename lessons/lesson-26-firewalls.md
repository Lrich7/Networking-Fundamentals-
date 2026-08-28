# Lesson 26 — Firewalls

## Learning Objectives

By the end of this lesson, you will be able to:

- Explain and apply firewall purpose and traffic policy.
- Explain and apply stateful vs. stateless filtering.
- Explain and apply inbound and outbound rules.
- Explain and apply host vs. network firewalls.
- Explain and apply zones and segmentation.
- Explain and apply allow/deny logic.
- Explain and apply firewall troubleshooting.

---

# Why This Matters

Network security is not one product or one setting. It is a layered process of reducing risk while still allowing the business to operate.

A useful mindset is:

```text
Identify what must be protected
        ↓
Understand the threat
        ↓
Reduce exposure
        ↓
Control access
        ↓
Monitor activity
        ↓
Respond and improve
```

---

# Core Concepts

## Firewall Purpose And Traffic Policy

Firewall purpose and traffic policy is an important part of designing, operating, and troubleshooting secure networks.

When evaluating it, ask:

```text
What are we protecting?
Who or what needs access?
What is the minimum access required?
How can the control fail?
How will we verify and monitor it?
```

## Stateful Vs. Stateless Filtering

Stateful vs. stateless filtering is an important part of designing, operating, and troubleshooting secure networks.

When evaluating it, ask:

```text
What are we protecting?
Who or what needs access?
What is the minimum access required?
How can the control fail?
How will we verify and monitor it?
```

## Inbound And Outbound Rules

Inbound and outbound rules is an important part of designing, operating, and troubleshooting secure networks.

When evaluating it, ask:

```text
What are we protecting?
Who or what needs access?
What is the minimum access required?
How can the control fail?
How will we verify and monitor it?
```

## Host Vs. Network Firewalls

Host vs. network firewalls is an important part of designing, operating, and troubleshooting secure networks.

When evaluating it, ask:

```text
What are we protecting?
Who or what needs access?
What is the minimum access required?
How can the control fail?
How will we verify and monitor it?
```

## Zones And Segmentation

Zones and segmentation is an important part of designing, operating, and troubleshooting secure networks.

When evaluating it, ask:

```text
What are we protecting?
Who or what needs access?
What is the minimum access required?
How can the control fail?
How will we verify and monitor it?
```

## Allow/Deny Logic

Allow/deny logic is an important part of designing, operating, and troubleshooting secure networks.

When evaluating it, ask:

```text
What are we protecting?
Who or what needs access?
What is the minimum access required?
How can the control fail?
How will we verify and monitor it?
```

## Firewall Troubleshooting

Firewall troubleshooting is an important part of designing, operating, and troubleshooting secure networks.

When evaluating it, ask:

```text
What are we protecting?
Who or what needs access?
What is the minimum access required?
How can the control fail?
How will we verify and monitor it?
```

# Security and Troubleshooting

Security controls can intentionally block traffic.

When connectivity fails, do not immediately disable security.

Use:

```text
Confirm scope
    ↓
Verify addressing/routing
    ↓
Identify required protocol and port
    ↓
Check security policy
    ↓
Review logs/evidence
    ↓
Make the smallest safe correction
    ↓
Verify
```

---

# Key Principle

> A secure network should allow required business traffic while denying or reducing unnecessary access.

Avoid broad rules such as "allow everything" simply to make a test pass.

---

# Knowledge Check

1. What security goal or control is being discussed in this lesson?
2. How can this control reduce network risk?
3. How could a misconfiguration affect legitimate traffic?
4. What evidence should you gather before changing a security setting?
5. Why is least privilege important?
6. Why should security changes be documented?

---

# Lesson Summary

Security works best as layers:

```text
People
  ↓
Endpoints
  ↓
Network access
  ↓
Segmentation
  ↓
Traffic controls
  ↓
Secure services
  ↓
Monitoring
  ↓
Response
```

---

# Hands-On Lab

➡️ **[Lab 26 — Firewalls](../labs/lab-26-firewalls.md)**