
## 🏦 Bank Mini-Program

### 🎯 MVP Features

-   **User Accounts**
    
    -   Create new bank accounts linked to app identity.
        
    -   Basic authentication & security.
        
-   **Balance Management**
    
    -   Track balance per account.
        
    -   Admins can manually increase balances.
        
-   **Money Transfers**
    
    -   Transfer between accounts (P2P).
        
-   **Payment Links (minimal)**
    
    -   Generate a link with an amount → another user can pay.
        

### 📌 Phases

1.  **Phase 1 (Core Banking)**
    
    -   Account creation, balance storage, admin balance adjustment.
        
    -   Simple money transfer.
        
2.  **Phase 2 (Payments)**
    
    -   Deposit/payment links (with expiration + unique ID).
        
    -   Basic transaction history.
        
3.  **Phase 3 (Advanced)**
    
    -   Integration with external payment gateways.
        
    -   Fraud detection, withdrawal methods, refunds.
        

----------

## 📧 Email Mini-Program

### 🎯 MVP Features

-   **Account Creation**
    
    -   Anyone can register an email account (`username@service`).
        
-   **Send/Receive Emails**
    
    -   Basic text emails between users inside the system.
        
-   **Inbox & Sent Views**
    
    -   Simple list view of received/sent emails.
        

### 📌 Phases

1.  **Phase 1 (Core Email)**
    
    -   Local send/receive (within app only).
        
    -   Simple inbox & sent items.
        
2.  **Phase 2 (Enhanced Email)**
    
    -   Attachments support (images, docs).
        
    -   Search & filters (by sender, subject).
        
3.  **Phase 3 (Integration)**
    
    -   Interoperability with external email (SMTP/IMAP).
        
    -   Spam filtering, security (2FA, DKIM/SPF).
        

----------

## 🔗 How They Fit Together

-   The **bank program** can support **payments in Food, Map, or Ride services**.
    
-   The **email program** can be used for **user communication, order receipts, transaction confirmations, or customer service.**
    
-   Both remain **modular** → they can run independently but integrate tightly with the ecosystem.
