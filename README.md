import java.util.regex.*;

class InvalidPasswordException extends Exception {
    public InvalidPasswordException(String message) {
        super(message);
    }
}

public class PasswordChecker {

    public static void validatePassword(String password) throws InvalidPasswordException {
        if (password.length() <= 8) {
            throw new InvalidPasswordException("Пароль повинен бути довшим за 8 символів.");
        }

        if (!password.matches(".*[A-Z].*")) {
            throw new InvalidPasswordException("Пароль повинен містити хоча б одну велику літеру.");
        }

        if (password.matches("[0-9]+")) {
            throw new InvalidPasswordException("Пароль не може бути лише з цифр.");
        }

        System.out.println("Пароль прийнятий!");
    }

    public static void main(String[] args) {
        String userPassword = "Test123";  // Приклад введеного пароля

        try {
            validatePassword(userPassword);
        } catch (InvalidPasswordException e) {
            System.out.println("Помилка: " + e.getMessage());
        }
    }
}

import java.util.Scanner;

class ProductNotAvailableException extends Exception {
    public ProductNotAvailableException(String message) {
        super(message);
    }
}

public class Shop {

    public static void checkProduct(String[] availableProducts, String productName) throws ProductNotAvailableException {
        for (String product : availableProducts) {
            if (product.equalsIgnoreCase(productName)) {
                System.out.println("Товар знайдено! Ви можете його придбати.");
                return;
            }
        }
        throw new ProductNotAvailableException("Товар не знайдено.");
    }

    public static void main(String[] args) {
        String[] products = {"Яблука", "Банани", "Молоко", "Хліб"};

        Scanner scanner = new Scanner(System.in);
        System.out.println("Введіть товар для покупки:");
        String productToBuy = scanner.nextLine();

        try {
            checkProduct(products, productToBuy);
        } catch (ProductNotAvailableException e) {
            System.out.println("Помилка: " + e.getMessage());
        }
    }
}
