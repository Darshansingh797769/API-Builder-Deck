# NIUM API Recipe Builder - Implementation Guide

## Overview
The **NIUM API Recipe Builder** is an automated Excel workbook designed to help you quickly identify which APIs you need to implement based on your client type and service requirements.

### What You Get
- **44+ APIs** across 6 service categories
- **Automated filtering** based on your selections
- **Color-coded requirements** (Mandatory, Conditional, Optional)
- **Complete implementation guidance** with examples
- **Compatibility matrix** showing service combinations

---

## Table of Contents
1. [Quick Start](#quick-start)
2. [Using the Recipe Builder](#using-the-recipe-builder)
3. [Understanding Your Options](#understanding-your-options)
4. [How to Read Your Recipe](#how-to-read-your-recipe)
5. [API Categories & Services](#api-categories--services)
6. [Implementation Workflows](#implementation-workflows)
7. [Advanced Usage](#advanced-usage)

---

## Quick Start

### 3-Step Process

**Step 1: Open the Dashboard**
- Start at the **Dashboard** sheet when you open the workbook
- Get an overview of available APIs and quick navigation

**Step 2: Build Your Recipe**
- Go to **Service Selector** sheet
- Select your **Client Type** from the dropdown
- Choose the **Services** you need (checkboxes)

**Step 3: Review Your APIs**
- Go to **Your Recipe** sheet
- Review all APIs relevant to your selection
- Start implementation planning

---

## Using the Recipe Builder

### Method 1: Service Selector (Recommended)

**Location:** `Service Selector` sheet

**How it works:**
1. **Select Client Type** (Row 6)
   - Dropdown list of 5 client types
   - Description auto-populates below

2. **Select Services** (Rows 13-18)
   - ☐ Customer Onboarding (4 APIs)
   - ☐ Wallet Management / Payin (6 APIs)
   - ☐ Payout (13 APIs)
   - ☐ Card Management (11 APIs)
   - ☐ Foreign Exchange (7 APIs)
   - ☐ Verify (3 APIs)

3. **View Your Recipe**
   - Go to `Your Recipe` sheet
   - All selected APIs appear with details

**Advantages:**
- ✓ Granular service selection
- ✓ See exactly which services you need
- ✓ Best for planning your implementation

---

### Method 2: Classic Recipe Builder (Alternative)

**Location:** `Classic Recipe Builder` sheet

**How it works:**
1. Select **Client Type** (Row 4)
2. Select **Use Case** (Row 6)
3. All relevant APIs auto-populate below

**Use Cases:**
- Customer Onboarding
- Payin (Payment collection)
- Payout (Money transfers)
- Cards (Card issuance & management)
- Spend Management (Corporate T&E)
- FX (Currency conversion)
- Verify (Account verification)
- Full Stack (Complete solution)

---

## Understanding Your Options

### Client Types (5 Options)

#### 1. **Bank - FI Client (COBO)**
**Model:** Crypto Asset Custodian - Bank holds crypto assets

**Use Cases:**
- Manage customer crypto assets
- Enable payouts to beneficiaries
- Handle FX and conversions

**Key Services:**
- Customer Onboarding ✓
- Payout ✓
- FX ✓
- Verify ✓

**Example:** Bank offering crypto custody services

---

#### 2. **Bank - FI Client (POBO)**
**Model:** Payouts by Operator - Bank enables payouts for customers

**Use Cases:**
- Direct customer payouts
- Beneficiary management
- Compliance handling

**Key Services:**
- Customer Onboarding ✓
- Payout ✓
- FX ✓
- Verify ✓

**Example:** Bank providing remittance services

---

#### 3. **Non-Bank FI Client**
**Model:** Financial Institution without banking license

**Use Cases:**
- Money transfer services
- Collections and payouts
- Multi-currency operations

**Key Services:**
- Customer Onboarding ✓
- Wallet Management / Payin ✓
- Payout ✓
- FX ✓
- Verify ✓

**Example:** Remittance company, MVNO

---

#### 4. **NonFI Direct (Enterprise)**
**Model:** Direct non-financial enterprise client

**Use Cases:**
- Global marketplace payments
- Vendor payouts
- Customer funding
- Compliance management

**Key Services:**
- ALL services available
- Full operational support

**Example:** E-commerce platform, gig economy app

---

#### 5. **Platform Client**
**Model:** Complete integration platform with all NIUM services

**Use Cases:**
- Neobank operations
- Payment aggregation
- Employee cards & T&E
- Multi-currency transfers
- Account verification

**Key Services:**
- ALL 44+ APIs available
- Maximum flexibility

**Example:** Fintech platform, digital bank

---

### Service Categories (6 Options)

#### 🔐 Customer Onboarding (4 APIs)
**What:** Manage the customer lifecycle from registration to activation

**APIs:**
1. **Create Customer v5** (Mandatory)
   - Register corporate or individual customer
   - Full KYC integration

2. **Get Customer v5** (Optional)
   - Retrieve customer details
   - Update customer info

3. **Public Corporate Details** (Conditional)
   - Fetch company info using Business ID
   - For corporate customers only

4. **Customer Status Webhook** (Mandatory)
   - Real-time onboarding status updates
   - Required for async operations

**Typical Flow:**
```
Register Customer → Submit KYC → Verify → Customer Status Webhook → Activate Account
```

**Best For:** All client types that need to onboard customers

---

#### 💰 Wallet Management / Payin (6 APIs)
**What:** Receive payments from customers via Virtual Accounts

**APIs:**
1. **Assign Payment ID** (Mandatory)
   - Generate Virtual Account Number (VAN)
   - Async process

2. **Virtual Account Assigned Webhook** (Mandatory)
   - Confirmation when VAN is created
   - Contains bank details

3. **VA Assignment Failure Webhook** (Mandatory)
   - Error notification if VAN fails
   - Includes error details

4. **Virtual Account Details V2** (Mandatory)
   - Retrieve full VA information
   - Includes PayID, routing details

5. **Manage Virtual Account Tags** (Optional)
   - Organize VAs with custom tags
   - For better tracking

6. **Wallet Funding Webhook** (Mandatory)
   - Notification when funds arrive
   - Real-time balance update

**Typical Flow:**
```
Assign Payment ID → VAN Created → Share with Customer → Customer Sends Funds
   → Wallet Funding Webhook → Confirm Receipt
```

**Best For:** Direct Clients, Platform Clients, Non-Bank FI Clients

---

#### 💸 Payout (13 APIs)
**What:** Send money globally to beneficiaries with compliance handling

**Core APIs:**
1. **Transfer Money** (Mandatory)
   - Initiate transfer to beneficiary
   - Core operation

2. **Fetch Purpose Code** (Mandatory)
   - Get purpose code for transfer
   - Regulatory requirement

3. **Fetch Remittance Life Cycle Status** (Mandatory)
   - Track transfer status
   - Real-time updates

4. **Transaction Compliance Status Callback** (Mandatory)
   - Handle compliance screening hits
   - RFI (Request for Information) trigger

5. **Beneficiary Validation Schema v2** (Optional)
   - Get required fields for beneficiary
   - Varies by corridor

**Compliance APIs:**
- **Response to Transaction RFI** (Mandatory)
  - Answer compliance questions
  - Required for flagged transfers

- **Transactions** (Mandatory)
  - Retrieve transaction details
  - Check RFI status

**Exchange Rate APIs:**
- **Lock Exchange Rate** (Conditional)
  - Lock FX rate for multi-currency
  - Time-limited hold

**Lookup APIs:**
- **Fetch Supported Corridors v3** (Optional)
- **Search Routing Code** (Optional)
- **Fetch Bank Details** (Optional)

**Webhooks:**
- **Remit Transaction Initiated** (Mandatory)
  - Notification when transfer starts

**Typical Flow:**
```
Validate Beneficiary → Lock FX Rate → Create Transfer
   → Compliance Screening
   [If Hit] → RFI Callback → Answer RFI → Resubmit
   [If Clear] → Transaction Initiated Webhook → Track Status → Complete
```

**Best For:** All client types

**Requirements:**
- **Mandatory:** 7 APIs
- **Conditional:** 1 API (FX only)
- **Optional:** 5 APIs

---

#### 🎴 Card Management (11 APIs)
**What:** Issue and manage payment cards (virtual & physical)

**Lifecycle APIs:**
1. **Add Card V2** (Mandatory)
   - Issue new virtual or physical card
   - Card creation

2. **Activate Card V2** (Conditional)
   - Activate physical card with code
   - Physical cards only

3. **Convert Card** (Conditional)
   - Convert virtual to physical card
   - Physical cards only

4. **Assign Card** (Conditional)
   - Assign pre-printed card to cardholder
   - Bulk issuance only

**Management APIs:**
5. **Card Details V2** (Mandatory)
   - Retrieve card information
   - Non-sensitive details

6. **Update Card Details V2** (Mandatory)
   - Update phone/email for notifications
   - OTP delivery configuration

7. **Card List V2** (Optional)
   - Fetch all cards for customer
   - Filtering support

8. **Get Card Details Widget** (Optional)
   - Fetch in widget format
   - For non-PCI DSS compliance

**Control APIs:**
9. **Lock/Unlock Cards** (Mandatory)
   - Freeze and unfreeze card
   - Temporary restrictions

10. **Block and Replace Card** (Mandatory)
    - Block card and issue replacement
    - Compromised card handling

11. **Renew Card** (Mandatory)
    - Renew expired card
    - Proactive renewal

**Typical Flow (Virtual Card):**
```
Add Card V2 → Card Details V2 → Update Details → Lock/Unlock → Renew
```

**Typical Flow (Physical Card):**
```
Add Card V2 → Activate Card V2 → Convert to Physical → Assign Card
   → Update Details → Lock/Unlock → Renew
```

**Best For:** Platform Clients only

---

#### 🌍 Foreign Exchange (7 APIs)
**What:** Convert currencies and lock exchange rates

**APIs:**
1. **Exchange Rate Lock and Hold** (Optional)
   - Lock rate temporarily
   - Used before payout

2. **Create Quote** (Optional)
   - Get quote for currency pair
   - Returns quote ID

3. **Fetch Quote** (Optional)
   - Retrieve quote details
   - Check expiry time

4. **Create Conversion** (Optional)
   - Initiate currency conversion
   - Uses locked quote

5. **Fetch Conversion** (Optional)
   - Check conversion status
   - Confirm completion

6. **List Conversions** (Optional)
   - View all conversions
   - Filter by date/status

7. **Conversion Status Webhook** (Optional)
   - Notification on status change
   - Real-time updates

**Typical Flow:**
```
Lock Rate OR Create Quote → Fetch Quote → Create Conversion
   → Conversion Status Webhook → Fetch Conversion → Complete
```

**Note:** All APIs are optional - use based on your multi-currency needs

---

#### ✅ Verify (3 APIs)
**What:** Account verification services

**APIs:**
1. **Verify Account v2** (Optional)
   - Initiate verification process
   - Various verification methods

2. **Verify Account Status** (Optional)
   - Check verification status
   - Real-time updates

3. **Verify Account Webhook** (Optional)
   - Notification when verified
   - Background verification

**Typical Flow:**
```
Verify Account v2 → Verify Account Webhook → Verify Account Status → Confirmed
```

**Best For:** All client types

---

## How to Read Your Recipe

### Color Coding System

| Color | Requirement | Meaning | Action |
|-------|-------------|---------|--------|
| 🔴 RED | Mandatory | Must implement | Critical - don't skip |
| 🟡 YELLOW | Conditional | Required IF scenario applies | Check remarks for conditions |
| 🟢 GREEN | Optional | Nice-to-have | Implement for enhanced functionality |

### Recipe Sheet Columns

**API ID**
- Unique identifier (e.g., P001, CA001)
- Use for reference

**Service Category**
- Which service group (Payout, Cards, etc.)
- Helps with organization

**API Name**
- Official NIUM API name
- Use in documentation

**Description**
- What the API does
- Quick reference

**Requirement**
- Mandatory / Conditional / Optional
- Defines implementation priority

**Applicable Client Types**
- Which client types can use it
- Verify your type is listed

**Use Cases**
- Which use cases need this API
- Confirm your use case

**Notes**
- Important tips or constraints
- Version recommendations
- Async flow info

**Remarks**
- Your implementation notes
- Add custom details

---

## API Categories & Services

### API Statistics

| Service | Total | Mandatory | Conditional | Optional |
|---------|-------|-----------|-------------|----------|
| Customer Onboarding | 4 | 2 | 1 | 1 |
| Wallet Management | 6 | 4 | 0 | 2 |
| Payout | 13 | 7 | 1 | 5 |
| Card Management | 11 | 6 | 3 | 2 |
| Foreign Exchange | 7 | 0 | 0 | 7 |
| Verify | 3 | 0 | 0 | 3 |
| **TOTAL** | **44** | **19** | **5** | **20** |

---

## Implementation Workflows

### Workflow 1: Payout Service Provider

**Client Type:** Non-Bank FI Client  
**Use Case:** Payout (Money Transfers)

**Required APIs:**
- Customer Onboarding (4 APIs)
  - Create Customer v5
  - Get Customer v5
  - Customer Status Webhook

- Payout (13 APIs)
  - Transfer Money (Core)
  - Fetch Purpose Code
  - Fetch Remittance Life Cycle Status
  - Transaction Compliance Status Callback
  - Response to Transaction RFI
  - Transactions
  - Remit Transaction Initiated Webhook
  - Lock Exchange Rate (if multi-currency)
  - Beneficiary Validation Schema v2
  - Fetch Supported Corridors v3
  - Search Routing Code APIs

**Total APIs:** 17

**Implementation Timeline:**
1. Week 1: Onboarding APIs
2. Week 2: Beneficiary & Compliance APIs
3. Week 3: Transfer & Webhook APIs
4. Week 4: Testing & Compliance

---

### Workflow 2: Platform Client - Full Stack

**Client Type:** Platform Client  
**Use Case:** Full Stack (Complete Solution)

**Required APIs:**
- All 44 APIs available
- Focus on:
  1. Customer Onboarding (Foundation)
  2. Wallet Management / Payin (Receive Money)
  3. Card Management (Issue Cards)
  4. Payout (Send Money)
  5. FX (Multi-currency)
  6. Verify (Compliance)

**Implementation Approach:**
- **Phase 1:** Core (Onboarding, Payin, Payout) = 23 APIs
- **Phase 2:** Cards & Enhanced (Card Management, FX) = 18 APIs
- **Phase 3:** Advanced (Verify, Webhooks) = 3 APIs

**Total APIs:** 44

**Implementation Timeline:**
- Phase 1: 8 weeks
- Phase 2: 6 weeks
- Phase 3: 4 weeks
- Total: 18 weeks

---

### Workflow 3: Enterprise - Collections Only

**Client Type:** NonFI Direct (Enterprise)  
**Use Case:** Payin (Collections)

**Required APIs:**
- Customer Onboarding (4 APIs)
- Wallet Management / Payin (6 APIs)

**Total APIs:** 10

**Implementation Timeline:**
1. Onboarding: 2 weeks
2. Payin: 2 weeks
3. Testing: 1 week
4. Go-Live: Ready

---

## Advanced Usage

### Using the Compatibility Matrix

**Location:** `Compatibility Matrix` sheet

Shows which use cases work with which client types:

```
              | Onboarding | Payin | Payout | Cards | Spend | FX | Verify
Bank COBO     |     ✓      |   ✗   |   ✓    |   ✗   |   ✗   |  ✓  |   ✓
Bank POBO     |     ✓      |   ✗   |   ✓    |   ✗   |   ✗   |  ✓  |   ✓
Non-Bank FI   |     ✓      |   ✓   |   ✓    |   ✗   |   ✗   |  ✓  |   ✓
NonFI Direct  |     ✓      |   ✓   |   ✓    |   ✗   |   ✗   |  ✓  |   ✓
Platform      |     ✓      |   ✓   |   ✓    |   ✓   |   ✓   |  ✓  |   ✓
```

**Usage:**
- Verify your client type × use case combination is supported
- Identify service combinations that work together
- Plan phased implementations

---

### Exporting Your Recipe

**Steps:**
1. Complete your selections in Service Selector
2. Go to Your Recipe sheet
3. Select the data (A1 through I + all filled rows)
4. Copy (Ctrl+C)
5. Paste in Word/Confluence for team sharing
6. Add your internal notes

---

### Adding Custom Notes

**In Your Recipe Sheet:**
- Column I is "Remarks"
- Add your implementation notes
- Track dependencies
- Document team assignments

**Example:**
```
Remarks:
- C001: Priority - coordinate with compliance team
- W001: Async flow - requires webhook infrastructure
- P007: Multi-corridor support needed - check with architect
```

---

## Common Questions

### Q: Do I need ALL the APIs?
**A:** No. Use the Service Selector to choose only what you need. Mandatory APIs must be implemented; optional ones add features.

### Q: Can I implement services in any order?
**A:** Generally yes, but follow logical order:
1. Customer Onboarding (foundation)
2. Wallet/Payin (receive money)
3. Payout (send money)
4. Cards (issue cards)
5. FX/Verify (enhancements)

### Q: What if my use case isn't listed?
**A:** Refer to the Compatibility Matrix. Your client type determines which services are available. Combine services as needed.

### Q: How long does implementation take?
**A:** Depends on APIs selected:
- Single service: 2-4 weeks
- Multiple services: 8-18 weeks
- Full stack (44 APIs): 18+ weeks

### Q: What about webhooks?
**A:** Webhooks are often Mandatory. Plan infrastructure early:
- Webhook endpoint setup
- Error handling & retries
- Security & validation
- Monitoring & logging

---

## Troubleshooting

### Issue: Client Type dropdown is empty
**Solution:** Ensure `Client & Use Case Reference` sheet has data. Check rows 4-8.

### Issue: APIs aren't showing in Your Recipe
**Solution:** 
1. Verify selections in Service Selector
2. Check that at least one service is selected
3. Ensure Client Type is selected

### Issue: Formula errors (#REF!, #NAME!)
**Solution:**
1. Check that all reference sheets exist
2. Verify sheet names match exactly (case-sensitive)
3. Recreate from latest version

---

## Support Resources

### NIUM Documentation
- API Documentation: `playbook.nium.com`
- Sample Flows: `gallery.preprod.nium.com`
- Sandbox Testing: Use provided credentials

### This Workbook
- **API Database:** Complete reference of 44+ APIs
- **Implementation Guide:** Detailed descriptions
- **Compatibility Matrix:** Service combinations

### Next Steps
1. Review your recipe thoroughly
2. Check Mandatory APIs (RED) first
3. Plan webhook infrastructure
4. Assign developers to API groups
5. Begin sandbox testing

---

## Version History

**v2.0 (Current)**
- 44+ APIs across 6 categories
- Service Selector with granular selection
- Compatibility Matrix
- Enhanced formatting and guides
- Dashboard overview

**v1.0**
- Basic recipe builder
- Client Type × Use Case matrix
- 30+ APIs

---

## Document Information

**Created:** September 2026  
**For:** NIUM API Integration Planning  
**Format:** Excel Workbook + Markdown Guide  
**APIs Covered:** 44+ across 6 services  
**Client Types:** 5 types  
**Use Cases:** 8 major workflows

---

**Ready to build your API recipe? Start with the Dashboard sheet!** 🚀
