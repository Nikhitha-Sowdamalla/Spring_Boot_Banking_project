
# 🏦 Spring Boot Banking System API (with H2 Database)  

This is a **Spring Boot Banking API** that allows:  
✅ Creating multiple bank accounts.  
✅ Depositing money into accounts.  
✅ Withdrawing money from accounts.  
✅ Transferring money between two accounts.  
✅ Checking account balance.  
✅ Using an **in-memory H2 database** instead of a persistent database.  

---

## 💾 Technologies Used  
- ✅ **Spring Boot 3.0+**  
- ✅ **H2 Database (in-memory)**  
- ✅ **Java 8+**  
- ✅ **Spring Web (REST APIs)**  

---

## 📊 Features  

| Feature Name        | Supported?     |  
|-------------------|-----------------|  
| ✅ Deposit Money     | Yes              |  
| ✅ Withdraw Money    | Yes              |  
| ✅ Transfer Money    | Yes              |  
| ✅ Check Balance     | Yes              |  
| ✅ H2 Database       | Yes (In-Memory)  |  
| ✅ Account Management| Yes              |  

---

## 📊 API Endpoints (with JSON Response Examples)  

### ✅ 1. **Create a Bank Account**  
**Endpoint:**  
```plaintext
POST: http://localhost:8080/accounts/create
```  

**Request Body (JSON):**  
```json
{
  "accountHolderName": "John Doe",
  "initialBalance": 1000
}
```  

**Response:**  
```json
{
  "accountId": 1,
  "accountHolderName": "John Doe",
  "balance": 1000.0
}
```  

---

### ✅ 2. **Deposit Money into Account**  
**Endpoint:**  
```plaintext
POST: http://localhost:8080/accounts/deposit
```  

**Request Body (JSON):**  
```json
{
  "accountId": 1,
  "amount": 500
}
```  

**Response:**  
```json
{
  "message": "₹500 deposited successfully.",
  "currentBalance": 1500.0
}
```  

---

### ✅ 3. **Withdraw Money from Account**  
**Endpoint:**  
```plaintext
POST: http://localhost:8080/accounts/withdraw
```  

**Request Body (JSON):**  
```json
{
  "accountId": 1,
  "amount": 200
}
```  

**Response:**  
```json
{
  "message": "₹200 withdrawn successfully.",
  "currentBalance": 1300.0
}
```  

---

### ✅ 4. **Transfer Money Between Accounts**  
**Endpoint:**  
```plaintext
POST: http://localhost:8080/accounts/transfer
```  

**Request Body (JSON):**  
```json
{
  "fromAccountId": 1,
  "toAccountId": 2,
  "amount": 300
}
```  

**Response:**  
```json
{
  "message": "₹300 transferred successfully from Account 1 to Account 2."
}
```  

---

### ✅ 5. **Check Account Balance**  
**Endpoint:**  
```plaintext
GET: http://localhost:8080/accounts/balance/1
```  

**Response:**  
```json
{
  "accountId": 1,
  "accountHolderName": "John Doe",
  "balance": 1000.0
}
```  

---

## ✅ 💻 How to Run This Project  
### **1. Clone the Repository**  
```bash
git clone https://github.com/your-username/Banking-System.git
cd Banking-System
```  

---

### **2. Build the Project**  
Use Maven to build the project:  
```bash
mvn clean install
```  

---

### **3. Run the Application**  
Run the Spring Boot Application:  
```bash
mvn spring-boot:run
```  

OR open **`BankingApplication.java`** in your IDE and click **Run**.  

---

### **4. Access H2 Database (Optional)**  
If you want to view the H2 in-memory database, open:  
```plaintext
http://localhost:8080/h2-console
```  

✅ **JDBC URL:** `jdbc:h2:mem:testdb`  
✅ **Username:** `sa`  
✅ **Password:** (Leave it blank)  

👉 Once inside, you can see all accounts created in the **ACCOUNTS** table.  

---

## ✅ 💸 Default Table Structure  
Once you create accounts or make transactions, H2 will automatically generate this table:  

### **Table: ACCOUNTS**  
| Account ID | Account Holder Name | Balance (₹)     |  
|------------|--------------------|-----------------|  
| 1          | John Doe             | ₹1000.0         |  
| 2          | Rahul Sharma         | ₹5000.0         |  

---

## ✅ 💯 Expected Scenarios  
| Action                        | Expected Outcome                                                                                  |  
|-------------------------------|----------------------------------------------------------------------------------------------------|  
| Create Account                 | Generates unique account ID + adds balance                                                        |  
| Deposit Money                  | Increases account balance                                                                          |  
| Withdraw Money                 | Deducts money (if sufficient balance)                                                              |  
| Transfer Money                 | Deducts from sender and credits receiver account                                                   |  
| Check Balance                  | Shows balance of any account                                                                      |  

---

## ✅ 💥 Error Handling  
The system also handles:  
| Error Scenario                          | Error Message                                                              | HTTP Status |  
|------------------------------------------|---------------------------------------------------------------------------|-------------|  
| Insufficient Balance                    | `Insufficient balance in your account.`                                    | 400         |  
| Invalid Account ID                      | `Account not found.`                                                       | 404         |  
| Negative Deposit Amount                 | `Deposit amount cannot be negative.`                                       | 400         |  
| Negative Transfer Amount                | `Transfer amount must be positive.`                                        | 400         |  

---

## ✅ 📊 Sample Transaction Flow  
Here's a sample transaction flow:  

1. **Create Account:**  
   - ✅ John Doe → ₹1000.0  
   - ✅ Rahul Sharma → ₹5000.0  

2. **Deposit ₹500 to John Doe's Account:**  
   - ✅ Balance → ₹1500.0  

3. **Withdraw ₹200 from John Doe's Account:**  
   - ✅ Balance → ₹1300.0  

4. **Transfer ₹300 from John Doe → Rahul Sharma:**  
   - ✅ John Doe → ₹1000.0  
   - ✅ Rahul Sharma → ₹5300.0  

