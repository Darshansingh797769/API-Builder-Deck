# NIUM API Recipe Builder - Quick Reference Card

## 📊 30-Second Overview

**What:** An automated Excel tool to identify APIs you need based on your client type and services.

**When to Use:** At the start of any NIUM integration project.

**Output:** A personalized API checklist with 44+ APIs, color-coded by requirement level.

---

## 🚀 3-Step Quick Start

### Step 1️⃣: Open Dashboard
- Start at **Dashboard** sheet
- See all available APIs and statistics
- Navigate to next steps

### Step 2️⃣: Build Recipe  
- Go to **Service Selector** sheet
- Select your **Client Type** (dropdown)
- Check the **Services** you need
- The tool calculates your API list

### Step 3️⃣: Review APIs
- Go to **Your Recipe** sheet
- See all APIs for your selections
- 🔴 RED = Must implement
- 🟡 YELLOW = Implement if scenario applies
- 🟢 GREEN = Optional enhancements

---

## 📋 Client Types at a Glance

| Client Type | Best For | Key Services |
|---|---|---|
| **Bank - COBO** | Crypto custody | Payout, FX, Verify |
| **Bank - POBO** | Beneficiary payouts | Payout, FX, Verify |
| **Non-Bank FI** | Money transfer business | Payin + Payout + FX |
| **NonFI Direct** | Enterprise payments | All except Cards (full) |
| **Platform** | Neobank/Fintech | All 44 APIs available |

---

## 🎯 Service Categories (What They Do)

| Service | # APIs | What It Does |
|---|---|---|
| 🔐 **Customer Onboarding** | 4 | Register & verify customers |
| 💰 **Wallet/Payin** | 6 | Receive payments via Virtual Accounts |
| 💸 **Payout** | 13 | Send money globally to beneficiaries |
| 🎴 **Card Management** | 11 | Issue & manage payment cards |
| 🌍 **Foreign Exchange** | 7 | Convert currencies & lock rates |
| ✅ **Verify** | 3 | Account verification |

---

## ⏱️ Implementation Time Estimates

| Scenario | APIs | Timeline |
|---|---|---|
| **Collections Only** | 10 | 1-2 weeks |
| **Payouts Only** | 17 | 3-4 weeks |
| **Collections + Payouts** | 19 | 4-6 weeks |
| **Cards (Platform)** | 11 | 4-6 weeks |
| **Full Stack** | 44 | 18+ weeks |

---

## 🎨 Color Legend

```
🔴 MANDATORY (RED)      = Must implement | Critical for use case
🟡 CONDITIONAL (YELLOW) = Required if scenario applies | Check notes
🟢 OPTIONAL (GREEN)     = Nice-to-have | Adds functionality
```

---

## 📊 API Statistics

| Requirement | Count | % |
|---|---|---|
| Mandatory | 19 | 43% |
| Conditional | 5 | 11% |
| Optional | 20 | 46% |
| **Total** | **44** | **100%** |

---

## 🔑 Key Workflows

### Workflow A: Payout Provider
```
Customer Onboarding (4) 
    ↓
Payout Services (13)
    ↓
FX Services (optional, 7)
────────────────────────
Total: 17-24 APIs
Timeline: 4-6 weeks
```

### Workflow B: Collections Provider
```
Customer Onboarding (4)
    ↓
Wallet Management (6)
    ↓
Verify (optional, 3)
────────────────────────
Total: 10-13 APIs
Timeline: 2-4 weeks
```

### Workflow C: Full Platform
```
Customer Onboarding (4)
    ↓
Wallet + Payin (6)
    ↓
Card Management (11)
    ↓
Payout (13)
    ↓
FX + Verify (10)
────────────────────────
Total: 44 APIs
Timeline: 18+ weeks
```

---

## 🛠️ Common Implementations at a Glance

### Fintech Platform
- ✓ All 44 APIs
- ✓ Full customer lifecycle
- ✓ Cards + spend management
- ✓ Multi-corridor payouts
- ✓ FX trading

**Mandatory Count:** 19 APIs  
**Implementation Time:** 18-24 weeks

---

### Remittance Company
- ✓ Customer Onboarding (4)
- ✓ Payout (13)
- ✓ FX Services (7, optional)
- ✗ Cards
- ✗ Payin

