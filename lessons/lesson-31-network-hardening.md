# Lesson 31 — Network Hardening

## Learning Objectives

By the end of this lesson, you will be able to:

- Explain and apply secure configuration baselines.
- Explain and apply patching and firmware.
- Explain and apply disable unused services and ports.
- Explain and apply management-plane security.
- Explain and apply network segmentation.
- Explain and apply logging and monitoring.
- Explain and apply configuration backups and documentation.

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

## Secure Configuration Baselines

Secure configuration baselines is an important part of designing, operating, and troubleshooting secure networks.

When evaluating it, ask:

```text
What are we protecting?
Who or what needs access?
What is the minimum access required?
How can the control fail?
How will we verify and monitor it?
```

## Patching And Firmware

Patching and firmware is an important part of designing, operating, and troubleshooting secure networks.

When evaluating it, ask:

```text
What are we protecting?
Who or what needs access?
What is the minimum access required?
How can the control fail?
How will we verify and monitor it?
```

## Disable Unused Services And Ports

Disable unused services and ports is an important part of designing, operating, and troubleshooting secure networks.

When evaluating it, ask:

```text
What are we protecting?
Who or what needs access?
What is the minimum access required?
How can the control fail?
How will we verify and monitor it?
```

## Management-Plane Security

Management-plane security is an important part of designing, operating, and troubleshooting secure networks.

When evaluating it, ask:

```text
What are we protecting?
Who or what needs access?
What is the minimum access required?
How can the control fail?
How will we verify and monitor it?
```

## Network Segmentation

Network segmentation is an important part of designing, operating, and troubleshooting secure networks.

When evaluating it, ask:

```text
What are we protecting?
Who or what needs access?
What is the minimum access required?
How can the control fail?
How will we verify and monitor it?
```

## Logging And Monitoring

Logging and monitoring is an important part of designing, operating, and troubleshooting secure networks.

When evaluating it, ask:

```text
What are we protecting?
Who or what needs access?
What is the minimum access required?
How can the control fail?
How will we verify and monitor it?
```

## Configuration Backups And Documentation

Configuration backups and documentation is an important part of designing, operating, and troubleshooting secure networks.

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

➡️ **[Lab 31 — Network Hardening](../labs/lab-31-network-hardening.md)**