# 💳 Payment Gateway System (LLD)

A **Low Level Design implementation of a Payment Gateway System in C++** demonstrating multiple design patterns used in scalable backend systems.

This system simulates payment processing using gateways like **Paytm** and **Razorpay** with retry logic, factory creation, and unified service handling.

---

# 🧠 Design Patterns Used

| Pattern | Usage |
|------|------|
| Singleton | PaymentController, PaymentService, GatewayFactory |
| Factory | Creates payment gateways |
| Proxy | Adds retry mechanism |
| Strategy | BankingSystem implementations |
| Template Method | Standard payment flow |

---

# 🏗 Architecture Flow

```
Client
   |
   v
PaymentController
   |
   v
PaymentService
   |
   v
GatewayFactory
   |
   v
PaymentGatewayProxy
   |
   v
Concrete Payment Gateway
   |
   v
Banking System
```

---

# 📦 Current Project Structure

Since this is an **LLD demonstration**, the entire implementation is kept in a single file.

```
payment-gateway-system
│
├── main.cpp
└── README.md
```

---

# 📚 Core Classes

### 1️⃣ PaymentRequest
Stores payment details.

```
sender
receiver
amount
currency
```

---

### 2️⃣ BankingSystem (Strategy)

Abstract interface for bank processing.

Implementations:

- PaytmBankingSystem
- RazorpayBankingSystem

---

### 3️⃣ PaymentGateway (Template Method)

Defines the payment workflow.

```
processPayment()
   |
   ├── validatePayment()
   ├── initiatePayment()
   └── confirmPayment()
```

Concrete implementations:

- PaytmGateway
- RazorpayGateway

---

### 4️⃣ PaymentGatewayProxy

Adds retry functionality if payment fails.

---

### 5️⃣ GatewayFactory (Singleton)

Creates payment gateway objects dynamically.

```
getGateway(GatewayType type)
```

---

### 6️⃣ PaymentService (Singleton)

Acts as a unified API for processing payments.

---

### 7️⃣ PaymentController (Singleton)

Handles client requests and coordinates the flow.

---

# 🔄 Payment Execution Flow

```
Client
  |
  v
PaymentController::handlePayment()
  |
  v
GatewayFactory::getGateway()
  |
  v
PaymentService::processPayment()
  |
  v
PaymentGatewayProxy
  |
  v
Concrete Gateway
  |
  v
BankingSystem
```

---

# ▶️ How to Run

### Compile

```
g++ main.cpp -o payment
```

### Run

```
./payment
```

---

# 🧪 Example Execution

```
Processing via Paytm
------------------------------
[Paytm] Validating payment
[Paytm] Initiating payment
[Paytm] Confirming payment
Result: SUCCESS
```

---

# 🚀 Future Improvements

- Add Stripe / PayPal gateway
- Add database logging
- Add transaction history
- Add REST API
- Split classes into multiple files

---

# 👨‍💻 Author

**Siddharth Chauhan**

BTech CSE  
Interested in System Design, AI and Robotics