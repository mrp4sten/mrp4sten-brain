Tags:
- [[SOLID]]
- [[Design Patterns]]
- [[Design Principles]]
- [[Programming]]

## Description
Open closed basically means Open for Extension, Closed for Modification. And this principle say that Classes should be open for extension but closed for modification. In doing so, we stop ourselves from modifying existing code and causing potential new bugs.

> The one exception to the rule is when fixing bugs in existing code.

## Samples

### Without Open Closed principle
```java
public class PaymentProcessor {

    public void processPayment(String paymentType, double amount) {
        if (paymentType.equals("CreditCard")) {
            processCreditCardPayment(amount);
        } else if (paymentType.equals("PayPal")) {
            processPayPalPayment(amount);
        } else if (paymentType.equals("BankTransfer")) {
            processBankTransferPayment(amount);
        }
    }

    private void processCreditCardPayment(double amount) {
        // Logic to process credit card payment
        System.out.println("Processing Credit Card payment of $" + amount);
    }

    private void processPayPalPayment(double amount) {
        // Logic to process PayPal payment
        System.out.println("Processing PayPal payment of $" + amount);
    }

    private void processBankTransferPayment(double amount) {
        // Logic to process bank transfer payment
        System.out.println("Processing Bank Transfer payment of $" + amount);
    }
}
```

### With Open Closed principle
```java
// PaymentMethod interface defines the contract for payment methods
public interface PaymentMethod {
    void processPayment(double amount);
}

// CreditCardPayment class implements the PaymentMethod interface
public class CreditCardPayment implements PaymentMethod {
    @Override
    public void processPayment(double amount) {
        System.out.println("Processing Credit Card payment of $" + amount);
    }
}

// PayPalPayment class implements the PaymentMethod interface
public class PayPalPayment implements PaymentMethod {
    @Override
    public void processPayment(double amount) {
        System.out.println("Processing PayPal payment of $" + amount);
    }
}

// BankTransferPayment class implements the PaymentMethod interface
public class BankTransferPayment implements PaymentMethod {
    @Override
    public void processPayment(double amount) {
        System.out.println("Processing Bank Transfer payment of $" + amount);
    }
}

// PaymentProcessor class is open for extension but closed for modification
public class PaymentProcessor {
    private PaymentMethod paymentMethod;

    public PaymentProcessor(PaymentMethod paymentMethod) {
        this.paymentMethod = paymentMethod;
    }

    public void processPayment(double amount) {
        paymentMethod.processPayment(amount);
    }
}

```