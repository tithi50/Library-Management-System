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

public class UserManager {
    private final String userFile = "users.txt";
    private List<User> users = new ArrayList<>();

    public UserManager() {
        loadUsers();
    }

    private void loadUsers() {
        try (BufferedReader br = new BufferedReader(new FileReader(userFile))) {
            String line;
            while ((line = br.readLine()) != null) {
                String[] data = line.split(",");
                users.add(new User(data[0], data[1]));
            }
        } catch (IOException e) {
            System.out.println("User file not found. Starting with no users.");
        }
    }

    private void saveUsers() {
        try (BufferedWriter bw = new BufferedWriter(new FileWriter(userFile))) {
            for (User user : users) {
                bw.write(user.toFileString());
                bw.newLine();
            }
        } catch (IOException e) {
            System.out.println("Error saving users.");
        }
    }

    public boolean registerUser(String username, String password) {
        for (User u : users) {
            if (u.getUsername().equals(username)) {
                System.out.println("Username already exists.");
                return false;
            }
        }
        users.add(new User(username, password));
        saveUsers();
        System.out.println("User registered successfully.");
        return true;
    }

    public boolean loginUser(String username, String password) {
        for (User u : users) {
            if (u.getUsername().equals(username) && u.getPassword().equals(password)) {
                return true;
            }
        }
        return false;
    }
}
