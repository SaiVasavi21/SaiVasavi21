#task1
#codsoft
#NUMBER GAME
import java.util.Scanner;
import java.util.Random;
public class task1 {
    public static void main(String args[])
{
generateRandom();
}
public static void generateRandom()
{
Random rand=new Random();
int randomNum=rand.nextInt(11);
guess(randomNum);
}
public static void guess(int randomNum)
{
Scanner sc=new Scanner(System.in);
System.out.println("");
System.out.println("Number Guessing Game");
System.out.println("Guess a number between 0-10:");
int guess=sc.nextInt();
System.out.println("");
while(guess<0|| guess>10)
{
System.out.print("guess a number between 0-10: ");
guess=sc.nextInt();
System.out.println("");
}
int tries=0;
while(guess!=randomNum)
{
tries++;
System.out.println("Wrong Guess");
System.out.print("Guess again:");
guess=sc.nextInt();
System.out.println("");
while(guess<0|| guess>10)
{
System.out.print("guess a number between 0-10: ");
guess=sc.nextInt();
System.out.println("");
}

}
System.out.println("Correct answer,You Won!");

System.out.println("Wrong tries:"+tries);

System.out.println(" ");
System.out.println("Press  1 to play again.");
System.out.println("Press 0 to exist.");
int choice=sc.nextInt();
if(choice==1)
    generateRandom();
else
    return;
}
}




#task_2
#codsoft
#STUDENT GRADE CALCULATION

import java.util.*;

public class task2 {
    public static void main(String args[])
    {
        Scanner sc=new Scanner(System.in);
        System.out.println("Eneter the numebr of subjects: ");
        int num=sc.nextInt();
        int[] marks=new int[num];
        for(int i=0;i<num;i++)
        {
            System.out.println("Enetr the marks for subject"+(i+1)+":");
            marks[i]=sc.nextInt();
            
        }
        int totalmarks=0;
        for(int mark:marks)
        {
            totalmarks+=mark;
        }
        double averagepercentage=(double) totalmarks/num;
        String grade="";
        if(averagepercentage>=90)
        {
            grade="A";
        }
        else if(averagepercentage>=80)
        {
            grade="B";
        }
        else if(averagepercentage>=70)
        {
            grade="C";
        }
        else if(averagepercentage>=60)
        {
            grade="D";
        }
        else
        {
            grade="F";
        }
        System.out.println("Total Marks:"+totalmarks);
        System.out.println("Average Percentage: "+averagepercentage);
        System.out.println("GRADE: "+grade);
    }
}



#task_3
#codsoft
#ATM INTERFACE


import java.util.*;
public class task3 {
    public static void  main(String args[])
    {
        int balance=5000,withdraw,deposite;
        Scanner sc=new Scanner(System.in);
        while(true)
        {
            System.out.println("Automated teller machine");
            System.out.println("Choose 1 for withdraw");
             System.out.println("Choose 2 for Deposite");
              System.out.println("Choose 3 for Check Balance");
               System.out.println("Choose 4 for EXIT");
                System.out.println("Choose the operation you want to perform:");
                int n=sc.nextInt();
                switch(n)
                {
                    case 1:
                         System.out.println("Enetr money to be withdraw:");
                         withdraw=sc.nextInt();
                         if(balance>=withdraw)
                         {
                             balance=balance-withdraw;
                              System.out.println("Please collect your money");
                              
                         }
                         else
                         {
                              System.out.println("Insufficient Balance");
                         }
                          System.out.println(" ");
                          break;
                    case 2:
                        System.out.print("Eneter money to be depoosited:");
                        deposite=sc.nextInt();
                        balance=balance+deposite;
                         System.out.println("Your money has been successfully deposited");
                          System.out.println(" ");
                          break;
                    case 3:
                         System.out.println("Balance :"+balance);
                          System.out.println(" ");
                          break;
                    case 4:
                         System.exit(0);
                }
        }
    }}


#task_5
#codsoft
#STUDEN MANAGEMENT SYSTEM




