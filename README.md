# Exception-handling
package exception.handling;

class InvalidInputException extends Exception {
public InvalidInputException(String message) {
super(message);
}
}
// Custom exception for negative numbers
class NegativeNumberException extends Exception {
public NegativeNumberException(String message) {
super(message);
}
}
// Custom exception for an unknown operator
class InvalidOperatorException extends Exception {
public InvalidOperatorException(String message) {
super(message);
}
}
// Custom exception for unsupported operations
class UnsupportedOperationException extends Exception {
public UnsupportedOperationException(String message) {
super(message);
}
}
// Calculator class
class Calculator {
public static double performOperation(double num1, double num2, char operator)
throws InvalidInputException, NegativeNumberException,
InvalidOperatorException, UnsupportedOperationException {
if (num1 < 0 || num2 < 0) {

throw new NegativeNumberException("Negative numbers are not allowed.");
}
switch (operator) {
case '+':
return num1 + num2;
case '-':
return num1 - num2;
case'*':
return num1 * num2;
case '/':
if (num2 == 0) {
throw new UnsupportedOperationException("Cannot divide by zero.");
}
return num1 / num2;
default:
throw new InvalidOperatorException("Invalid operator: "+ operator);
}
}
}
// Main class for testing the calculator
public class ExtendedCalculator {
public static void main(String[] args) {
// Test the calculator with exception handling
try {
double result1 = Calculator.performOperation(10, 2, '+');
System.out.println("Result 1: " + result1);
double result2 = Calculator.performOperation(8, 0, '/'); // This will trigger

System.out.println("Result 2: " + result2); 
} catch (InvalidInputException | NegativeNumberException |
InvalidOperatorException | UnsupportedOperationException e) {
System.out.println("Exception: "+ e.getMessage());
}

}
}
OUTPUT:
Result 1: 12.0
Exception: Cannot divide by zero.
BUILD SUCCESSFUL (total time: 0 seconds)


