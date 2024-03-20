package projectpayroll;

        import java.text.SimpleDateFormat;
        import java.util.Date;
        import java.util.Scanner;

        
public class payroll {

	public static void main(String[] args) {
		


				Scanner s = new Scanner(System.in);
				SimpleDateFormat dF = new SimpleDateFormat("hh:mm");
				
				String names;
				System.out.print("Employee Name: ");
				names = s.nextLine();
				
				String idNumber;
				System.out.print("Employee ID: ");
				idNumber = s.nextLine();

				String loginTimeStr;
				System.out.print("Login Time(ex. 08:00): ");
				loginTimeStr = s.nextLine();
				
				String logoutTimeStr;
				System.out.print("Logout Time (ex. 17:00): ");
				logoutTimeStr = s.nextLine();
				
				
				try {
					Date LoginTime = dF.parse(loginTimeStr);
					Date logoutTime = dF.parse(logoutTimeStr);
					
					long diffInMillies = logoutTime.getTime() - LoginTime.getTime();
					double hoursWorked = (double) diffInMillies / (60 * 60 * 1000);
					
					System.out.println("\nEmployee Details:");
					System.out.println("Employee Name: " + names);
					System.out.println("Employee ID: " +idNumber);
					System.out.println("Login Time: " +loginTimeStr);
					System.out.println("Logout Time: " +logoutTimeStr);
					System.out.printf("Hours Worked: %.2f\n", hoursWorked - 1);
					
					int daysinweek = 5;
		            double hourlyRate = 100; 
		            double weeklySalary = hoursWorked * daysinweek * hourlyRate;
		            System.out.printf("\nWeekly Salary:  ₱%.2f\n", weeklySalary);
		            
		            double monthlySalary = 18000.00; // Employee's monthly salary
		            double taxRate;

		            if (monthlySalary < 20000.00) {
		                taxRate = 0;
		            } else if (monthlySalary > 20000.00) {
		                taxRate = 0.2;
		            } else {
		                taxRate = 0.3;
		            }

		            double taxDeduction = monthlySalary * taxRate;
		            double pagIbigDeduction = 200.00;
		            double sssDeduction = 800.00;
		            double lunchDeduction = 100.00;

		            // Other deductions...
		            // double otherDeduction = ...

		            double totalDeductions = taxDeduction + pagIbigDeduction + sssDeduction + lunchDeduction;
		            
		            double netPay = monthlySalary - totalDeductions;

		            // Print payslip
		            System.out.println("\nPayslip:");
		            System.out.println("Monthly Salary: ₱" + monthlySalary);
		            System.out.println("Tax Deduction: ₱" + taxDeduction);
		            System.out.println("Pag-IBIG Deduction: ₱" + pagIbigDeduction);
		            System.out.println("SSS Deduction: ₱" + sssDeduction);
		            System.out.println("Lunch Deduction: ₱" + lunchDeduction);
		            System.out.println("Total Deductions: ₱" + totalDeductions);
		            System.out.println("Total Deductions: ₱" + totalDeductions);
		            System.out.println("Net Pay: ₱" + netPay);
		            
		           

				} catch (Exception e) {
					System.out.println("Error. Please enter the correct time format.");
		        } finally {
		            s.close();
		        }		

			}

		
	}



