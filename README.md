# Lab-9

Lab 9

Q1 Comparable interface

Thursday Lab 9

package Lab9;

/*
 * 3.  Create a arraylist of students name and remove name of students who start 
 * with ‘S’ using lambda expression.
 */
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

// Product class implementing Comparable interface
class Product implements Comparable<Product> {
    private String name;
    private double price;

    // Constructor
    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }

    // Getter for name
    public String getName() {
        return name;
    }

    // Getter for price
    public double getPrice() {
        return price;
    }

    // Implementing compareTo method of Comparable interface
    @Override
    public int compareTo(Product other) {
        // Compare based on price
        return Double.compare(this.price, other.price);
    }

    // Overriding toString method for better printing
    @Override
    public String toString() {
        return "Product [name=" + name + ", price=" + price + "]";
    }
}

public class Comparable_interface {
    public static void main(String[] args) {
        // Create a list of products
        List<Product> products = new ArrayList<>();
        products.add(new Product("Laptop", 999.99));
        products.add(new Product("Smartphone", 499.99));
        products.add(new Product("Tablet", 299.99));

        // Print the original list
        System.out.println("Original list of products:");
        for (Product product : products) {
            System.out.println(product);
        }

        // Sort the list using Collections.sort() method (which internally uses compareTo())
        Collections.sort(products);

        // Print the sorted list
        System.out.println("\nSorted list of products based on price:");
        for (Product product : products) {
            System.out.println(product);
        }
    }
}



Q2 Teachers

Thursday Lab 9

package Lab9;
/*
 * 2.   A class teacher has decided to split her entire class into four groups, namely Sapphire, Perl, Ruby, and Emerald for sports competitions. For dividing the students into these four groups, she has followed the pattern given below:
 * Sapphire - 1, 5, 9, 13, 17, 21, ...
 * Perl - 2, 6, 10, 14, 18, 22, ...
 * Ruby - 3, 7, 11, 15, 19, 23, ...
 * Emerald - 4, 8, 12, 16, 20, 24, ...
 */
import java.util.Scanner;

public class Teacher 
{
    // Member variable to store Roll number
    int RollNo;
    // Method to take input from the user
    public void Input() 
    {
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter your Roll no : ");
        RollNo = sc.nextInt(); // Store user input in RollNo variable
        logic(); // Call logic method to determine group
    }
    
    // Method to determine group based on Roll number
    public void logic() 
    {
        // Determine group based on Roll number modulo 4
        if (RollNo % 4 == 1) 
        {
            System.out.println("It belongs to the group Sapphire: ");
        } 
        else if (RollNo % 4 == 2) 
        {
            System.out.println("It belongs to the group Perl : ");
        } 
        else if (RollNo % 4 == 3) 
        {
            System.out.println("It belongs to the group Ruby : ");
        } 
        else if (RollNo % 4 == 0) 
        {
            System.out.println("It belongs to the group Emerald : ");
        }
    }
    
    // Main method to create object of Teacher class and invoke Input method
    public static void main(String[] args) 
    {
        Teacher t = new Teacher(); // Create object of Teacher class
        t.Input(); // Invoke Input method
    }
}


Q3 Lambad 

Thursday lab 9 


package Lab9;
/*
 * Define Product class with name, price,  and sort it price wise 
 * (use comparable interface) .
 */


import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class RemoveStudentsWithS 
{
    public static void main(String[] args) 
    {
        // Create an ArrayList to store student names
        List<String> studentNames = new ArrayList<>();
        // Add some student names to the list
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter the name of Students : ");
        String data="yes";
		while(!data.equalsIgnoreCase("NO"))
		{
			data=sc.next();
			if(data.equalsIgnoreCase("NO"))
			{
				break;
			}
			studentNames.add(data);
		}
        // Print the original list of student names
        System.out.println("Original list of student names: " + studentNames);
        // Remove names of students starting with 'S' using lambda expression
        studentNames.removeIf(name -> name.startsWith("S"));
        studentNames.removeIf(name -> name.startsWith("s"));
        // Print the updated list of student names after removal
        System.out.println("Updated list after removing names starting with 'S': " + studentNames);
    }
}


Q4 BookManagementSystem

Thuradsy lab 9

package Lab9;

/*
 * 4.Write an application to create a book managment system to do the following process :
 * Add book
 * Update book
 * Delete book
 * add author to each by using collection framwork.
 */

