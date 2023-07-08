package com.hrithik;

import java.io.*;
import java.util.*;

class Employee {
    private String id;
    private String name;
    private String designation;
    private double salary;

    public Employee(String id, String name, String designation, double salary) {
        this.id = id;
        this.name = name;
        this.designation = designation;
        this.salary = salary;
    }

    public String getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public String getDesignation() {
        return designation;
    }

    public double getSalary() {
        return salary;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setDesignation(String designation) {
        this.designation = designation;
    }

    public void setSalary(double salary) {
        this.salary = salary;
    }

    @Override
    public String toString() {
        return "ID: " + id + "\nName: " + name + "\nDesignation: " + designation + "\nSalary: " + salary + "\n";
    }
}

class EmployeeManagementSystem {
    private List<Employee> employees;
    private File file;

    public EmployeeManagementSystem(String filePath) {
        employees = new ArrayList<>();
        file = new File(filePath);
        loadEmployees();
    }

    public void addEmployee(Employee employee) {
        employees.add(employee);
        saveEmployees();
        System.out.println("Employee added successfully.");
    }

    public void viewAllEmployees() {
        if (employees.isEmpty()) {
            System.out.println("No employees found.");
        } else {
            System.out.println("Employee List:");
            for (Employee employee : employees) {
                System.out.println(employee);
            }
        }
    }

    public void updateEmployee(String id, String name, String designation, double salary) {
        for (Employee employee : employees) {
            if (employee.getId().equals(id)) {
                employee.setName(name);
                employee.setDesignation(designation);
                employee.setSalary(salary);
                saveEmployees();
                System.out.println("Employee updated successfully.");
                return;
            }
        }
        System.out.println("Employee not found.");
    }

    private void loadEmployees() {
        Scanner scanner = null;
        try {
            scanner = new Scanner(file);
            while (scanner.hasNextLine()) {
                String[] employeeData = scanner.nextLine().split(",");
                String id = employeeData[0];
                String name = employeeData[1];
                String designation = employeeData[2];
                double salary = Double.parseDouble(employeeData[3]);
                employees.add(new Employee(id, name, designation, salary));
            }
        } catch (FileNotFoundException e) {
            System.out.println("Employee data file not found. Starting with an empty employee list.");
        } finally {
            if (scanner != null) {
                scanner.close();
            }
        }
    }

    private void saveEmployees() {
        PrintWriter writer = null;
        try {
            writer = new PrintWriter(file);
            for (Employee employee : employees) {
                writer.println(employee.getId() + "," + employee.getName() + "," +
                        employee.getDesignation() + "," + employee.getSalary());
            }
        } catch (FileNotFoundException e) {
            System.out.println("Error saving employee data.");
        } finally {
            if (writer != null) {
                writer.close();
            }
        }
    }
}

public class Main {
    public static void main(String[] args) {
        EmployeeManagementSystem system = new EmployeeManagementSystem("employees.txt");

        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.println("----- Employee Management System -----");
            System.out.println("1. Add Employee");
            System.out.println("2. View All Employees");
            System.out.println("3. Update Employee");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");

            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter employee ID: ");
                    String id = scanner.nextLine();
                    System.out.print("Enter employee name: ");
                    String name = scanner.nextLine();
                    System.out.print("Enter employee designation: ");
                    String designation = scanner.nextLine();
                    System.out.print("Enter employee salary: ");
                    double salary = scanner.nextDouble();
                    scanner.nextLine(); // Consume newline
                    Employee newEmployee = new Employee(id, name, designation, salary);
                    system.addEmployee(newEmployee);
                    break;
                case 2:
                    system.viewAllEmployees();
                    break;
                case 3:
                    System.out.print("Enter the ID of the employee to update: ");
                    String updateId = scanner.nextLine();
                    System.out.print("Enter updated name: ");
                    String updatedName = scanner.nextLine();
                    System.out.print("Enter updated designation: ");
                    String updatedDesignation = scanner.nextLine();
                    System.out.print("Enter updated salary: ");
                    double updatedSalary = scanner.nextDouble();
                    scanner.nextLine(); // Consume newline
                    system.updateEmployee(updateId, updatedName, updatedDesignation, updatedSalary);
                    break;
                case 4:
                    System.out.println("Exiting...");
                    System.exit(0);
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
                    break;
            }
        }
    }
}

