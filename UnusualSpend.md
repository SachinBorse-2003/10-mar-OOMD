# Unusual Spending Alert System

## Scenario

You work at a credit card company and are tasked with adding a value-add feature. The goal is to provide alerts to users when their spending in any particular category is higher than usual. The system should:

1. Compare the total amount paid for the current month, grouped by category, with the previous month.
2. Filter down to the categories for which the user spent at least 50% more this month than last month.
3. Compose an email message to the user listing the categories for which spending was unusually high.

## Object-Oriented Principles in Use
1. ### Abstraction:

The CreditCard class abstracts away the details of spending tracking. It encapsulates the necessary data and methods, allowing the system to focus on the high-level concept of credit card functionality.

2. ### Encapsulation:

Both the CreditCard and EmailComposer classes encapsulate their respective functionalities. They hide the internal details and provide well-defined interfaces for interacting with their objects.

# Object-Oriented Modeling and Design (OOMD)

## Classes:

### 1. CreditCard
   - Properties:
     - `cardNumber: string`
     - `owner: User`

### 2. User
   - Properties:
     - `name: string`
     - `emailId: string`
     - `transactions: List[Transaction]`

### 3. Transaction
   - Properties:
     - `amount: float`
     - `category: Category`
     - `timestamp: DateTime`

### 4. Category
   - Properties:
     - `name: string`

### 5. Alert
   - Properties:
     - `user: User`
     - `categoriesWithUnusualSpend: List[Category]`
     - `totalUnusualSpend: float`

## States and Methods:

### CreditCard
- **States:**
  - `cardNumber`: The unique identifier for the credit card.
  - `owner`: The user associated with the credit card.

### User
- **States:**
  - `name`: The name of the user.
  - `emailId`: The email address of the user.
  - `transactions`: A list of transactions made by the user.

- **Behaviour:**
  - `filterCategoriesWithUnusualSpend(month: Month): List[Category]`
    - Filters and returns the categories for which the user spent at least 50% more in the given month compared to the previous month.

### Transaction
- **States:**
  - `amount`: The amount spent in the transaction.
  - `category`: The category of the transaction.
  - `timestamp`: The timestamp of the transaction.

### Category
- **States:**
  - `name`: The name of the spending category.

### Alert
- **States:**
  - `user`: The user for whom the alert is generated.
  - `categoriesWithUnusualSpend`: The list of categories with unusually high spending.
  - `totalUnusualSpend`: The total amount spent unusually.

- **Behaviour:**
  - `composeEmailMessage(): str`
    - Composes and returns the email message listing the categories with unusually high spending.

### MonthlySpendingAnalyzer
- **Behaviour:**
  - `compareMonthlySpending(user: User, currentMonth: Month, previousMonth: Month): Alert`
    - Compares the total amount spent in each category between the current and previous months, generates an alert for unusually high spending, and returns it.


