# Calculator

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class StringSumCalculator 
{
    private JFrame frame;                   // The main window frame
    private JTextField firstNumberField, secondNumberField;    // Text field for the numbers input
    private JButton calculateButton;        // Button to perform the calculation

    public StringSumCalculator() 
    {
        frame = new JFrame("Calculator");   // Create the frame with a title
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);   // Close the application when the frame is closed
        frame.setSize(300, 150);   // Set the size of the frame
        frame.setLayout(new FlowLayout());   // Set the layout manager to FlowLayout

        JLabel firstLabel = new JLabel("First number:");   // Create a label for the first number input
        firstNumberField = new JTextField(10);   // Create a text field for the first number input with width 10

        JLabel secondLabel = new JLabel("Second number:");   // Create a label for the second number input
        secondNumberField = new JTextField(10);   // Create a text field for the second number input with width 10

        calculateButton = new JButton("Calculate");   // Create the calculate button
        calculateButton.addActionListener(new CalculateButtonListener());   // Add an ActionListener to the button

        frame.add(firstLabel);   // Add the first label to the frame
        frame.add(firstNumberField);   // Add the first number input field to the frame
        frame.add(secondLabel);   // Add the second label to the frame
        frame.add(secondNumberField);   // Add the second number input field to the frame
        frame.add(calculateButton);   // Add the calculate button to the frame

        frame.setVisible(true);   // Make the frame visible
    }

    private class CalculateButtonListener implements ActionListener 
    {

        public void actionPerformed(ActionEvent e) 
        {
            try 
            {
                String firstString = firstNumberField.getText();   // Get the text entered in the first number field
                String secondString = secondNumberField.getText();   // Get the text entered in the second number field

                double firstNumber = Double.parseDouble(firstString);   // Convert the first string to an integer
                double secondNumber = Double.parseDouble(secondString);   // Convert the second string to an integer

                double total = firstNumber + secondNumber;   // Calculate the sum of the two numbers

                JOptionPane.showMessageDialog(frame, "Total : " + total);   // Display the sum in a dialog box
            } 
            
            catch (NumberFormatException ex) 
            {
                JOptionPane.showMessageDialog(frame, "Invalid input. Please enter valid integers.");   // Display an error message in a dialog box if the input is not valid
            }
        }
    }

    public static void main(String[] args) 
    {
        SwingUtilities.invokeLater(new Runnable() 
        {
            public void run() 
            {
                new StringSumCalculator();   // Create an instance of the class
            }
        });
    }
}
