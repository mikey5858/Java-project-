import java.util.Scanner;

public class SimpleLibrary {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

  String[] books = {"Java Programming", "Data Structures", "Database Systems"};
        boolean[] isAvailable = {true, true, true};
        int choice;

   do {
            System.out.println("\n===== LIBRARY MANAGEMENT SYSTEM =====");
            System.out.println("1. Display Books");
            System.out.println("2. Borrow Book");
            System.out.println("3. Return Book");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            choice = sc.nextInt();

  switch (choice) {
                case 1:
                    System.out.println("\nAvailable Books:");
                    for (int i = 0; i < books.length; i++) {
                        System.out.println((i + 1) + ". " + books[i] + " - " +
                                (isAvailable[i] ? "Available" : "Borrowed"));
                    }
                    break;

  case 2:
                    System.out.print("Enter book number to borrow: ");
                    int borrow = sc.nextInt();
                    if (borrow >= 1 && borrow <= books.length) {
                        if (isAvailable[borrow - 1]) {
                            isAvailable[borrow - 1] = false;
                            System.out.println("You borrowed " + books[borrow - 1]);
                        } else {
                            System.out.println("Sorry, that book is already borrowed!");
                        }
                    } else {
                        System.out.println("Invalid book number!");
                    }
                    break;

  case 3:
                    System.out.print("Enter book number to return: ");
                    int ret = sc.nextInt();
                    if (ret >= 1 && ret <= books.length) {
                        if (!isAvailable[ret - 1]) {
                            isAvailable[ret - 1] = true;
                            System.out.println("You returned " + books[ret - 1]);
                        } else {
                            System.out.println("That book was not borrowed!");
                        }
                    } else {
                        System.out.println("Invalid book number!");
                    }
                    break;

   case 4:
                    System.out.println("Thank you for using the Library System!");
                    break;

  default:
                    System.out.println("Invalid choice, please try again!");
            }
        } while (choice != 4);

   sc.close();
    }
}
