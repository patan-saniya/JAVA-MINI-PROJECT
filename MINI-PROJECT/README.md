## Title: To write a java code on Library Management System(file-based)
## Source Code:
## Book.java:
``` java
public class Book {
    int id;
    String title;
    boolean available;

    public Book(int id, String title) {
        this.id = id;
        this.title = title;
        this.available = true;
    }
}
```
## Library.java:
``` java
import java.util.ArrayList;

public class Library {
    ArrayList<Book> books = new ArrayList<>();

    public void addBook(int id, String title) {
        books.add(new Book(id, title));
        System.out.println("Book added successfully!");
    }

    public void viewBooks() {
        for (Book b : books) {
            System.out.println(b.id + " - " + b.title + " - " + (b.available ? "Available" : "Issued"));
        }
    }

    public void issueBook(int id) {
        for (Book b : books) {
            if (b.id == id && b.available) {
                b.available = false;
                System.out.println("Book issued!");
                return;
            }
        }
        System.out.println("Book not available!");
    }

    public void returnBook(int id) {
        for (Book b : books) {
            if (b.id == id && !b.available) {
                b.available = true;
                System.out.println("Book returned!");
                return;
            }
        }
        System.out.println("Invalid book ID!");
    }
}

```
## LibrarySystem.java:
``` java
import java.util.Scanner;

public class LibrarySystem {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Library lib = new Library();

        while (true) {
            System.out.println("\n--- Library Management System ---");
            System.out.println("1. Add Book");
            System.out.println("2. View Books");
            System.out.println("3. Issue Book");
            System.out.println("4. Return Book");
            System.out.println("5. Exit");

            System.out.print("Enter choice: ");
            int choice = sc.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter Book ID: ");
                    int id = sc.nextInt();
                    sc.nextLine();
                    System.out.print("Enter Book Title: ");
                    String title = sc.nextLine();
                    lib.addBook(id, title);
                    break;

                case 2:
                    lib.viewBooks();
                    break;

                case 3:
                    System.out.print("Enter Book ID to issue: ");
                    lib.issueBook(sc.nextInt());
                    break;

                case 4:
                    System.out.print("Enter Book ID to return: ");
                    lib.returnBook(sc.nextInt());
                    break;

                case 5:
                    System.out.println("Exiting...");
                    System.exit(0);

                default:
                    System.out.println("Invalid choice!");
            }
        }
    }
}
```
## OUTPUT:
![OUTPUT](output.PNG)



