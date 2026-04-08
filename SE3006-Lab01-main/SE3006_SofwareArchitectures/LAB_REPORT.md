

** Furkan Efe Yüksel / 220717012

---

### 1. Objective
The goal of this lab was to implement a simple order management system using the **Layered Architecture** pattern. The project demonstrates the separation of concerns by dividing the application into three distinct layers: Persistence, Business, and Presentation.

### 2. Architectural Layers

#### 2.1. Persistence Layer (Data Access)
- **Class:** `ProductRepository`
- **Details:** This layer handles data storage. In this implementation, a `HashMap` is used as an in-memory database.
- **Key Methods:** `findById(Long id)` for retrieving products and `save(Product product)` for updating product information.

#### 2.2. Business Layer (Business Logic)
- **Class:** `OrderService`
- **Details:** Contains the core logic of the application. It validates product existence and stock availability before processing an order.
- **Dependency:** It uses **Constructor Injection** to receive the `ProductRepository`.
- **Exception Handling:** Throws `IllegalArgumentException` if the product is not found or if there is insufficient stock.

#### 2.3. Presentation Layer (User Interface)
- **Class:** `OrderController`
- **Details:** Acts as an entry point for user requests. It triggers the business logic and handles exceptions to provide user-friendly feedback.
- **Error Management:** Uses a `try-catch` block to capture errors from the service layer and prints formatted success/error messages.

### 3. Implementation Details
The application follows the principle of **Dependency Injection (DI)**. All dependencies are injected via constructors, making the system more modular and testable.

### 4. Test Scenarios and Results
The system was tested with three main scenarios in the `Main` class:
1. **Valid Order:** Successfully reduced stock for a valid product.
2. **Insufficient Stock:** Correctly identified and blocked an order exceeding available stock.
3. **Invalid Product ID:** Handled cases where the requested Product ID did not exist, preventing a `NullPointerException` through proper null-checking.

---
