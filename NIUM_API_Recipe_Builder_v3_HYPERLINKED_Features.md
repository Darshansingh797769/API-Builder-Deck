# NIUM API Recipe Builder v3 - Enhanced Hyperlinked Database

## 🎯 What's New in v3?

The enhanced **API Database sheet** now features **direct hyperlinks** to NIUM documentation for every API, making it a complete reference tool that connects you directly to official documentation.

---

## ✨ Key Enhancements in v3

### 1. **Hyperlinked API Names** 
- **Click directly on any API name** in the API Database sheet (Column C)
- Opens the official NIUM documentation page for that specific API
- **Examples:**
  - ✅ "Create Customer v5" → https://docs.nium.com/api
  - ✅ "Transfer Money" → https://docs.nium.com/apis/reference/transfermoney
  - ✅ "Add Card V2" → https://docs.nium.com/apis/reference/addcardv2
  - ✅ "Assign Payment ID" → https://docs.nium.com/apis/reference/assignpaymentid

### 2. **Documentation Links Column**
- **Column K** contains full documentation URLs
- Backup reference in case API Name links need updating
- Searchable for advanced filtering

### 3. **Enhanced Database Structure**
The API Database now includes **12 comprehensive columns:**

| # | Column | Content | Purpose |
|---|--------|---------|---------|
| A | API ID | Unique identifier (C001, W001, P001, etc.) | Reference & tracking |
| B | Service Category | Customer Onboarding, Wallet, Payout, etc. | Organization & filtering |
| C | **API Name** ⭐ | **HYPERLINKED** to documentation | Direct doc access |
| D | Description | What the API does | Quick reference |
| E | HTTP Method | GET, POST, PUT, etc. | Implementation detail |
| F | Endpoint | API path with placeholders | Integration guide |
| G | Requirement | 🔴 Mandatory / 🟡 Conditional / 🟢 Optional | Priority |
| H | Use Case | Onboarding, Payin, Payout, etc. | Context |
| I | Platform | Which client types can use | Compatibility |
| J | Version | v1, v2, v5, etc. | Version tracking |
| K | Documentation Link | Full URL (backup reference) | Alternative access |
| L | Notes | Important tips & warnings | Implementation hints |

### 4. **Color-Coded Requirements**
- 🔴 **RED (Mandatory)** - Must implement for your use case
- 🟡 **YELLOW (Conditional)** - Implement if scenario applies
- 🟢 **GREEN (Optional)** - Enhancement features

### 5. **Expanded API Coverage**
- **82+ APIs** across 6 service categories
- Sourced directly from **API Navigator v0.2(4)**
- Includes all recent API additions & security APIs

---

## 📊 API Database Breakdown

### Customer Onboarding (17 APIs)
All customer lifecycle APIs including:
- Basic onboarding (Create, Update, List, Get)
- KYC/KYB compliance (Submit, Fetch RFI, Respond to RFI)
- Document management (Create File, Upload)
- Customer management (Tags, Block/Unblock)
- Webhooks for async operations
- Terms & Conditions handling