import java.io.*;
import java.util.ArrayList;
import java.util.List;
import java.util.*;
class Student
{
    private String name;
    private int rollNumber;
    private String grade;
    public Student(String name,int rollNumber,String grade)
    {
        this.name=name;
        this.rollNumber=rollNumber;
        this.grade=grade;
    }
    public String getName()
    {
        return name;
    }
    public int getRollNumber()
    {
        return rollNumber;
    }
    public String getGrade()
    {
        return grade;
    }
    @Override
    public String toString()
    {
        return "Name: " +name + ",Roll Number :" +rollNumber+",Grade: " +grade;
    }
}
class StudentManagementSystem
{
    private List<Student> students=new ArrayList<>();
    public void addStudent(Student student)
    {
        students.add(student);
    }
    public void removeStudent(int rollNumber)
    {
        students.removeIf(student -> student.getRollNumber() == rollNumber);
    }
    public Student findStudent(int rollNumber)
    {
        for(Student student : students)
        {
            if(student.getRollNumber() == rollNumber)
            {
                return student;
            }
        }
        return null;
    }
    public List<Student>getAllStudents()
    {
        return students;
    }
            public void saveToFile(String filename)
            {
                        try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream(filename))) {

                   oos.writeObject(students);
            }
                catch(IOException  e)
                {
                    e.printStackTrace();
                }
}
            public void loadFromFile(String filename)
            {
                try(ObjectInputStream ois=new ObjectInputStream(new FileInputStream(filename)))
                {
                    students = (List<Student>) ois.readObject();
                }
                catch (IOException | ClassNotFoundException e)
                {
                    e.printStackTrace();
                }
            }
}
public class task4 {
     public static void main(String[] args) {
        StudentManagementSystem sms = new StudentManagementSystem();
        Scanner sc= new Scanner(System.in);

        while(true)
        {
           System.out.println("Student Management System");
           System.out.println("1. Add Student");
           System.out.println("2. Remove Student");
           System.out.println("3. Search Student ");
           System.out.println("4. Display All Students");
           System.out.println("5. Save to File");
           System.out.println("7. Exit");
           System.out.println("Select an option: ");
           
           int choice=sc.nextInt();
           sc.nextLine();
            switch (choice) {
                case 1:
                    System.out.print("Enter name: ");
                    String name = sc.nextLine();
                    System.out.print("Enter roll number: ");
                    int rollNumber = sc.nextInt();
                    sc.nextLine(); 
                    System.out.print("Enter grade: ");
                    String grade = sc.nextLine();

                    Student student = new Student(name, rollNumber, grade);
                    sms.addStudent(student);
                    break;
                case 2:
                    System.out.print("Enter roll number to remove: ");
                    int rollToRemove = sc.nextInt();
                    sc.nextLine(); 
                    sms.removeStudent(rollToRemove);
                    break;
                case 3:
                    System.out.print("Enter roll number to search: ");
                    int rollToSearch = sc.nextInt();
                    sc.nextLine(); 
                    Student foundStudent = sms.findStudent(rollToSearch);
                    if (foundStudent != null) {
                        System.out.println("Student found: " + foundStudent);
                    } else {
                        System.out.println("Student not found.");
                    }
                    break;
                case 4:
                    List<Student> allStudents = sms.getAllStudents();
                    if (allStudents.isEmpty()) {
                        System.out.println("No students in the system.");
                    } else {
                        for (Student s : allStudents) {
                            System.out.println(s);
                        }
                    }
                    break;
                case 5:
                    sms.saveToFile("students.dat");
                    System.out.println("Data saved to file.");
                    break;
                case 6:
                    sms.loadFromFile("students.dat");
                    System.out.println("Data loaded from file.");
                    break;
                case 7:
                    System.out.println("Exiting application.");
                    sc.close();
                    System.exit(0);
                    break;
                default:
                    System.out.println("Invalid option. Please try again.");
            }
        }
    }
}

