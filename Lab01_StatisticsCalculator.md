package CalculatorLab;
import java.util.*;

public class Calculator {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in); //create a new scanner

        //prompt input
        System.out.println("Enter a list of numbers seperated by spaces: \n"); 
        String userInput = input.nextLine(); //store input
        
        //format input, split by white space
        String[] numbers = userInput.trim().split("\\s+");
        
        //store numbers in a list
        List<Double> numList = new ArrayList<>();
        
        for(int i = 0; i < numbers.length; i++){
                double num = Double.parseDouble(numbers[i]); //convert to double
                numList.add(num); //add the current number to the list
        }
        
        //-----------------------------------------------------------------------------------------------
        //prompt the user to select an action 
        System.out.println("Select an integer for an operation: "
                + "\n1. MEDIAN \n2. MEAN \n3. SORT ASCENDING");
        //store the user's response in a variable
        int opChoice = input.nextInt();
        
        //use a switch statement to call a function based on the input
        switch(opChoice){
            case 1:
                median(numList);
                break;
            case 2:
                mean(numList);
                break;
            case 3:
                sortAscending(numList);
                break; 
            default:
                System.out.println("Invalid option. Please select 1, 2, or 3");
        }
        input.close();   
    }
    
    //methods for calculator
    
    //sort ascending method uses nested loops and conditionals
    public static void sortAscending(List<Double> list){
        Collections.sort(list);
        System.out.println("SORTED LIST: " + list);
    }
    
    //calculating mean method
    public static void mean(List<Double> list){
        double sum = 0;
        for(int i = 0; i < list.size(); i++){
            sum = sum + list.get(i);
        }
        
        double mean = sum/(list.size());
        System.out.println("MEAN: " + mean);
    }
    
    public static void median(List<Double> list){
        int n = list.size();
            sortAscending(list);
            
            if(n % 2 == 0){ //for even # of values in the list
                double avg = (list.get(n/2 - 1) + list.get(n/2)) /2;
                System.out.println("MEDIAN: " + avg);
            }
            else{ //for odd # of values in the list
                System.out.println("MEDIAN: " + list.get(n/2));
            }
    }
}