**Mandatory Count:** 7 APIs  
**Implementation Time:** 4-6 weeks

---

### Enterprise with Collections
- ✓ Customer Onboarding (4)
- ✓ Wallet Management (6)
- ✗ Payouts
- ✗ Cards
- ✗ FX

**Mandatory Count:** 6 APIs  
**Implementation Time:** 2-3 weeks

---

## 📁 Workbook Structure

| Sheet | Purpose |
|---|---|
| **Dashboard** | Overview & navigation (START HERE) |
| **Service Selector** | Select client type + services (RECOMMENDED) |
| **Your Recipe** | View personalized API list |
| **Classic Recipe Builder** | Alternative: Select type + use case |
| **API Database** | Complete reference of 44+ APIs |
| **Compatibility Matrix** | Which services work together |
| **Client & Use Case Reference** | Detailed descriptions |
| **Quick Start Guide** | How to use this workbook |
| **Implementation Guide** | Detailed API information |
| **Filtered Recipe Results** | Dynamic API filtering |

---

## ⚡ Pro Tips

### Tip 1: Start with Mandatory APIs
- All RED items must be implemented
- They form the foundation
- Build optional features after

### Tip 2: Plan Webhook Infrastructure
- Many mandatory APIs need webhooks
- Set up early: monitoring, retry logic, security
- Common webhooks: Customer Status, Wallet Funding, Transaction Status

### Tip 3: Use the Compatibility Matrix
- Verify your client type × services work together
- Platform Client can use everything
- Others have limitations

### Tip 4: Build Phased Implementation Plan
- Phase 1: Core services (Onboarding + Payin OR Payout)
- Phase 2: Additional services (Cards, FX)
- Phase 3: Enhancements (Verify, advanced features)

### Tip 5: Reference the Notes Column
- Each API has implementation notes
- Check for version recommendations
- Look for dependency warnings

---

## 🔗 Dependency Chain

```
FOUNDATION
  └─ Customer Onboarding (4 APIs)
     
PAYMENT COLLECTION
  └─ Wallet Management (6 APIs)
     └─ Requires: Customer Onboarding
     
PAYMENT SENDING
  └─ Payout (13 APIs)
     └─ Requires: Customer Onboarding
     └─ Optional: FX Services
     
CARDS & SPEND
  └─ Card Management (11 APIs)
     └─ Requires: Customer Onboarding
     └─ Platform Client only
     
CURRENCY CONVERSION
  └─ Foreign Exchange (7 APIs)
     └─ Requires: Wallet/Payout set up
     
VERIFICATION
  └─ Verify Services (3 APIs)
     └─ Optional add-on for any setup
```

---

## ❓ Quick Troubleshooting

| Problem | Solution |
|---|---|
| Can't find my use case | Check Compatibility Matrix - your client type may not support it |
| Too many mandatory APIs | Your client type is more complex - follow the dependency chain |
| Don't know where to start | Begin with Customer Onboarding, then Payin OR Payout |
| Need phased approach | Implement in phases: Core → Cards → FX → Verify |
| Webhook infrastructure needed | Plan this early - 80% of mandatory APIs need webhooks |

---

## 📞 What's Next After Recipe Building?

1. **Week 1:** Review recipe with architecture team
2. **Week 2:** Plan webhook infrastructure
3. **Week 3:** Set up sandbox testing
4. **Week 4:** Detailed API integration planning
5. **Week 5+:** Begin implementation

---

## 📚 Key References

| Resource | Where to Find |
|---|---|
| Full API Docs | playbook.nium.com |
| Sample Flows | gallery.preprod.nium.com |
| Sandbox Credentials | NIUM onboarding team |
| Technical Support | integration@nium.com |

---

## 💡 Remember

- ✓ Start with the Dashboard
- ✓ Use Service Selector for granular control
- ✓ Read the color-coded requirements
- ✓ Check the notes for each API
- ✓ Plan webhook infrastructure early
- ✓ Implement in phases
- ✓ Test in sandbox first

---

**Version:** 2.0  
**Date:** September 2026  
**APIs Included:** 44+  
**Client Types:** 5  
**Use Cases:** 8

---

**Questions? Check the Implementation Guide for detailed information!**
