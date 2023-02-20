```
iimport java.util.ArrayList;
import java.util.Scanner;

public class BankManagementSystem {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Account> accounts = new ArrayList<>();

        while (true) {
            System.out.println("Welcome to Bank Management System");
            System.out.println("1. Create account");
            System.out.println("2. Deposit money");
            System.out.println("3. Withdraw money");
            System.out.println("4. View account balance");
            System.out.println("5. Exit");

            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    createAccount(accounts, scanner);
                    break;
                case 2:
                    depositMoney(accounts, scanner);
                    break;
                case 3:
                    withdrawMoney(accounts, scanner);
                    break;
                case 4:
                    viewBalance(accounts, scanner);
                    break;
                case 5:
                    System.out.println("Thank you for using Bank Management System");
                    return;
                default:
                    System.out.println("Invalid choice. Please try again.");
                    break;
            }
        }
    }

    private static void createAccount(ArrayList<Account> accounts, Scanner scanner) {
        System.out.print("Enter account holder name: ");
        String accountHolderName = scanner.next();

        System.out.print("Enter account type (Savings or Current): ");
        String accountType = scanner.next();

        System.out.print("Enter initial deposit amount: ");
        double initialDeposit = scanner.nextDouble();

        Account account = new Account(accountHolderName, accountType, initialDeposit);
        accounts.add(account);

        System.out.println("Account created successfully with account number " + account.getAccountNumber());
    }

    private static void depositMoney(ArrayList<Account> accounts, Scanner scanner) {
        System.out.print("Enter account number: ");
        int accountNumber = scanner.nextInt();

        Account account = findAccount(accounts, accountNumber);

        if (account == null) {
            System.out.println("Account not found. Please try again.");
            return;
        }

        System.out.print("Enter deposit amount: ");
        double depositAmount = scanner.nextDouble();

        account.deposit(depositAmount);
        System.out.println("Deposit successful. New balance is " + account.getBalance());
    }

    private static void withdrawMoney(ArrayList<Account> accounts, Scanner scanner) {
        System.out.print("Enter account number: ");
        int accountNumber = scanner.nextInt();

        Account account = findAccount(accounts, accountNumber);

        if (account == null) {
            System.out.println("Account not found. Please try again.");
            return;
        }

        System.out.print("Enter withdraw amount: ");
        double withdrawAmount = scanner.nextDouble();

        boolean success = account.withdraw(withdrawAmount);

        if (success) {
            System.out.println("Withdrawal successful. New balance is " + account.getBalance());
        } else {
            System.out.println("Insufficient balance. Please try again.");
        }
    }

    private static void viewBalance(ArrayList<Account> accounts, Scanner scanner) {
        System.out.print("Enter account number: ");
        int accountNumber = scanner.nextInt();

        Account account = findAccount(accounts, accountNumber);

        if (account == null) {
            System.out.println("Account not found. Please try again.");
            return;
        }

        System.out.println("Account balance is " + account.getBalance());
    }

    private static Account findAccount(ArrayList<Account> accounts, int accountNumber) {
        for (Account account : accounts) {
            if (account.getAccountNumber() == accountNumber) {
                return account;
            }
        }

        return
```
