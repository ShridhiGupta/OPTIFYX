import java.util.ArrayList;
import java.util.Scanner;

class Account {
    private double balance;
    private ArrayList<String> transactionHistory;

    public Account(double initialBalance) {
        this.balance = initialBalance;
        this.transactionHistory = new ArrayList<>();
        transactionHistory.add("Initial Balance: $" + initialBalance);
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        balance += amount;
        transactionHistory.add("Deposited: $" + amount);
    }

    public boolean withdraw(double amount) {
        if (amount > balance) {
            System.out.println("Insufficient Balance!");
            return false;
        } else {
            balance -= amount;
            transactionHistory.add("Withdrawn: $" + amount);
            return true;
        }
    }

    public void printTransactionHistory() {
        System.out.println("Transaction History:");
        for (String transaction : transactionHistory) {
            System.out.println(transaction);
        }
    }
}

class ATM {
    private Account account;
    private Scanner scanner;

    public ATM(Account account) {
        this.account = account;
        this.scanner = new Scanner(System.in);
    }

    public void start() {
        System.out.println("Welcome to the ATM");
        System.out.print("Enter User ID: ");
        String userId = scanner.next();
        System.out.print("Enter ATM PIN: ");
        int pin = scanner.nextInt();

        if (authenticate(userId, pin)) {
            showMenu();
        } else {
            System.out.println("Invalid Credentials! Exiting...");
        }
    }

    private boolean authenticate(String userId, int pin) {
        return userId.equals("admin") && pin == 1234; // Simple authentication
    }

    private void showMenu() {
        while (true) {
            System.out.println("\n1. View Available Balance");
            System.out.println("2. Withdraw Amount");
            System.out.println("3. Deposit Amount");
            System.out.println("4. View Mini Statement");
            System.out.println("5. Exit");
            System.out.print("Enter Choice: ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.println("Available Balance: $" + account.getBalance());
                    break;
                case 2:
                    System.out.print("Enter amount to withdraw: ");
                    double withdrawAmount = scanner.nextDouble();
                    if (account.withdraw(withdrawAmount)) {
                        System.out.println("Collect the cash: $" + withdrawAmount);
                    }
                    break;
                case 3:
                    System.out.print("Enter amount to deposit: ");
                    double depositAmount = scanner.nextDouble();
                    account.deposit(depositAmount);
                    System.out.println("Amount Deposited Successfully!");
                    break;
                case 4:
                    account.printTransactionHistory();
                    break;
                case 5:
                    System.out.println("Thank you for using our ATM!");
                    return;
                default:
                    System.out.println("Invalid Choice! Try again.");
            }
        }
    }
}

public class ATMInterface {
    public static void main(String[] args) {
        Account userAccount = new Account(5000); // Initial balance of $5000
        ATM atmMachine = new ATM(userAccount);
        atmMachine.start();
    }
}
