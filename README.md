![An image of blue sticky notes on a wall with a yellow one standing out][image1]  
**SMS SERVICE SYSTEM**

 

# Overview

Implement an sms service with Golang

# ENTITIES

### 

### **1.User**

Represents the users of the system.

* **Attributes**:  
  * `UserID`: A unique identifier for each user.  
  * `Name`: The full name of the user.  
  * `ProfilePicture`: URL or file path for the user's avatar.  
  * `Email`: The user's email address for communication and notifications.  
  * `PhoneNumber`: The user's personal phone number.  
  * `Password`: Encrypted password for authentication.  
  * `SubscriptionPlan`: The current subscription tier (e.g., Basic, Premium).  
  * `QuotaLimit`: The number of messages allowed per month.  
  * `MessagesRemaining`: The number of messages the user can still send.  
  * `SubscriptionStatus`: Status of the user's subscription (e.g., Active, Expired).  
- 

### **2\. Message**

Represents the messages sent through the system.

* **Attributes**:  
  * `MessageID`: A unique identifier for each message.  
  * `SenderID`: The `UserID` of the user who sent the message.  
  * `Content`: The text content of the message.  
  * `Timestamp`: When the message was created.  
  * `ScheduledTime`: Timestamp for when the message is intended to be sent (for scheduled messages).  
  * `Status`: The current status of the message (e.g., Sent, Failed, Queued).

### **3\. Recipient**

Represents the recipients of messages.

* **Attributes**:  
  * `RecipientID`: A unique identifier for each recipient.  
  * `Name`: The name of the recipient (optional).  
  * `PhoneNumber`: The recipient's phone number.  
  * `UserID`: Links the recipient to a specific user.

### **4\. Payment**

Tracks payments made by users.

* **Attributes**:  
  * `PaymentID`: A unique identifier for each payment.  
  * `UserID`: The user who made the payment.  
  * `Amount`: The payment amount.  
  * `Date`: The date of the transaction.  
  * `PaymentStatus`: Status of the payment (e.g., Completed, Failed).

### **5\. Payment**

**Tracks payments made by users.**

* **Attributes:**  
  * **`PaymentID`: A unique identifier for each payment.**  
  * **`UserID`: The user who made the payment.**  
  * **`Amount`: The payment amount.**  
  * **`Date`: The date of the transaction.**  
  * **`PaymentStatus`: Status of the payment (e.g., Completed, Failed).**

### **6\. MessageQueue**

**Handles message queuing and delivery.**

* **Attributes:**  
  * **`QueueID`: A unique identifier for the queue entry.**  
  * **`MessageID`: The ID of the message in the queue.**  
  * **`RecipientID`: The recipient associated with the message.**  
  * **`ScheduledTimestamp`: Time at which the message was placed in the queue.**  
  * **`FailureReason`: Explanation for failed delivery attempts.**  
  * **`ProcessingTime`: Time taken for the message to move through the queue.**  
  *   
  * **`Status`: Current delivery status (e.g., Queued, Delivered, Failed).**  
  * **`RetryCount`: Number of retry attempts for delivery.**

### **7\. Subscription**

Represents subscription plans and their details.

* **Attributes**:  
  * `SubscriptionID`: A unique identifier for each subscription.  
  * `PlanName`: Name of the plan (e.g., Basic, Premium).  
  * `MessageLimit`: The number of messages allowed under the plan.  
  * `Price`: The monthly price for the subscription.  
  * `Duration`: Length of the subscription (e.g., 1 month, 1 year).

### **Core User Stories**

1. As a User, I want to authenticate into the SMS service securely, so that I can access my account without the risk of data breaches.  
2. As a User, I want to compose messages and send them to a list of phone numbers, so that I can communicate with multiple recipients at once.  
3. As a User, I want to view my subscription plan details, so that I can understand my monthly message quota and payment status.  
4. As a User, I want to upgrade or renew my subscription plan easily, so that I can access more features or increase my message limit.  
5. As a User, I want to receive notifications when I am close to exceeding my monthly message quota, so that I can plan my usage or upgrade my plan.  
6. As a User, I want to schedule messages to be sent at a specific time, so that I can automate reminders and announcements.  
7. As a User, I want to track the delivery status of my messages, so that I know whether they were successfully sent to recipients.

### **Subscription-Specific Stories**

1. **As a User**, I want to apply promotional codes when subscribing, so that I can benefit from discounts.  
2. **As a User**, I want to enable auto-renewal for my subscription, so that I don’t lose access to the service unexpectedly.  
3. **As a System**, I need to disable message-sending features once a user exceeds their quota, so that the subscription rules are enforced.  
4. **As a User**, I want to see detailed statistics about my message usage (e.g., sent messages per day), so that I can manage my plan efficiently.

### **Recipient Management Stories**

1. **As a User**, I want to save and manage recipient lists (e.g., adding, deleting, grouping), so that I don’t have to re-enter phone numbers repeatedly.  
2. **As a User**, I want to check if recipients have opted in to receive messages, so that I comply with communication regulations.  
3. **As a User**, I want to personalize messages for recipients (e.g., inserting their names), so that my communication feels more tailored and professional.

### **Error Handling Stories**

1. **As a User**, I want to receive clear error messages when a delivery fails (e.g., invalid phone number, blocked recipient), so that I can troubleshoot and ensure successful communication.  
2. **As a System**, I need to retry sending failed messages automatically, so that the service is more reliable for users.

### **Advanced Features Stories**

1. **As a User**, I want to integrate the SMS service with external tools (e.g., CRM systems), so that I can streamline my communication workflow.  
2. **As a User**, I want to send multimedia messages (e.g., images or videos), so that I can share visual content with recipients.

### **System Stories**

1. **As a System**, I need to monitor the user's message quota and subscription status, so that the application runs smoothly and meets user expectations.  
2. **As a System**, I need to validate phone numbers before sending messages, so that invalid entries are flagged and corrected.

