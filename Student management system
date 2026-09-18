import java.io.*;
import java.util.*;

public class Main {

    static Scanner sc = new Scanner(System.in);
    static ArrayList<Student> students = new ArrayList<>();
    static final String FILE = "students.txt";

    // Student class
    static class Student {
        int id;
        String name;
        String course;
        double marks;

        Student(int id, String name, String course, double marks) {
            this.id = id;
            this.name = name;
            this.course = course;
            this.marks = marks;
        }

        String getGrade() {
            if (marks >= 90) return "A+";
            if (marks >= 80) return "A";
            if (marks >= 70) return "B";
            if (marks >= 60) return "C";
            if (marks >= 50) return "D";
            return "F";
        }

        public String toString() {
            return "ID: " + id +
                   " | Name: " + name +
                   " | Course: " + course +
                   " | Marks: " + marks +
                   " | Grade: " + getGrade();
        }
    }

    public static void main(String[] args) {

        loadData();

        System.out.println("======================================");
        System.out.println("      STUDENT MANAGEMENT SYSTEM");
        System.out.println("======================================");

        while (true) {

            System.out.println("\n1. Add Student");
            System.out.println("2. View Students");
            System.out.println("3. Search Student");
            System.out.println("4. Delete Student");
            System.out.println("5. Performance Report");
            System.out.println("6. Save & Exit");

            System.out.print("\nEnter your choice: ");

            try {
                int choice = Integer.parseInt(sc.nextLine());

                switch (choice) {

                    case 1:
                        addStudent();
                        break;

                    case 2:
                        viewStudents();
                        break;

                    case 3:
                        searchStudent();
                        break;

                    case 4:
                        deleteStudent();
                        break;

                    case 5:
                        performanceReport();
                        break;

                    case 6:
                        saveData();
                        System.out.println(
                            "\nData saved successfully."
                        );
                        System.out.println(
                            "Thank you for using the system!"
                        );
                        return;

                    default:
                        System.out.println(
                            "Invalid choice. Please choose 1-6."
                        );
                }

            } catch (NumberFormatException e) {
                System.out.println(
                    "Please enter a valid number."
                );
            }
        }
    }

    // Add student
    static void addStudent() {

        try {
            System.out.print("Enter Student ID: ");
            int id = Integer.parseInt(sc.nextLine());

            // Check duplicate ID
            for (Student s : students) {
                if (s.id == id) {
                    System.out.println(
                        "Student ID already exists!"
                    );
                    return;
                }
            }

            System.out.print("Enter Student Name: ");
            String name = sc.nextLine();

            if (name.trim().isEmpty()) {
                System.out.println(
                    "Name cannot be empty."
                );
                return;
            }

            System.out.print("Enter Course: ");
            String course = sc.nextLine();

            if (course.trim().isEmpty()) {
                System.out.println(
                    "Course cannot be empty."
                );
                return;
            }

            System.out.print("Enter Marks (0-100): ");
            double marks = Double.parseDouble(sc.nextLine());

            if (marks < 0 || marks > 100) {
                System.out.println(
                    "Marks must be between 0 and 100."
                );
                return;
            }

            students.add(
                new Student(id, name, course, marks)
            );

            System.out.println(
                "Student added successfully!"
            );

        } catch (NumberFormatException e) {

            System.out.println(
                "Invalid input. Please enter correct values."
            );
        }
    }

    // View students
    static void viewStudents() {

        System.out.println("\n========== ALL STUDENTS ==========");

        if (students.isEmpty()) {
            System.out.println(
                "No student records found."
            );
            return;
        }

        for (Student s : students) {
            System.out.println(s);
        }
    }

    // Search student
    static void searchStudent() {

        try {
            System.out.print("Enter Student ID: ");
            int id = Integer.parseInt(sc.nextLine());

            for (Student s : students) {

                if (s.id == id) {

                    System.out.println(
                        "\nStudent Found:"
                    );

                    System.out.println(s);
                    return;
                }
            }

            System.out.println(
                "Student not found."
            );

        } catch (NumberFormatException e) {

            System.out.println(
                "Invalid Student ID."
            );
        }
    }

    // Delete student
    static void deleteStudent() {

        try {
            System.out.print(
                "Enter Student ID to delete: "
            );

            int id = Integer.parseInt(sc.nextLine());

            Iterator<Student> iterator =
                students.iterator();

            while (iterator.hasNext()) {

                Student s = iterator.next();

                if (s.id == id) {

                    iterator.remove();

                    System.out.println(
                        "Student deleted successfully!"
                    );

                    return;
                }
            }

            System.out.println(
                "Student not found."
            );

        } catch (NumberFormatException e) {

            System.out.println(
                "Invalid Student ID."
            );
        }
    }

    // Performance report
    static void performanceReport() {

        if (students.isEmpty()) {

            System.out.println(
                "No student records available."
            );

            return;
        }

        System.out.println(
            "\n====== PERFORMANCE REPORT ======"
        );

        double total = 0;
        Student topStudent = students.get(0);

        for (Student s : students) {

            total += s.marks;

            if (s.marks > topStudent.marks) {
                topStudent = s;
            }
        }

        double average =
            total / students.size();

        System.out.println(
            "Total Students: " + students.size()
        );

        System.out.printf(
            "Average Marks: %.2f%n",
            average
        );

        System.out.println(
            "Top Student: " +
            topStudent.name
        );

        System.out.println(
            "Top Marks: " +
            topStudent.marks
        );

        System.out.println(
            "\nStudent Grades:"
        );

        for (Student s : students) {
            System.out.println(
                s.name + " -> " + s.getGrade()
            );
        }
    }

    // Save data to file
    static void saveData() {

        try {

            BufferedWriter writer =
                new BufferedWriter(
                    new FileWriter(FILE)
                );

            for (Student s : students) {

                writer.write(
                    s.id + "," +
                    s.name + "," +
                    s.course + "," +
                    s.marks
                );

                writer.newLine();
            }

            writer.close();

        } catch (IOException e) {

            System.out.println(
                "Error saving data."
            );
        }
    }

    // Load data from file
    static void loadData() {

        File file = new File(FILE);

        if (!file.exists()) {
            return;
        }

        try {

            BufferedReader reader =
                new BufferedReader(
                    new FileReader(FILE)
                );

            String line;

            while ((line = reader.readLine()) != null) {

                String[] data =
                    line.split(",");

                if (data.length == 4) {

                    int id =
                        Integer.parseInt(data[0]);

                    String name = data[1];
                    String course = data[2];

                    double marks =
                        Double.parseDouble(data[3]);

                    students.add(
                        new Student(
                            id,
                            name,
                            course,
                            marks
                        )
                    );
                }
            }

            reader.close();

        } catch (Exception e) {

            System.out.println(
                "Could not load previous data."
            );
        }
    }
}
