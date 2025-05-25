import java.util.Scanner;

class Complex {
    double real, imag;

    Complex(double r, double i) {
        real = r;
        imag = i;
    }

    public String toString() {
        return real + " + " + imag + "i";
    }
}

class ScientificCalculator {

    // Integer operations
    int add(int a, int b) { return a + b; }
    int subtract(int a, int b) { return a - b; }
    int multiply(int a, int b) { return a * b; }
    int divide(int a, int b) { return a / b; }

    // Float operations
    float add(float a, float b) { return a + b; }
    float subtract(float a, float b) { return a - b; }
    float multiply(float a, float b) { return a * b; }
    float divide(float a, float b) { return a / b; }

    // Complex operations
    Complex add(Complex a, Complex b) {
        return new Complex(a.real + b.real, a.imag + b.imag);
    }

    Complex subtract(Complex a, Complex b) {
        return new Complex(a.real - b.real, a.imag - b.imag);
    }

    Complex multiply(Complex a, Complex b) {
        double real = a.real * b.real - a.imag * b.imag;
        double imag = a.real * b.imag + a.imag * b.real;
        return new Complex(real, imag);
    }

    Complex divide(Complex a, Complex b) {
        double denom = b.real * b.real + b.imag * b.imag;
        double real = (a.real * b.real + a.imag * b.imag) / denom;
        double imag = (a.imag * b.real - a.real * b.imag) / denom;
        return new Complex(real, imag);
    }

    // Trigonometric operations
    double sin(float angle) { return Math.sin(Math.toRadians(angle)); }
    double cos(float angle) { return Math.cos(Math.toRadians(angle)); }
    double tan(float angle) { return Math.tan(Math.toRadians(angle)); }

    // Logarithmic operations
    double log(float value) { return Math.log(value); }        // Natural log
    double log10(float value) { return Math.log10(value); }    // Base-10 log
}

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        ScientificCalculator calc = new ScientificCalculator();

        while (true) {
            System.out.println("\n--- Scientific Calculator ---");
            System.out.println("1. Integer Arithmetic");
            System.out.println("2. Float Arithmetic");
            System.out.println("3. Complex Arithmetic");
            System.out.println("4. Trigonometric Functions");
            System.out.println("5. Logarithmic Functions");
            System.out.println("6. Exit");
            System.out.print("Choose an option: ");
            int choice = sc.nextInt();

            if (choice == 6) break;

            switch (choice) {
                case 1:
                    System.out.print("Enter two integers: ");
                    int i1 = sc.nextInt();
                    int i2 = sc.nextInt();
                    System.out.print("Operation (+ - * /): ");
                    char op1 = sc.next().charAt(0);
                    switch (op1) {
                        case '+': System.out.println("Result: " + calc.add(i1, i2)); break;
                        case '-': System.out.println("Result: " + calc.subtract(i1, i2)); break;
                        case '*': System.out.println("Result: " + calc.multiply(i1, i2)); break;
                        case '/': System.out.println("Result: " + calc.divide(i1, i2)); break;
                    }
                    break;

                case 2:
                    System.out.print("Enter two float numbers: ");
                    float f1 = sc.nextFloat();
                    float f2 = sc.nextFloat();
                    System.out.print("Operation (+ - * /): ");
                    char op2 = sc.next().charAt(0);
                    switch (op2) {
                        case '+': System.out.println("Result: " + calc.add(f1, f2)); break;
                        case '-': System.out.println("Result: " + calc.subtract(f1, f2)); break;
                        case '*': System.out.println("Result: " + calc.multiply(f1, f2)); break;
                        case '/': System.out.println("Result: " + calc.divide(f1, f2)); break;
                    }
                    break;

                case 3:
                    System.out.print("Enter real and imaginary parts of first complex number: ");
                    double r1 = sc.nextDouble(), im1 = sc.nextDouble();
                    System.out.print("Enter real and imaginary parts of second complex number: ");
                    double r2 = sc.nextDouble(), im2 = sc.nextDouble();
                    Complex c1 = new Complex(r1, im1);
                    Complex c2 = new Complex(r2, im2);
                    System.out.print("Operation (+ - * /): ");
                    char op3 = sc.next().charAt(0);
                    Complex result = null;
                    switch (op3) {
                        case '+': result = calc.add(c1, c2); break;
                        case '-': result = calc.subtract(c1, c2); break;
                        case '*': result = calc.multiply(c1, c2); break;
                        case '/': result = calc.divide(c1, c2); break;
                    }
                    System.out.println("Result: " + result);
                    break;

                case 4:
                    System.out.print("Enter angle in degrees: ");
                    float angle = sc.nextFloat();
                    System.out.print("Function (sin/cos/tan): ");
                    String trig = sc.next();
                    switch (trig) {
                        case "sin": System.out.println("sin(" + angle + ") = " + calc.sin(angle)); break;
                        case "cos": System.out.println("cos(" + angle + ") = " + calc.cos(angle)); break;
                        case "tan": System.out.println("tan(" + angle + ") = " + calc.tan(angle)); break;
                    }
                    break;

                case 5:
                    System.out.print("Enter a positive number: ");
                    float value = sc.nextFloat();
                    System.out.print("Function (log/log10): ");
                    String log = sc.next();
                    switch (log) {
                        case "log": System.out.println("ln(" + value + ") = " + calc.log(value)); break;
                        case "log10": System.out.println("log10(" + value + ") = " + calc.log10(value)); break;
                    }
                    break;

                default:
                    System.out.println("Invalid option.");
            }
        }

        System.out.println("Calculator closed.");
        sc.close();
    }
}

