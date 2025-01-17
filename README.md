Unit Converter and Expense Management Application
Overview
This Java console application provides two core functionalities:

Unit Conversion: Convert between different units of measurement, such as:
Length (Meters to Kilometers)
Weight (Kilograms to Pounds)
Temperature (Celsius to Fahrenheit)
Expense Management: Allows the user to manage personal expenses by performing the following actions:
Add new expenses
Edit existing expenses
Delete expenses
View all expenses
The application stores all conversion and expense data locally in an SQLite database.

Technologies Used
Java: Core programming language.
SQLite: Local database for storing conversions and expenses.
JDBC: For database interactions.
Apache POI (optional): For generating Excel reports (if integrated).
Swing (optional): For GUI (if integrated, though this app is CLI by default).
Features
Unit Conversion:

Convert Length (Meters to Kilometers)
Convert Weight (Kilograms to Pounds)
Convert Temperature (Celsius to Fahrenheit)
Save conversion results to the database for future reference.
Expense Management:

Add expenses with descriptions, amounts, and categories.
Edit or delete existing expenses.
View all expenses stored in the database.
Database:

SQLite database stores expenses and unit conversion records persistently.
Getting Started
System Requirements
Java 8 or higher installed.
SQLite JDBC Driver (included in the project dependencies).
SQLite database file (expense_conversion.db).
Installation
Clone the repository or download the project files.

Database Setup:

Make sure the SQLite database is properly created. If you have not already, you can run the following SQL queries to set up the database:
sql
Copy code
CREATE TABLE expenses (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    description TEXT,
    amount REAL,
    category TEXT,
    date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE conversions (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    conversion_type TEXT,
    input_value REAL,
    converted_value REAL,
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
Dependencies:

If you are using Maven, the dependencies will be automatically handled. Otherwise, make sure to include the necessary SQLite JDBC Driver and Apache POI JAR files in your project classpath.

SQLite JDBC Driver: SQLite JDBC Download.

Apache POI (optional for Excel export): Apache POI Download.

Compiling and Running the Application:

To compile the code, navigate to the project folder and run:
bash
Copy code
javac -d bin src/*.java
To run the application from the command line:
bash
Copy code
java -cp bin MainApp
Alternatively, you can package the application into a JAR file for easy execution.

bash
Copy code
jar cfm ExpenseManagerApp.jar META-INF/MANIFEST.MF -C bin/ .
Then, run the application with:

bash
Copy code
java -jar ExpenseManagerApp.jar
Configuration
The database file expense_conversion.db will be created automatically when you run the application for the first time. You don't need to manually create the database unless you are setting it up on a new machine.

The application will prompt you in the console for selecting operations like unit conversion or expense management.

Usage
After running the application, you will interact with the program through the console. The program presents a menu with the following options:

1. Unit Conversion
Step 1: Choose a conversion type:

Length (meters to kilometers)
Weight (kilograms to pounds)
Temperature (Celsius to Fahrenheit)
Step 2: Enter the value to be converted.

Step 3: The program will display the converted value and save the conversion in the database.

2. Expense Management
The expense management system allows you to:

Add Expenses:

Enter a description, amount, and category (e.g., Food, Transport, etc.).
Edit Expenses:

Modify existing expenses by providing the expense ID.
Delete Expenses:

Remove an expense from the database using its ID.
View All Expenses:

Display all stored expenses, including description, amount, category, and date.
3. Exit
Exits the program.
Example
Here is an example of the user interaction:

vbnet
Copy code
Welcome to the Unit Converter and Expense Manager!
1. Unit Conversion
2. Manage Expenses
3. Exit
Choose an option: 1

Choose Conversion Type:
1. Length (meters to kilometers)
2. Weight (kilograms to pounds)
3. Temperature (Celsius to Fahrenheit)
Choose an option: 1
Enter value to convert: 1500
Converted value: 1.5
In this example, a length of 1500 meters is converted to 1.5 kilometers and saved in the database.

Database Schema
expenses table
id: Integer (Primary Key)
description: Text (Expense Description)
amount: Real (Amount Spent)
category: Text (Expense Category)
date: Timestamp (Date of Expense)
conversions table
id: Integer (Primary Key)
conversion_type: Text (Type of Conversion: Length, Weight, Temperature)
input_value: Real (Input Value for Conversion)
converted_value: Real (Converted Value)
timestamp: Timestamp (Date of Conversion)
Optional Features (If Integrated)
Generating Excel Reports
The application can optionally generate Excel reports for all expenses using Apache POI. This feature can be added by calling a method to export expenses from the database to an .xlsx file.

Export/Import Expense Data (JSON/XML)
If desired, you can implement JSON/XML export and import functionality for backup and sharing of expenses.

Troubleshooting
SQLite Database Issues: If the database file is not created automatically, make sure the JDBC connection is configured correctly.
Dependencies: Ensure that all required dependencies are included, especially the SQLite JDBC driver.
Invalid Input: If the user enters an invalid number or value, the program will prompt them again.
