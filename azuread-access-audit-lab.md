# 📄 Building Audit‑Style Reports in Microsoft Entra ID (GUI Walkthrough)

A step‑by‑step guide for documenting user access, role changes, and orphaned accounts for compliance and governance.  

This guide demonstrates how to manually generate audit‑style evidence from the Microsoft Entra ID portal, mirroring the data collected by automated scripts or identity governance tools.  
It is ideal for compliance simulations, internal audits, access reviews, and documentation purposes.

---

## 🧭 Prerequisites

You must have one of the following roles to complete these steps:
- Global Administrator  
- Privileged Role Administrator  
- Security Administrator  
- Identity Governance Administrator  

You also need access to:  
👉 [https://entra.microsoft.com](https://entra.microsoft.com)

---

## 🟦 1. Audit User Access (Assigned Roles, Groups, and Apps)

Auditors often ask: **“Who has access to what?”**  
This section shows how to manually gather that evidence.

### 🔹 1.1 View a User’s Privileged Role Assignments
**Steps**
1. Go to **Identity → Users → All users**  
2. Select a user  
3. Navigate to **Assigned roles**  
4. Capture a screenshot of the user’s directory role assignments  

📷 **Screenshot Placeholder:**  
![User role assignments](images/user-role-assignments.png)

**What this represents in an audit:**  
- Confirms privileged access  
- Shows standing vs. temporary elevated permissions  
- Supports least‑privilege analysis  

---

### 🔹 1.2 View a User’s Group Membership (Access Through Groups)
**Steps**
1. In the same user profile, select **Groups**  
2. Capture a screenshot of group membership  

📷 **Placeholder:**  
![User group memberships](images/user-groups.png)

**Why this matters:**  
Group → App → Role mappings often grant hidden access.

---

### 🔹 1.3 View a User’s Application Assignments
**Steps**
1. Open the user profile  
2. Click **Applications**  
3. Capture app assignments  

📷 **Placeholder:**  
![User app assignments](images/user-app-assignments.png)

**Audit Value:**  
Shows access to business apps, including high‑risk apps (e.g., Salesforce, HRIS).

---

## 🟦 2. Audit Role Changes (Who Added / Removed Access?)

Compliance simulations require proving:
- Who assigned a role  
- Who revoked it  
- When it happened  
- Whether it was approved  

### 🔹 2.1 Access Audit Logs for Role Changes
**Steps**
1. Navigate to **Identity → Monitoring → Audit logs**  
2. In the search bar, type *role*  
3. Filter **Activity** for events such as:  
   - Add member to Role  
   - Remove member from Role  
   - Update Role Assignment  
4. Capture screenshots  

📷 **Placeholder:**  
![Role change audit logs](images/role-change-logs.png)

---

### 🔹 2.2 Filter Role Audit Events by User
1. Under Audit logs, click Add filters. In this lab, I selected **Initiated by**, but all of the options are:
**Filter by:**
- Initiated by  
- Target user  
- Activity  
- Date range  

📷 **Placeholder:**  
![Filtered role events](images/filtered-role-events.png)

**Audit Value:**  
Proves change accountability — who modified privileged access.

---

## 🟦 3. Identify Orphaned Accounts (Stale, Disabled, Guest, Unused)

Orphaned accounts are among the highest‑risk identity gaps during SOC or ISO/NIST compliance reviews.  

These include:
- Disabled accounts with roles  
- Users with no sign‑in activity for 90 + days  
- External users left behind (`#EXT#`)  
- Unlicensed accounts with administrator rights  
- Accounts with no manager / owner  

---

### 🔹 3.1 Find Stale Accounts (No Login in 90 + Days)
**Steps**
1. Go to **Identity → Monitoring → Sign‑in logs**  
2. Select **Add filter → User type**  
3. Sort by date or filter by 90 + day inactivity  
4. Capture a screenshot  

📷 **Placeholder:**  
![Stale accounts](images/stale-accounts.png)

---

### 🔹 3.2 Identify Disabled Accounts
**Steps**
1. Go to **Entra → Users → All users**  
2. At the top, click **Add filter**  
3. Select **No** 
4. Apply the filter
5. The list now shows ONLY disabled users (if there are any)

📷 **Placeholder:**  
![Disabled users](images/disabled-users.png)

**Audit Value:**  
Disabled accounts assigned to admin roles are a critical finding.

---

### 🔹 3.3 Identify Guest or External Users With Access
**Steps**
1. Go to **Users → All users**  
2. Apply filter: **User type = Guest**  
3. Capture guest accounts  
4. Click each → capture **Assigned Roles**  

📷 **Placeholder:**  
![Guest privileged accounts](images/guest-admins.png)

---

### 🔹 3.4 Find Accounts With No Assigned Manager (Orphaned Ownership)
**Steps**
1. Go to **Identity → Users**  
2. Add column: **Manager**  
3. Filter for “No manager assigned”  
4. Screenshot results  

📷 **Placeholder:**  
![Accounts with no manager](images/no-manager.png)

**Audit Value:**  
Shows accounts with unclear ownership — a strong finding during compliance checks.

---

## 🟦 4. Exportable Built‑In Reports (Evidence for Auditors)

Entra allows exporting several audit‑relevant CSVs.

### 🔹 4.1 Export Role Assignments
**Steps**
1. **Identity → Roles & administrators**  
2. Click a role  
3. Click **Download assignments**  

📷 **Placeholder:**  
![Export role assignments](images/export-role-assignments.png)

---

### 🔹 4.2 Export Sign‑in Logs
**Steps**
1. **Identity → Monitoring → Sign‑in logs**  
2. Click **Export → Choose CSV**  

📷 **Placeholder:**  
![Export sign‑in logs](images/export-signin-logs.png)

---

### 🔹 4.3 Export Directory Audit Logs
**Steps**
1. **Identity → Monitoring → Audit logs**  
2. Select **Download logs**  

📷 **Placeholder:**  
![Export audit logs](images/export-audit-logs.png)

---

## 🟦 5. Access Review Evidence (Compliance Simulation)

Most compliance frameworks (SOX, SOC 2, ISO 27001, PCI) require periodic access reviews.

### 🔹 5.1 Navigating Access Reviews
**Steps**
1. Go to **Identity Governance → Access Reviews**  
2. Open an existing review or create a new one  
3. Capture:  
   - Review definition  
   - Assigned reviewers  
   - Review results  
   - Users flagged for removal  

📷 **Placeholder:**  
![Access review evidence](images/access-review-results.png)

**Audit Value:**  
Shows active governance and remediation workflows.

---

## 🟦 6. What This Manual Audit Demonstrates

These screenshots and steps create a full audit trail showing:  

✔ What access users have  
✔ How roles are assigned and changed  
✔ Whether privileged accounts are stale  
✔ Whether orphaned accounts exist  
✔ Whether governance processes are active  
✔ Exportable artifacts that match compliance expectations  

They complement automation tools and scripts by providing the visual evidence auditors expect for access control assessments.
