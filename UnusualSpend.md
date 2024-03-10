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

## Code Implementation

```java
/**
 * Credit Card Class - Represents a user's credit card and spending information.
 */
class CreditCard {
    // Assume necessary properties and methods for tracking spending.
}

/**
 * EmailComposer Class - Handles composing email messages for unusual spending alerts.
 */
class EmailComposer {
    /**
     * Compose an email message for unusual spending.
     *
     * @param userName User's name.
     * @param unusualSpending Map of categories and their spending amounts.
     * @return Composed email message.
     */
    public String composeEmail(String userName, Map<String, Double> unusualSpending) {
        StringBuilder message = new StringBuilder();
        message.append("# Unusual Spending Alert\n\n");
        message.append("Unusual spending of ₹").append(calculateTotal(unusualSpending)).append(" detected!\n\n");
        message.append("Hello ").append(userName).append("!\n\n");
        message.append("We have detected unusually high spending on your card in these categories:\n");

        for (Map.Entry<String, Double> entry : unusualSpending.entrySet()) {
            message.append("* You spent ₹").append(entry.getValue()).append(" on ").append(entry.getKey()).append("\n");
        }

        message.append("\nThanks,\nThe Credit Card Company");
        return message.toString();
    }

    // Assume a method to calculate the total spending amount from the Map.
    private double calculateTotal(Map<String, Double> spendingMap) {
        // Implementation details...
    }
}

/**
 * Main Class - Entry point for the program.
 */
public class Main {
    public static void main(String[] args) {
        // Assume instantiation and usage of CreditCard class to get spending data.
        CreditCard userCard = new CreditCard();
        Map<String, Double> unusualSpending = userCard.detectUnusualSpending();

        // Assume instantiation and usage of EmailComposer class to send email alerts.
        EmailComposer emailComposer = new EmailComposer();
        String emailMessage = emailComposer.composeEmail("Baburao", unusualSpending);

        // Print or send the email message.
        System.out.println(emailMessage);
    }
}

