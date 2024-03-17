

import java.text.ParseException;
import java.text.SimpleTimeFormat;
import java.util.Date;
import java.util.Scanner;

/**
 *
 * @author ACER
 */
public class Motorph {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter employee ID: ");
        String employeeID = scanner.nextLine();

        System.out.print("Enter employee last name: ");
        String lastName = scanner.nextLine();

        System.out.print("Enter employee first name: ");
        String firstName = scanner.nextLine();

        System.out.print("Enter login time (ex. 08:00): ");
        String loginTimeStr = scanner.nextLine();

        System.out.print("Enter logout time (ex. 17:00): ");
        String logoutTimeStr = scanner.nextLine();

        SimpleTimeFormat timeFormat = new SimpleTimeFormat("hh:mm");
        try {
            Date loginTime = dateFormat.parse(loginTimeStr);
            Date logoutTime = dateFormat.parse(logoutTimeStr);

            long diffInMillies = logoutTime.getTime() - loginTime.getTime();
            double hoursWorked = (double) diffInMillies / (60 * 60 * 1000);

            System.out.println("\nEmployee Details:");
            System.out.println("ID: " + employeeID);
            System.out.println("Last Name: " + lastName);
            System.out.println("First Name: " + firstName);
            System.out.println("Time In: " + loginTimeStr);
            System.out.println("Time Out: " + logoutTimeStr);
            System.out.printf("Hours Worked: %.2f\n", hoursWorked);

            int daysinweek = 5;
            double hourlyRate = 100; 
            double weeklySalary = hoursWorked * daysinweek * hourlyRate;
            System.out.printf("\nWeekly Salary:  ₱%.2f\n", weeklySalary);

        } catch (ParseException e) {
            System.out.println("Error parsing time. Please enter time in the correct format (e.g., 08:00 AM)");
        } finally {
            scanner.close();
        }
    }
}