import java.util.*;
//Class to represent an autho
class Author 
{
    private String name;

    public Author(String name) 
    {
        this.name = name;
    }

    public String getName() 
    {
        return name;
    }

    @Override
    public String toString() 
    {
        return name;
    }
}

//Class to represent a book
class Book 
{
    private String title;
    private Set<Author> authors;

    public Book(String title) 
    {
        this.title = title;
        this.authors = new HashSet<>();
    }

    public String getTitle() 
    {
        return title;
    }

    public Set<Author> getAuthors() 
    {
        return authors;
    }

    public void addAuthor(Author author) 
    {
        authors.add(author);
    }

    public void removeAuthor(Author author) 
    {
        authors.remove(author);
    }

    @Override
    public String toString() 
    {
        return title + " by " + authors;
    }
}

//Class to manage the book management system
public class BookManagementSystem 
{
    private Map<String, Book> books;// Map to store books with titles as keys
    private Scanner scanner;// Scanner object for user input

    // Constructor to initialize the books map and scanner
    public BookManagementSystem() 
    {
        this.books = new HashMap<>();
        this.scanner = new Scanner(System.in);
    }

    // Method to add a book to the system
    public void addBook() 
    {
        System.out.print("Enter book title: ");
        String title = scanner.nextLine();
        Book book = new Book(title);
        books.put(title, book);
        System.out.println("Book '" + title + "' added successfully.");
    }

    // Method to update a book's title
    public void updateBook() 
    {
        System.out.print("Enter current book title: ");
        String oldTitle = scanner.nextLine();
        if (books.containsKey(oldTitle)) 
        {
            System.out.print("Enter new book title: ");
            String newTitle = scanner.nextLine();
            Book book = books.remove(oldTitle);
            book = new Book(newTitle);
            books.put(newTitle, book);
            System.out.println("Book '" + oldTitle + "' updated to '" + newTitle + "' successfully.");
        } 
        else 
        {
            System.out.println("Book '" + oldTitle + "' not found.");
        }
    }

    // Method to delete a book from the system
    public void deleteBook() 
    {
        System.out.print("Enter book title to delete: ");
        String title = scanner.nextLine();
        if (books.containsKey(title)) 
        {
            books.remove(title);
            System.out.println("Book '" + title + "' deleted successfully.");
        } 
        else 
        {
            System.out.println("Book '" + title + "' not found.");
        }
    }

    // Method to add an author to a book
    public void addAuthorToBook() 
    {
        System.out.print("Enter book title to add author: ");
        String title = scanner.nextLine();
        if (books.containsKey(title)) 
        {
            System.out.print("Enter author name: ");
            String authorName = scanner.nextLine();
            Author author = new Author(authorName);
            Book book = books.get(title);
            book.addAuthor(author);
            System.out.println("Author '" + authorName + "' added to book '" + title + "' successfully.");
        } 
        else 
        {
            System.out.println("Book '" + title + "' not found.");
        }
    }

    // Method to display all books in the system
    public void displayBooks() 
    {
        if (books.isEmpty()) 
        {
            System.out.println("No books in the system.");
        } 
        else 
        {
            System.out.println("Books in the system:");
            for (Book book : books.values()) 
            {
                System.out.println(book);
            }
        }
    }

    public static void main(String[] args) 
    {
        BookManagementSystem system = new BookManagementSystem();
        Scanner scanner = new Scanner(System.in);
        while (true) 
        {
            System.out.println("\nSelect operation:");
            System.out.println("1. Add Book");
            System.out.println("2. Update Book");
            System.out.println("3. Delete Book");
            System.out.println("4. Add Author to Book");
            System.out.println("5. Display Books");
            System.out.println("6. Exit");

            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline

            switch (choice) 
            {
                case 1:
                    system.addBook();
                    break;
                case 2:
                    system.updateBook();
                    break;
                case 3:
                    system.deleteBook();
                    break;
                case 4:
                    system.addAuthorToBook();
                    break;
                case 5:
                    system.displayBooks();
                    break;
                case 6:
                    System.out.println("Exiting...");
                    scanner.close();
                    System.exit(0);
                default:
                    System.out.println("Invalid choice.");
            }
        }
    }
}


Q5 HashMap_Cube

Thursday lab 9

package Lab9;

/*
 * 5. Create hash map whose keys are1 to 15 and its values cube of keys.
 */

