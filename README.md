# BCA-4C-JAVA
Dear Students, Java first assignment need to complete on time

Encapsulation in Java is the process by which data (variables) and the code that acts upon them (methods) are integrated as a single unit. By encapsulating a class's variables, other classes cannot access them, and only the methods of the class can access them. 
Create a class EMPLOYEE having data members as NameOfEmp, Emp-Id, BasicSalary and GrossSalary. NameOfEmp, Emp-Id, BasicSalary should be entered as user input. Calculate HRA (HRA is 25% of BasicSalary).Also, calculate DA (DA is 40% of BasicSalary). Then, calculate GrossSalary (GrossSalary=BasicSalary+HRA+DA). 
Implement the following queries: 
a) Display the NameOfEmp and GrossSalary of employees whose name starts With a consonent.
b) Display the Emp-Id and GrossSalary of Employees whose Emp-Id is between 101 and 150.
c) Count the total number of Employees whose GrossSalary is less than 35000/-


Namit mehta
2210997150
Bca 4C

import java.util.Scanner;

class EMPLOYEE {
    private String NameOfEmp;
    private int EmpId;
    private double BasicSalary;
    private double GrossSalary;

    public EMPLOYEE(String NameOfEmp, int EmpId, double BasicSalary) {
        this.NameOfEmp = NameOfEmp;
        this.EmpId = EmpId;
        this.BasicSalary = BasicSalary;
        calculateGrossSalary();
    }

    private void calculateGrossSalary() {
        double HRA = 0.25 * BasicSalary;
        double DA = 0.4 * BasicSalary;
        GrossSalary = BasicSalary + HRA + DA;
    }

    public String getNameOfEmp() {
        return NameOfEmp;
    }

    public double getGrossSalary() {
        return GrossSalary;
    }

    public int getEmpId() {
        return EmpId;
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        EMPLOYEE[] employees = new EMPLOYEE[5];

        for (int i = 0; i < employees.length; i++) {
            System.out.println("Enter NameOfEmp for employee " + (i + 1) + ":");
            String name = scanner.nextLine();
            System.out.println("Enter Emp-Id for employee " + (i + 1) + ":");
            int id = Integer.parseInt(scanner.nextLine());
            System.out.println("Enter BasicSalary for employee " + (i + 1) + ":");
            double basicSalary = Double.parseDouble(scanner.nextLine());
            employees[i] = new EMPLOYEE(name, id, basicSalary);
        }

        System.out.println("Employees whose name starts with a consonant:");
        for (EMPLOYEE employee : employees) {
            if (!isVowel(employee.getNameOfEmp().charAt(0))) {
                System.out.println("Name: " + employee.getNameOfEmp() + ", Gross Salary: " + employee.getGrossSalary());
            }
        }

        System.out.println("Employees whose Emp-Id is between 101 and 150:");
        for (EMPLOYEE employee : employees) {
            if (employee.getEmpId() >= 101 && employee.getEmpId() <= 150) {
                System.out.println("Emp-Id: " + employee.getEmpId() + ", Gross Salary: " + employee.getGrossSalary());
            }
        }

        int count = 0;
        for (EMPLOYEE employee : employees) {
            if (employee.getGrossSalary() < 35000) {
                count++;
            }
        }
        System.out.println("Total number of employees whose GrossSalary is less than 35000: " + count);
    }

    private static boolean isVowel(char c) {
        return "aeiouAEIOU".indexOf(c) != -1;
    }
}
