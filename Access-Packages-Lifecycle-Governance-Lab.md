# 🧩 Configure Access Packages, Entitlement Management, and<br> Expiration Policies in Microsoft Entra ID  

*Simulating Full Identity Lifecycle Governance (using Access Packages and Entitlement Management)*  

---

## 🧭 Objective
Demonstrate how to govern user access in Microsoft Entra ID (Azure AD) by creating a catalog, defining access packages, adding resources, and configuring approval and expiration policies to automate the identity lifecycle.

---

## 🧰 Technologies Used
- Microsoft Entra ID (Azure Active Directory)  
- Microsoft 365 Admin Center  
- Entitlement Management / Access Packages  
- Access Reviews & Lifecycle Policies  

---

## ⚙️ Lab Steps

### 1️⃣ Create a Catalog
1. Sign in to [https://entra.microsoft.com](https://entra.microsoft.com).  
2. In the Search bar at the top of the window, type **Identity Governance** and select it under **Services**.
  
4. Select **+ New Catalog**.  
   - **Name:** `Demo`  
   - **Subscription:** Select an active subscription (if required).  
   - **Enabled:** Yes  
   - **Enabled for external users:** No  
5. Click **Create**.  
   > ✅ A new catalog (named *Demo*) is now available for access packages.  

---

### 2️⃣ Create an Access Package
1. Go to **Identity → Governance → Entitlement Management → Access Packages**.  
2. Select **+ New Access Package**.  
3. In **Basics**, enter:
   - **Name:** `Demo Access Package`
   - **Description:** `Provides governed access to internal resources.`
   - **Catalog:** Select `Demo`  
4. Click **Next → Resource Roles**.

---

### 3️⃣ Add Resources to the Access Package
1. On **Resources Roles**, select **+ Groups and Teams** → enable the toggle to *Show resources not in this catalog*.  
2. Choose a group (e.g., `Demo Group`) → **Role:** `Member`.  
3. Add **Applications**:
   - Toggle “Show resources not in catalog.”  
   - Select applications (e.g., `Box`, `Demo App`).  
   - Assign appropriate roles (`User`, `Admin`).  
4. Review that the listed resources include both group(s) and app(s).  
5. Click **Next → Requests**.

---

### 4️⃣ Define Who Can Request Access
1. In **Users who can request access**, choose:  
   - **For users in your directory:** ✅ Enabled.  
2. Under **Request type scope**, select: **All members (excluding guests)**.  
3. **Requires approval:** Yes.  
4. **Request justification:** Required.  
5. **Approver:** Manager (Direct Manager).  
6. **Fallback approver:** Specify an admin or security officer account.  
7. **Decision duration:** 14 days.  
8. Click **Next → Requester Information**.  

---

### 5️⃣ Requester Information (Optional)
- Skip custom questions unless you need to collect attributes from the requester.  
- Click **Next → Lifecycle**.

---

### 6️⃣ Configure Expiration and Lifecycle Policies
1. In **Expiration**, set **Access expires → After number of days = 365** (1 year).  
2. Enable **Allow custom duration requests from users** if applicable.  
3. Enable **Access Reviews:** ✅ Yes.  
4. Set review details:
   - **Start date:** Choose desired start.  
   - **Frequency:** Quarterly or Annually.  
   - **Duration:** e.g., 30 days.  
   - **Reviewer:** Manager.  
   - **Fallback reviewer:** Admin or IAM Lead.  
5. Click **Next → Rules → Next → Create**.  

---

### 7️⃣ Review and Create
Verify the summary page shows:
- Catalog Name = Demo  
- Resource Roles = Group(s) and Application(s) added  
- Requesters = All members (excluding guests)  
- Approval Workflow = Manager + Fallback Approver  
- Expiration = 1 year with Access Review  

Click **Create**.  
> ✅ The Access Package is provisioned and available in your tenant.  

---

### 8️⃣ Validate Lifecycle Governance
1. Open [https://myaccess.microsoft.com](https://myaccess.microsoft.com).  
2. Sign in as a standard user and locate the `Demo Access Package`.  
3. Submit a request including a justification.  
4. Approver receives notification, reviews, and approves.  
5. Confirm the requester is added to the group(s) and applications.  
6. When policy expires, the access is automatically revoked or queued for review.

---

## ✅ Outcome
After completing this lab, you will have:
- Created a catalog and access package for identity governance.  
- Configured group and application assignments through self‑service requests.  
- Implemented approval and review policies for access control.  
- Defined expiration policies to automate user offboarding and ensure compliance.  

---

**Author:** *Qadriyyah Abdullah [Ms Bey]*  
**Date:** *December 2025*  
**Tags:** `SC‑300` `AzureAD` `Microsoft Entra ID` `IdentityGovernance` `AccessPackages` `LifecycleManagement`