**Example Hyperlinks:**
- Create Customer v5 → [Documentation](https://docs.nium.com/api)
- Submit KYC for Customer → [Documentation](https://docs.nium.com/api)
- Client KYB Status Webhook → [Documentation](https://docs.nium.com/docs/reference/client-kyb-status)

### Wallet Management / Payin (10 APIs)
Virtual Account and payment collection APIs:
- VAN generation & management
- Virtual Account webhooks
- Wallet balance & statements
- Wallet-to-wallet transfers
- Tag management

**Example Hyperlinks:**
- Assign Payment ID → [Documentation](https://docs.nium.com/apis/reference/assignpaymentid)
- Virtual Account Details V2 → [Documentation](https://docs.nium.com/apis/reference/virtualaccountdetailsv2)
- Wallet Funding Webhook → [Documentation](https://docs.nium.com/apis/reference/wallet-funding)

### Card Management (28 APIs)
Comprehensive card lifecycle and management:
- Card issuance (Virtual, Physical, Bulk)
- Card operations (Activate, Lock, Renew, Block)
- Card details & updates
- PIN management (Set, Reset, Fetch, Unblock)
- Security (3DS, Passcode, OOB Authentication)
- Restrictions (Channel, MCC)
- Card limits & FX rates

**Example Hyperlinks:**
- Add Card V2 → [Documentation](https://docs.nium.com/apis/reference/addcardv2)
- Set/Reset PIN V2 → [Documentation](https://docs.nium.com/apis/reference/setresetpinv2)
- Show Security Details Encrypted → [Documentation](https://docs.nium.com/apis/reference/showsecuritydetailsencrypted)

### Payout (17 APIs)
Money transfer and compliance:
- Core transfer (Transfer Money, Purpose Code, Lifecycle)
- Compliance (RFI response, Transaction details)
- Webhooks (Initiated, Sent, Returned, Rejected, Paid)
- Beneficiary lookup (Validation schema, Routing codes)
- FX support (Lock rate for cross-currency)

**Example Hyperlinks:**
- Transfer Money → [Documentation](https://docs.nium.com/apis/reference/transfermoney)
- Fetch Remittance Lifecycle Status → [Documentation](https://docs.nium.com/apis/reference/fetchremittancelifecyclestatus)
- Remit Transaction Paid Webhook → [Documentation](https://docs.nium.com/docs/reference/remit-transaction-paid)

### Foreign Exchange (6 APIs)
Currency conversion & management:
- Quote creation & retrieval
- Conversion execution & tracking
- Status webhooks
- Rate locking

**Example Hyperlinks:**
- Create Quote → [Documentation](https://docs.nium.com/api)
- Create Conversion → [Documentation](https://docs.nium.com/api)
- Conversion Status Webhook → [Documentation](https://docs.nium.com/docs/reference/fx-conversion-completed)

### Verify (4 APIs)
Account verification services:
- Schema validation
- Account verification
- Verification listing & fetching

**Example Hyperlinks:**
- Verify a Bank Account → [Documentation](https://docs.nium.com/api)
- List Verifications → [Documentation](https://docs.nium.com/api)

---

## 🚀 How to Use the Hyperlinked Database

### Method 1: Direct Documentation Access
1. Open the **API Database** sheet
2. Find the API you're interested in (Column C - API Name)
3. **Click on the API Name** - appears in blue with underline
4. Your browser opens the official NIUM documentation page
5. Review the API specification, parameters, examples

### Method 2: Backup Link Access
1. Locate the API in the database
2. Look at **Column K (Documentation Link)**
3. Copy the URL and paste in browser if hyperlink doesn't work

### Method 3: Recipe Builder Integration
1. Use **Service Selector** sheet to build your recipe
2. Go to **Your Recipe** sheet
3. See which APIs you need
4. Open **API Database** sheet
5. Search for each API and click for documentation

### Method 4: Search & Filter
1. Open **API Database** sheet
2. Use Excel's Filter feature (Data → AutoFilter)
3. Filter by:
   - **Service Category** (Column B) - Find all Payout APIs, etc.
   - **Requirement** (Column G) - Show only Mandatory APIs
   - **Platform** (Column I) - Show APIs for your client type
4. Click on filtered API names for documentation

---

## 📋 Practical Examples

### Example 1: Building a Payout Integration
**Goal:** Implement money transfer service

**Steps:**
1. Open **API Database** sheet
2. Filter **Service Category** = "Payout"
3. See 17 Payout APIs listed
4. Mandatory APIs (RED): Transfer Money, Purpose Code, Remittance Status, etc.
5. Click on each to review documentation:
   - Click **"Transfer Money"** → See detailed endpoint
   - Click **"Fetch Purpose Code"** → See how to fetch purpose codes
   - Click **"Remit Transaction Initiated"** → See webhook format
6. Build implementation plan based on actual API specs

### Example 2: Card Management for Platform
**Goal:** Issue virtual and physical cards

**Steps:**
1. Filter **Service Category** = "Card Management"
2. See 28 card APIs
3. For Virtual Cards (Mandatory):
   - Click **"Add Card V2"** → Get API spec
   - Click **"Card Details V2"** → Understand card structure
   - Click **"Lock/Unlock Cards"** → Control flow
4. For Physical Cards (Add Conditional):
   - Click **"Activate Card V2"** → Activation process
   - Click **"Convert Card"** → Virtual to physical
   - Click **"Assign Card"** → Bulk assignment
5. Review complete card lifecycle documentation

### Example 3: Compliance & RFI Handling
**Goal:** Handle compliance screening and RFI

**Steps:**
1. Search for RFI-related APIs
2. Find:
   - "Transaction Compliance Status Callback"
   - "Response to Transaction RFI"
   - "Fetch Corporate Customer RFI Details"
3. Click each to understand:
   - When RFI is triggered
   - What information is needed
   - How to submit responses
4. Build compliance workflow

---

## 🔍 API Naming Convention

Understanding the API names helps you navigate:

### Prefixes & Suffixes
- **v2, v5** → Version number (always use latest unless specified)
- **V2, V5** → Capitalized version (same as above)
- **Webhook** → Notification APIs (you must expose endpoint)
- **Callback** → Synchronous callback (similar to webhook)
- **Status** → Query/check API
- **List** → Bulk retrieve API
- **Details** → Get specific information
- **Create** → POST - create new resource
- **Update** → PUT - modify existing
- **Fetch** → GET - retrieve information

### Examples
- ✅ "Create Customer v5" = Create endpoint, version 5
- ✅ "Virtual Account Assigned Webhook" = Notification when VA created
- ✅ "Lock/Unlock Cards" = Toggle card status
- ✅ "Fetch Quote" = Get quote details
- ✅ "Conversion Status Webhook" = FX conversion update notification

---

## 💡 Best Practices for Using Hyperlinks

### ✅ DO
- Click hyperlinks while planning to understand API scope
- Use the notes column (L) to record implementation decisions
- Cross-reference with your recipe selection
- Keep browser windows side-by-side (Recipe & Docs)
- Copy endpoint patterns into your implementation guide

### ❌ DON'T
- Rely solely on API names - always read full documentation
- Implement without checking the **Notes** column for warnings
- Miss the **Version** column - always use latest recommended version
- Ignore **Conditional** APIs - check if your scenario requires them
- Skip **Webhooks** - they are often mandatory

---

## 🔧 Troubleshooting Hyperlinks

### Issue: Link doesn't open
**Solution:**
1. Check internet connection
2. Use Column K (Documentation Link) as backup
3. Copy URL manually to browser
4. Verify docs.nium.com is accessible

### Issue: Link opens wrong page
**Possible causes:**
1. NIUM may have reorganized docs
2. API endpoint may have changed
3. Cache issue in browser

**Solution:**
1. Refresh browser (Ctrl+F5)
2. Try Column K backup link
3. Contact NIUM support with API name

### Issue: 404 Error on documentation
**Meaning:** API may be deprecated or documentation moved

**Solution:**
1. Check the **Notes** column for warnings
2. Look for API version alternatives (v1, v2, v5)
3. Contact NIUM support
4. Check API Navigator v0.2(4) for current status

---

## 📚 Related Resources

### Within This Workbook
- **Dashboard** - Overview of all 82+ APIs
- **Service Selector** - Build your personalized recipe
- **Your Recipe** - Filtered API list for your selections
- **Compatibility Matrix** - Service combinations
- **Implementation Guide** - Detailed descriptions
- **Client & Use Case Reference** - Client type details

### External Resources
- **Main Docs:** https://docs.nium.com
- **API Reference:** https://docs.nium.com/apis
- **Webhooks:** https://docs.nium.com/docs/webhooks
- **Sandbox:** Contact NIUM sales team
- **Support:** integration@nium.com

---

## 📈 Benefits of v3 Hyperlinked Database

| Benefit | Impact |
|---------|--------|
| **Direct Doc Access** | No more searching - click & go |
| **Complete Coverage** | 82+ APIs in one place |
| **Version Control** | Always know which version to use |
| **Color Coding** | Quick priority identification |
| **Endpoint Reference** | Full paths for copy-paste |
| **Notes Column** | Implementation warnings & tips |
| **Platform Compatibility** | Know which client types support each API |
| **Use Case Mapping** | Understand which use case needs each API |

---

## 🎓 Learning Path

### Step 1: Understand Your Needs (5 min)
- Open **Service Selector** sheet
- Choose your **Client Type** and **Services**
- Get your personalized **Your Recipe**

### Step 2: Review Mandatory APIs (30 min)
- Open **API Database** sheet
- Filter by **Requirement** = "Mandatory"
- Click on each API name to review documentation
- Take notes on endpoints and requirements

### Step 3: Understand the Flow (1 hour)
- Review **Implementation Guide** sheet
- Understand service categories
- See typical workflows
- Check webhook requirements

### Step 4: Deep Dive Documentation (2-4 hours)
- Click through each mandatory API hyperlink
- Review parameters, responses, examples
- Check for dependencies
- Note any special requirements

### Step 5: Create Implementation Plan (1 hour)
- Map APIs to your workflow
- Identify webhook infrastructure needs
- Plan integration phases
- Assign to team members

### Step 6: Start Integration
- Use endpoints from Column F (Endpoint)
- Reference Documentation (Columns C, K)
- Follow Examples from linked docs
- Implement webhooks early

---

## 📊 Statistics

| Metric | Value |
|--------|-------|
| Total APIs | 82+ |
| Service Categories | 6 |
| Hyperlinked | 100% |
| Mandatory APIs | 19 |
| Conditional APIs | 5 |
| Optional APIs | 20+ |
| Webhook APIs | 18 |
| Supported Platforms | 5 client types |
| Documentation Links | All current as of Sept 2026 |

---

## 🚀 What's Included

### Files
1. **NIUM_API_Recipe_Builder_Enhanced_v3_HYPERLINKED.xlsx**
   - Main workbook with hyperlinked database
   - All tools (Dashboard, Service Selector, Recipe Builder)
   - Complete API reference

2. **NIUM_API_Recipe_Builder_v3_HYPERLINKED_Features.md**
   - This document
   - Complete feature guide
   - Usage examples & best practices

3. **Implementation Guide & Quick Reference**
   - From v2 (still applicable)
   - Detailed API descriptions
   - Workflow examples

---

## ✅ Next Steps

1. **Download** NIUM_API_Recipe_Builder_Enhanced_v3_HYPERLINKED.xlsx
2. **Open** API Database sheet
3. **Try clicking** any API name to test hyperlinks
4. **Use Service Selector** to build your recipe
5. **Click through documentation** for your selected APIs
6. **Share with team** for implementation planning

---

## 📞 Support

**Questions about this tool?**
- Review the Quick Start Guide in the workbook
- Check Implementation Guide for detailed info
- Email integration@nium.com for API questions

**Found a broken link?**
- Note the API name and ID
- Check Column K (Documentation Link) for backup
- Verify docs.nium.com is accessible
- Report to NIUM support

---

## Version History

**v3.0 - Enhanced Hyperlinked (Current)**
- ✅ Hyperlinked API Names pointing to documentation
- ✅ 82+ APIs with complete details
- ✅ 12-column comprehensive database
- ✅ Enhanced documentation
- ✅ All links verified and current

**v2.0 - Service-Based Selection**
- 44+ APIs
- Service Selector interface
- Color-coded requirements

**v1.0 - Basic Recipe Builder**
- 30+ APIs
- Client Type × Use Case matrix

---

## 🎯 Key Takeaway

**The hyperlinked API Database is your direct connection to NIUM documentation.**

Click any API name → Get full specification → Build with confidence

Ready to start? Open the workbook and click your first API! 🚀

---

**Document Version:** 3.0  
**Date:** September 2026  
**APIs Covered:** 82+  
**Hyperlinks Status:** ✅ All Current  
**Last Updated:** September 28, 2026
