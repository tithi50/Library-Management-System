/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package com.mycompany.librarymanagementsystem2;

/**
 *
 * @author ashim
 */
import java.io.*;
import java.util.*;

public class Library {
    private List<Book> books = new ArrayList<>();
    private final String fileName = "books.txt";

    public Library() {
        loadBooks();
    }

    private void loadBooks() {
        try (BufferedReader br = new BufferedReader(new FileReader(fileName))) {
            String line;
            while ((line = br.readLine()) != null) {
                String[] data = line.split(",");
                books.add(new Book(data[0], data[1], data[2], Boolean.parseBoolean(data[3])));
            }
        } catch (IOException e) {
            System.out.println("File not found, starting with empty library.");
        }
    }

    private void saveBooks() {
        try (BufferedWriter bw = new BufferedWriter(new FileWriter(fileName))) {
            for (Book book : books) {
                bw.write(book.toFileString());
                bw.newLine();
            }
        } catch (IOException e) {
            System.out.println("Error saving books.");
        }
    }

    public void addBook(Book book) {
        books.add(book);
        saveBooks();
    }

    public void issueBook(String bookId) {
        for (Book book : books) {
            if (book.getId().equals(bookId) && !book.isIssued()) {
                book.setIssued(true);
                saveBooks();
                System.out.println("Book issued successfully.");
                return;
            }
        }
        System.out.println("Book not found or already issued.");
    }

    public void returnBook(String bookId) {
        for (Book book : books) {
            if (book.getId().equals(bookId) && book.isIssued()) {
                book.setIssued(false);
                saveBooks();
                System.out.println("Book returned successfully.");
                return;
            }
        }
        System.out.println("Book not found or wasn't issued.");
    }

    public void viewBooks() {
        for (Book book : books) {
            System.out.println(book.getId() + " | " + book.getTitle() + " | " + book.getAuthor() + " | " + (book.isIssued() ? "Issued" : "Available"));
        }
    }
}