import java.util.HashMap;
import java.util.Map;

public class HashMap_Cube 
{
    public static void main(String[] args) 
    {
        // Create a HashMap to store the cubes of keys
        Map<Integer, Integer> cubeMap = new HashMap<>();
        // Populate the map with keys from 1 to 15 and their cubes as values
        for (int i = 1; i <= 15; i++) 
        {
            cubeMap.put(i, i * i * i);
        }

        // Print the HashMap
        System.out.println("HashMap with keys and their cubes:");
        for (Map.Entry<Integer, Integer> entry : cubeMap.entrySet()) 
        {
            System.out.println("Key: " + entry.getKey() + ", Cube: " + entry.getValue());
        }
    }
}


Q5 DoctorManagement

Thursday Lab 9

package Lab9;

/*
 * 6.Create arraylist of doctor(id,name,specility) and generate 
 * addDoctor(),displayDoctors(),updateDoctor() methods.
 */

import java.util.ArrayList;
import java.util.Scanner;

// Doctor class to represent doctors
class Doctor {
    private int id;
    private String name;
    private String specialty;

    // Constructor
    public Doctor(int id, String name, String specialty) {
        this.id = id;
        this.name = name;
        this.specialty = specialty;
    }

    // Getter methods
    public int getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public String getSpecialty() {
        return specialty;
    }

    // Setter methods
    public void setName(String name) {
        this.name = name;
    }

    public void setSpecialty(String specialty) {
        this.specialty = specialty;
    }

    // Override toString() method for better printing
    @Override
    public String toString() {
        return "Doctor [id=" + id + ", name=" + name + ", specialty=" + specialty + "]";
    }
}

// DoctorManagement class to manage doctors
public class DoctorManagement 
{
    private ArrayList<Doctor> doctors;
    // Constructor
    public DoctorManagement() 
    {
        doctors = new ArrayList<>();
    }
    // Method to add a doctor
    public void addDoctor(int id, String name, String specialty) 
    {
        Doctor doctor = new Doctor(id, name, specialty);
        doctors.add(doctor);
        System.out.println("Doctor added successfully.");
    }
    // Method to display all doctors
    public void displayDoctors() 
    {
        if (doctors.isEmpty()) 
        {
            System.out.println("No doctors to display.");
        } 
        else 
        {
            System.out.println("List of doctors:");
            for (Doctor doctor : doctors) 
            {
                System.out.println(doctor);
            }
        }
    }

    // Method to update doctor's information
    public void updateDoctor(int id, String name, String specialty) 
    {
        for (Doctor doctor : doctors) 
        {
            if (doctor.getId() == id) 
            {
                doctor.setName(name);
                doctor.setSpecialty(specialty);
                System.out.println("Doctor information updated successfully.");
                return;
            }
        }
        System.out.println("Doctor with ID " + id + " not found.");
    }

    public static void main(String[] args) 
    {
        DoctorManagement doctorManagement = new DoctorManagement();
        Scanner scanner = new Scanner(System.in);

        // Menu for operations
        while (true) 
        {
            System.out.println("\nSelect operation:");
            System.out.println("1. Add Doctor");
            System.out.println("2. Display Doctors");
            System.out.println("3. Update Doctor");
            System.out.println("4. Exit");

            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline

            switch (choice) 
            {
                case 1:
                    System.out.println("Enter doctor ID:");
                    int id = scanner.nextInt();
                    scanner.nextLine(); // Consume newline
                    System.out.println("Enter doctor name:");
                    String name = scanner.nextLine();
                    System.out.println("Enter doctor specialty:");
                    String specialty = scanner.nextLine();
                    doctorManagement.addDoctor(id, name, specialty);
                    break;
                case 2:
                    doctorManagement.displayDoctors();
                    break;
                case 3:
                    System.out.println("Enter doctor ID to update:");
                    int updateId = scanner.nextInt();
                    scanner.nextLine(); // Consume newline
                    System.out.println("Enter new name:");
                    String newName = scanner.nextLine();
                    System.out.println("Enter new specialty:");
                    String newSpecialty = scanner.nextLine();
                    doctorManagement.updateDoctor(updateId, newName, newSpecialty);
                    break;
                case 4:
                    System.out.println("Exiting...");
                    scanner.close();
                    System.exit(0);
                default:
                    System.out.println("Invalid choice.");
            }
        }
    }
}

