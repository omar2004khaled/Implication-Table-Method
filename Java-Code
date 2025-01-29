
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Comparator;
import java.util.HashMap;
import java.util.HashSet;
import java.util.List;
import java.util.Map;
import java.util.Scanner;
import java.util.Set;
public class Main {
	public static void main(String[] args) {   
	Scanner scanner = new Scanner(System.in);
/* examples from lectures and sheets 
a e e 1 1
b c e 1 1
c i h 0 0
d h a 1 1
e i f 0 0
f e g 0 0
g h b 1 1
h c d 0 0
i f b 1 1
*//*	 
a b i c g 0 0 0 0 0 0 0 0
b b c f g 0 0 0 0 0 0 0 0
c h d d f 1 1 1 1 1 1 1 1
d h c e g 1 1 1 1 1 1 1 1
e b c i g 0 0 0 0 0 0 0 0
f f i i k 0 0 0 0 0 0 0 0
g j k g h 0 0 0 0 0 0 0 0
h e f c g 0 0 0 0 0 0 0 0
i i i i d 0 0 0 0 0 0 0 0
j b f c g 0 0 0 0 0 0 0 0
k a c e g 1 1 1 1 1 1 1 1
*//*
a b d 1 0
b - b - 0
c e d 0 -
d b a 1 0
e - c - 1
f - e 0 1 *//*a h c 1 0
b c d 0 1
c h b 0 0
d f h 0 0
e c f 0 1
f f g 0 0
g g c 1 0
h a c 1 0
*/
/*a d c 0 0
b f h 0 0
c e d 1 1
d a e 0 0
e c a 1 1
f f b 1 1
g b h 0 0
h c g 1 1
*/
	    
        // ANSI escape code for blue colour
        String bb = "\u001B[34m";
        // ANSI escape code to reset colour
        String rr = "\u001B[0m";
        System.out.println(bb+"Enter (0) for complete Specified Networks (1) for incomplete Specified Networks"+rr);
        int comp = scanner.nextInt();
        System.out.println(bb+"incase of moore output(z) should be entered in repeated coloumns"+rr);
		char[][] inputArray = scanInputArray();
		if(inputArray[0].length==5) {
		boolean similarLastTwoElements = false;

        for (int i = 0; i < inputArray.length; i++) {
            for (int j = i + 1; j < inputArray.length; j++) {
                if (inputArray[i][3] == inputArray[j][3] && inputArray[i][4] == inputArray[j][4]) {
                    similarLastTwoElements = true;
                    break;
                }
            }
            if (similarLastTwoElements) {
                break;
            }
        }

        if (similarLastTwoElements) {
            
        } else {
            System.out.println(bb+"---Already reduced---"+rr);
            System.exit(0); 
        }
        // Call the function
        String[][] resultArray = createSquaredArray(inputArray);
        String[][] resultArray2 = xfunction(inputArray, resultArray);
        
System.out.println(bb+"-----State Table before reduction-----"+rr);
System.out.println("P.S  N.S at X=0   N.S at X=1    Output");
        for (int i = 0; i < inputArray.length; i++) {
            for (int j = 0; j < inputArray[i].length; j++) {
                System.out.print(inputArray[i][j] + "         ");
            }
            System.out.println();
        }
System.out.println();
System.out.println(bb+"-----Implication Table-----"+rr);

for (int i = 0; i < resultArray2.length; i++) {
            String[] row = resultArray2[i];
            int elementsToPrint = i + 2; // Starting from the first row, increment the number of elements to print

            // Print the elements in the row
            for (int j = 0; j < elementsToPrint; j++) {
                // Check if the column index is within the bounds of the array
                if (j < row.length) {
                    // Adjust the spacing based on the length of the element
                    System.out.print(String.format("%-8s ", row[j])); // Adjust the padding as needed
                }
            }
            System.out.println(); // Move to the next row
        }
System.out.println();
System.out.println(bb+"-----Equivalent Classes-----"+rr);    
String[] resultArray3 = manipulateArray(resultArray2);
if (resultArray3.length > 0) {
    String[] newArray = new String[resultArray3.length - 1];
    System.arraycopy(resultArray3, 1, newArray, 0, newArray.length);
    resultArray3 = newArray;
} else {
	resultArray3 = new String[0];
}
char[] firstColumn = new char[inputArray.length];

// Extract first column elements
for (int i = 0; i < inputArray.length; i++) {
    firstColumn[i] = inputArray[i][0];
}
// Find all characters not present in resultArray3
char[] missingChars = findMissingChars(firstColumn, resultArray3);
// Add the missing characters as separate elements to resultArray3
for (char c : missingChars) {
    resultArray3 = addElement(resultArray3, Character.toString(c));
}
removeSimilarCharacters(resultArray3);/*important for incomplete*/
for (int i = 0; i < resultArray3.length; i++) {
if (resultArray3.length==inputArray.length) {String concatenatedString = "";
for (String str : resultArray3) {
    concatenatedString += str;
}
// Convert concatenatedString to String[]
String[] concatenatedStringArray = { concatenatedString };
System.out.println(concatenatedStringArray[0]); break;}
else
    System.out.print(resultArray3[i] + " ");
}
System.out.println();
System.out.println();
System.out.println(bb+"-----State Table after reduction-----"+rr);
System.out.println("P.S  N.S at X=0   N.S at X=1    Output");
if (resultArray3.length==inputArray.length) {
	for (int i = 0; i < inputArray[0].length; i++) {
    System.out.print(inputArray[0][i] + "         ");
}}
else {
	
	 int numRows = inputArray.length; // Number of rows
     int numCols = inputArray[0].length;
     
     // Initialize resultArray3 with some string values
     

     for (int i = 0; i < resultArray3.length; i++) {
         if (resultArray3[i].length() > 1) {
             char firstChar = resultArray3[i].charAt(0); // Get the first character
             for (int l = 0; l < numRows; l++) {
                 for (int k = 0; k < numCols; k++) {
                     if (resultArray3[i].indexOf(inputArray[l][k]) != -1) { // Check if character exists in the string
                         inputArray[l][k] = firstChar; // Replace with the first character
                     }
                 }
             }
         }
     }
     
     inputArray = modifyArray(inputArray);
     removeRows(inputArray);
     
     for (char[] row1 : inputArray) {
    	    boolean isEmptyRow = true;
    	    // Check if row is not null and not empty
    	    if (row1 != null) {
    	        for (char c : row1) {
    	            if (c != ' ') {
    	                System.out.print(c + "      ");
    	                isEmptyRow = false;
    	            }
    	        }
    	        if (!isEmptyRow) {
    	            System.out.println();
    	        }
    	    }
    	}

	
}
		      }/*if*/
		else {        String[][] resultArray = createSquaredArray(inputArray);
                       String[][] resultArray2 = xxfunction(inputArray, resultArray);
                      System.out.println(bb+"-----State Table before reduction-----"+rr);
                       System.out.println("P.S                      N.S                               Output");
                               for (int i = 0; i < inputArray.length; i++) {
                                   for (int j = 0; j < inputArray[i].length; j++) {
                                       System.out.print(inputArray[i][j] + "         ");
                                   }
                                   System.out.println();
                               }
                       System.out.println();

                       System.out.println(bb+"-----Implication Table-----"+rr);

                       for (int i = 0; i < resultArray2.length; i++) {
                                   String[] row = resultArray2[i];
                                   int elementsToPrint = i + 2; // Starting from the first row, increment the number of elements to print

                                   // Print the elements in the row
                                   for (int j = 0; j < elementsToPrint; j++) {
                                       // Check if the column index is within the bounds of the array
                                       if (j < row.length) {
                                           // Adjust the spacing based on the length of the element
                                           System.out.print(String.format("%-15s ", row[j])); // Adjust the padding as needed
                                       }
                                   }
                                   System.out.println(); // Move to the next row
                               }
                       System.out.println();
                       System.out.println();
if(comp==0) {
                       System.out.println(bb+"-----Equivalent Classes-----"+rr);  
                       
                       String[] resultArray3 = manipulateArray(resultArray2);
                       if (resultArray3.length > 0) {
                           String[] newArray = new String[resultArray3.length - 1];
                           System.arraycopy(resultArray3, 1, newArray, 0, newArray.length);
                           resultArray3 = newArray;
                       } else {
                       	resultArray3 = new String[0];
                       }
                       char[] firstColumn = new char[inputArray.length];

                       // Extract first column elements
                       for (int i = 0; i < inputArray.length; i++) {
                           firstColumn[i] = inputArray[i][0];
                       }
                       // Find all characters not present in resultArray3
                       char[] missingChars = findMissingChars(firstColumn, resultArray3);
                       // Add the missing characters as separate elements to resultArray3
                       for (char c : missingChars) {
                           resultArray3 = addElement(resultArray3, Character.toString(c));
                       }
                       removeSimilarCharacters(resultArray3);/*important for incomplete*/
                       for (int i = 0; i < resultArray3.length; i++) {
                       if (resultArray3.length==inputArray.length) {String concatenatedString = "";
                       for (String str : resultArray3) {
                           concatenatedString += str;
                       }
                       // Convert concatenatedString to String[]
                       String[] concatenatedStringArray = { concatenatedString };
                       System.out.println(concatenatedStringArray[0]); break;}
                       else
                           System.out.print(resultArray3[i] + " ");
                       }  

                       System.out.println();
                       System.out.println();
                       System.out.println(bb+"-----State Table after reduction-----"+rr);
                       System.out.println("P.S                      N.S                               Output");
                       
                       if (resultArray3.length==inputArray.length) {
                       	for (int i = 0; i < inputArray[0].length; i++) {
                           System.out.print(inputArray[0][i] + "         ");
                       }}
                       else {
                       	
                       	 int numRows = inputArray.length; // Number of rows
                            int numCols = inputArray[0].length;
                            
                            // Initialize resultArray3 with some string values
                            

                            for (int i = 0; i < resultArray3.length; i++) {
                                if (resultArray3[i].length() > 1) {
                                    char firstChar = resultArray3[i].charAt(0); // Get the first character
                                    for (int l = 0; l < numRows; l++) {
                                        for (int k = 0; k < numCols; k++) {
                                            if (resultArray3[i].indexOf(inputArray[l][k]) != -1) { // Check if character exists in the string
                                                inputArray[l][k] = firstChar; // Replace with the first character
                                            }
                                        }
                                    }
                                }
                            }
                            
                            inputArray = modifyArray(inputArray);
                            removeRows(inputArray);
                            
                            for (char[] row1 : inputArray) {
                           	    boolean isEmptyRow = true;
                           	    // Check if row is not null and not empty
                           	    if (row1 != null) {
                           	        for (char c : row1) {
                           	            if (c != ' ') {
                           	                System.out.print(c + "      ");
                           	                isEmptyRow = false;
                           	            }
                           	        }
                           	        if (!isEmptyRow) {
                           	            System.out.println();
                           	        }
                           	    }
                           	}
                       }
}
else if(comp==1) {
	System.out.println(bb+"Implication table only available Reduced state table will be added later"+rr);
}

		        }
    }
 /*  Creates the squared array used in the Implication Table method */
public static String[][] createSquaredArray(char[][] inputArray) {
        int size = inputArray.length; //for columns ;)
        String[][] squaredArray = new String[size][size];

        // Fill the squared array with '@' characters except for the last row
        for (int i = 0; i < size - 1; i++) {
            for (int j = 0; j < size; j++) {
                if (j == 0) {
                    // Copy elements from the input array with a shift
                    squaredArray[i][j] = String.valueOf(inputArray[i + 1][j]);
                } else {
                    // Fill other columns with '@'
                    squaredArray[i][j] = "@";
                }
            }
        }

        // Set the last row in new array with elements from the first column in old array with a shift
        for (int j = 0; j < size; j++) {
            squaredArray[size - 1][j] = (j == 0) ? "@" : String.valueOf(inputArray[j - 1][0]);
        }

        return squaredArray;
    }
/*****************/
public static String[][] xfunction(char[][] inputArray, String[][] squaredArray) {
    int n1 = squaredArray.length;
    char temp1, temp2;
    boolean check;
 /*1st round*/   
    // Process elements with "@" in squaredArray
    for (int i = 0; i < n1; i++) {
        for (int j = 0; j < n1; j++) {
            if (squaredArray[i][j].equals("@") && (i != n1 - 1 || j != 0)) {
                temp1 = squaredArray[i][0].charAt(0);
                temp2 = squaredArray[n1 - 1][j].charAt(0);
                int arrayIndex1 = -1, arrayIndex2 = -1;
                // Find the arrays to which temp1 and temp2 belong
                for (int k = 0; k < inputArray.length; k++) {
                    if (inputArray[k][0] == temp1) {
                        arrayIndex1 = k;
                    }
                    if (inputArray[k][0] == temp2) {
                        arrayIndex2 = k;
                    }
                }
                // Compare last two elements of the arrays
                int lastIdx = inputArray[arrayIndex1].length - 1;
                check = check1(inputArray[arrayIndex1][lastIdx - 1],inputArray[arrayIndex2][lastIdx - 1])&&
                        check1(inputArray[arrayIndex1][lastIdx],inputArray[arrayIndex2][lastIdx]);
                if (!check) {
                    squaredArray[i][j] = "X";
                } else if (check) {
                    // Additional checks for the last two elements
/**************************************************************************************************************/
                    if (check1(inputArray[arrayIndex1][lastIdx - 2] , inputArray[arrayIndex2][lastIdx - 2] )&&
                        check1(inputArray[arrayIndex1][lastIdx - 3] , temp2 )&& check1(inputArray[arrayIndex2][lastIdx - 3] , temp1) ||
                        check1(inputArray[arrayIndex1][lastIdx - 3] , temp1) && check1(inputArray[arrayIndex2][lastIdx - 3] , temp2) &&
                        check1(inputArray[arrayIndex1][lastIdx - 2] , temp2) && check1(inputArray[arrayIndex2][lastIdx - 2] , temp1)) {
                        squaredArray[i][j] = "T";
                    } else if (check1(inputArray[arrayIndex1][lastIdx - 3] , inputArray[arrayIndex2][lastIdx - 3]) &&
                               !check1(inputArray[arrayIndex1][lastIdx - 2] , inputArray[arrayIndex2][lastIdx - 2])) {
                        squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - 2] + "," + inputArray[arrayIndex2][lastIdx - 2];
                    } else if (!check1(inputArray[arrayIndex1][lastIdx - 3] , inputArray[arrayIndex2][lastIdx - 3]) &&
                               check1(inputArray[arrayIndex1][lastIdx - 2] , inputArray[arrayIndex2][lastIdx - 2])) {
                        squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - 3] + "," + inputArray[arrayIndex2][lastIdx - 3];
                    }else if (check1(inputArray[arrayIndex1][lastIdx - 3] , inputArray[arrayIndex2][lastIdx - 4]) &&
                               check1(inputArray[arrayIndex1][lastIdx - 4] , inputArray[arrayIndex2][lastIdx - 3])) {
                        squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - 2] + "," + inputArray[arrayIndex2][lastIdx - 2];
                    }else if (check1(inputArray[arrayIndex1][lastIdx - 4] , inputArray[arrayIndex2][lastIdx - 2]) &&
                               check1(inputArray[arrayIndex1][lastIdx - 2] , inputArray[arrayIndex2][lastIdx - 4])) {
                        squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - 3] + "," + inputArray[arrayIndex2][lastIdx - 3];
                    }
                           /***************This should deal with redundant states****************/   
                    /********************************************************************************/
                    else if( (check1(inputArray[arrayIndex1][lastIdx - 3],inputArray[arrayIndex1][lastIdx - 4])||
                           check1(inputArray[arrayIndex1][lastIdx - 3],inputArray[arrayIndex2][lastIdx - 4]))&&
                            
                           (check1(inputArray[arrayIndex1][lastIdx - 2],inputArray[arrayIndex1][lastIdx - 4])||
                            check1(inputArray[arrayIndex1][lastIdx - 2],inputArray[arrayIndex2][lastIdx - 4]))&&
                            
                           (check1(inputArray[arrayIndex2][lastIdx - 2],inputArray[arrayIndex1][lastIdx - 4])||
                           check1(inputArray[arrayIndex2][lastIdx - 2],inputArray[arrayIndex2][lastIdx - 4]))&&
                      
                           (check1(inputArray[arrayIndex2][lastIdx - 3],inputArray[arrayIndex1][lastIdx - 4])||
                           check1(inputArray[arrayIndex2][lastIdx - 3],inputArray[arrayIndex2][lastIdx - 4]))   ){
                      squaredArray[i][j] = "T";
                      
                  }else if( check1(inputArray[arrayIndex1][lastIdx - 3],inputArray[arrayIndex2][lastIdx - 3])&&
                           check1(inputArray[arrayIndex1][lastIdx - 2],inputArray[arrayIndex2][lastIdx - 2])     ){
                      squaredArray[i][j] = "T";
                      
                  }
                    else if (!check1(inputArray[arrayIndex1][lastIdx - 3] , inputArray[arrayIndex2][lastIdx - 3]) &&
                               !check1(inputArray[arrayIndex1][lastIdx - 2] , inputArray[arrayIndex2][lastIdx - 2])) {
                        squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - 3] + "," + inputArray[arrayIndex2][lastIdx - 3] + 
                                             "/" + inputArray[arrayIndex1][lastIdx - 2] + "," + inputArray[arrayIndex2][lastIdx - 2];
                    }
                }
            }
        }
    }
/*3rd round*/
// Additional loop for handling cases where the length of the string at squaredArray[i][j] is 3
int counter=3;
while(counter==3) {
counter=2;
for (int i = 0; i < n1; i++) {
    for (int j = 0; j < n1; j++) {
        if (squaredArray[i][j].length() == 3) {
            // Extract temp1 and temp2 from squaredArray[i][j]
             temp1 = squaredArray[i][j].charAt(0);
             temp2 = squaredArray[i][j].charAt(2);
            
            // Find the value of the element in squaredArray whose leftmost element in its row is temp2 and bottommost element in its column is temp1
            for (int k = 0; k < n1; k++) {
                for (int m = 0; m < n1; m++) {
                    if ((squaredArray[k][0].charAt(0) == temp1 && squaredArray[n1-1][m].charAt(0) == temp2) ||
                        (squaredArray[k][0].charAt(0) == temp2 && squaredArray[n1-1][m].charAt(0) == temp1)) {
                        if (squaredArray[k][m].equals("X")) {
                            squaredArray[i][j] = "X"; counter =3;}
                        if (squaredArray[k][m].equals("T")) {
                            squaredArray[i][j] = "T"; counter =3;}
                    }
                }
            }
        }
    }
}
for (int i = 0; i < n1; i++) {
    for (int j = 0; j < n1; j++) {
        if (squaredArray[i][j].length() == 7) {
            // Extract temp1, temp2, temp3, temp4 from squaredArray[i][j]
             temp1 = squaredArray[i][j].charAt(0);
             temp2 = squaredArray[i][j].charAt(2);
            char temp3 = squaredArray[i][j].charAt(4);
            char temp4 = squaredArray[i][j].charAt(6);
            
            // Find the value of the element in squaredArray whose leftmost element in its row is temp2 and bottommost element in its column is temp1
            for (int k = 0; k < n1; k++) {
                for (int m = 0; m < n1; m++) {
                    if ((squaredArray[k][0].charAt(0) == temp1 && squaredArray[n1-1][m].charAt(0) == temp2) ||
                        (squaredArray[k][0].charAt(0) == temp2 && squaredArray[n1-1][m].charAt(0) == temp1) ||
                        (squaredArray[k][0].charAt(0) == temp3 && squaredArray[n1-1][m].charAt(0) == temp4) ||
                        (squaredArray[k][0].charAt(0) == temp4 && squaredArray[n1-1][m].charAt(0) == temp3)) {
                        if (squaredArray[k][m].equals("X")) {
                            squaredArray[i][j] = "X"; counter =3;}
                    }
                }
            }
        }
    }
}
}/*while counter*/    
    return squaredArray;
}

public static String[] manipulateArray(String[][] squaredArray) {
    int numRows = squaredArray.length;
    int numCols = squaredArray[0].length;

    String[] charArray = new String[numCols];
    String[] elementArray = new String[numCols];

    int size = 0;

    for (int i = 0; i < numCols; i++) {
        char temp = squaredArray[numRows - 1][i].charAt(0);
        boolean tempNotFound = true;

        // Check if the character already exists in charArray
        for (int k = 0; k < size; k++) {
            if (charArray[k] != null && charArray[k].indexOf(temp) != -1) { 
                tempNotFound = false;
                break;
            }
        }

        if (tempNotFound) {
            charArray[size] = String.valueOf(temp);
            StringBuilder elementBuilder = new StringBuilder();

            // Construct element by appending elements from the first column
            for (int j = 0; j < numRows; j++) {
                if (!squaredArray[j][i].equals("X") && !squaredArray[j][i].equals("@")) {
                    elementBuilder.append(squaredArray[j][0]);
                }
            }
            elementArray[size] = elementBuilder.toString();
            size++;
        }
    }

    // Construct the result array
    String[] resultArray = new String[size];
    for (int i = 0; i < size; i++) {
        resultArray[i] = charArray[i] + elementArray[i];
    }

    // Sort the result array
    Arrays.sort(resultArray);

    String[] manipulatedArr = manipulateArrayStrings(resultArray);
    String[] result3 = removeDuplicatesAndSubstrings(manipulatedArr);
    
    return result3;
    
}
public static String[] manipulateArrayStrings(String[] arr) {
    String[] manipulatedArr = new String[arr.length];
    for (int i = 0; i < arr.length; i++) {
        if (i == 0) {
            manipulatedArr[i] = arr[i].substring(1);
        } else if (i == 1) {
            manipulatedArr[i] = arr[i].substring(0, arr[i].length() - 1);
        } else {
            manipulatedArr[i] = arr[i].substring(1, arr[i].length() - 1);
        }
    }
    return manipulatedArr;
}
public static String[] removeDuplicatesAndSubstrings(String[] arr) {
    // Remove substrings
    for (int i = 0; i < arr.length; i++) {
        String string = arr[i];
        if (string != null) {
            for (int j = 0; j < arr.length; j++) {
                if (i != j && arr[j] != null && arr[j].contains(string)) {
                    arr[i] = null; // Mark substring for removal
                    break;
                }
            }
        }
    }

    // Remove marked elements and duplicates
    int index = 0;
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] != null) {
            boolean isDuplicate = false;
            for (int j = 0; j < i; j++) {
                if (arr[j] != null && arr[j].equals(arr[i])) {
                    isDuplicate = true;
                    break;
                }
            }
            if (!isDuplicate) {
                arr[index++] = arr[i];
            }
        }
    }

    // Resize array
    return Arrays.copyOf(arr, index);
}
public static char[] findMissingChars(char[] firstColumn, String[] resultArray3) {
    List<Character> missingCharsList = new ArrayList<>();
    for (char c : firstColumn) {
        boolean found = false;
        for (String str : resultArray3) {
            if (str.contains(Character.toString(c))) {
                found = true;
                break;
            }
        }
        if (!found) {
            missingCharsList.add(c);
        }
    }
    char[] missingChars = new char[missingCharsList.size()];
    for (int i = 0; i < missingCharsList.size(); i++) {
        missingChars[i] = missingCharsList.get(i);
    }
    return missingChars;
}
// Function to add an element to a String array
public static String[] addElement(String[] array, String element) {
    String[] newArray = new String[array.length + 1];
    System.arraycopy(array, 0, newArray, 0, array.length);
    newArray[array.length] = element;
    return newArray;
}
public static char[][] modifyArray(char[][] inputArray) {
    int numRows = inputArray.length;
    int numCols = inputArray[0].length;
    char[][] modifiedArray = new char[numRows][numCols];
    
    // Copy inputArray to modifiedArray
    for (int i = 0; i < numRows; i++) {
        modifiedArray[i] = Arrays.copyOf(inputArray[i], numCols);
    }

    // Remove duplicates
    for (int i = 1; i < numRows; i++) {
        boolean duplicate = false;
        for (int j = 0; j < i; j++) {
            if (Arrays.equals(inputArray[i], inputArray[j])) {
                duplicate = true;
                break;
            }
        }
        if (duplicate) {
            modifiedArray[i] = new char[numCols];
            Arrays.fill(modifiedArray[i], ' '); // Fill with spaces
        }
    }
    
    return modifiedArray;
}
public static char[][] scanInputArray() {
    // ANSI escape code for cyan color
    String bb = "\u001B[34m";
    // ANSI escape code to reset color
    String rr = "\u001B[0m";
    try (Scanner scanner = new Scanner(System.in)) {
		int rows, cols;
		int x;

		do {
		    System.out.print(bb + "Enter the number of states: " + rr);
		    rows = scanner.nextInt();
		    System.out.print(bb + "Enter the number of inputs: " + rr);
		    x = scanner.nextInt();
		    if(x==1) {cols=5;}
		    else if(x==2) {cols=13;}
		    else {cols=-1;}
		    if (cols != 5 && cols != 13) {
		        System.out.println(bb + "Number of inputs can be either 5 coloumns (one input) or 13 coloumns(two input). Please try again." + rr);
		    }
		} while (cols != 5 && cols != 13);

		char[][] array = new char[rows][cols];
		System.out.println(bb + "Enter the elements of the state table:" + rr);
		for (int i = 0; i < rows; i++) {
		    for (int j = 0; j < cols; j++) {
		        array[i][j] = scanner.next().charAt(0);
		    }
		}
		
		return array;
	}
}
public static String[][] xxfunction(char[][] inputArray, String[][] squaredArray) {
    int n1 = squaredArray.length;
    char temp1, temp2;
    boolean check;
 /*1st round*/   
    // Process elements with "@" in squaredArray
    for (int i = 0; i < n1; i++) {
        for (int j = 0; j < n1; j++) {
            if (squaredArray[i][j].equals("@") && (i != n1 - 1 || j != 0)) {
                temp1 = squaredArray[i][0].charAt(0);
                temp2 = squaredArray[n1 - 1][j].charAt(0);
                int arrayIndex1 = -1, arrayIndex2 = -1;

                // Find the arrays to which temp1 and temp2 belong
                for (int k = 0; k < inputArray.length; k++) {
                    if (inputArray[k][0] == temp1) {
                        arrayIndex1 = k;
                    }
                    if (inputArray[k][0] == temp2) {
                        arrayIndex2 = k;
                    }
                }
                        int lastIdx = inputArray[arrayIndex1].length - 1-4;
                        check = check1(inputArray[arrayIndex1][lastIdx - 3] , inputArray[arrayIndex2][lastIdx - 3]) &&
                        check1(inputArray[arrayIndex1][lastIdx - 2] , inputArray[arrayIndex2][lastIdx - 2]) &&
                        check1(inputArray[arrayIndex1][lastIdx - 1] , inputArray[arrayIndex2][lastIdx - 1]) &&
                        check1(inputArray[arrayIndex1][lastIdx] , inputArray[arrayIndex2][lastIdx])&&
                        check1(inputArray[arrayIndex1][lastIdx + 3] , inputArray[arrayIndex2][lastIdx + 3]) &&
                        check1(inputArray[arrayIndex1][lastIdx + 2] , inputArray[arrayIndex2][lastIdx + 2]) &&
                        check1(inputArray[arrayIndex1][lastIdx + 1] , inputArray[arrayIndex2][lastIdx + 1]) &&
                        check1(inputArray[arrayIndex1][lastIdx+4] , inputArray[arrayIndex2][lastIdx+4])
                        
                        ;

                if (!check) {
                    squaredArray[i][j] = "X";
                } else if (check) {
            
/**************************************************************************************************************/
                	if (check1(inputArray[arrayIndex1][lastIdx - (4 + 3)] , inputArray[arrayIndex2][lastIdx - (4 + 3)])&&
                	        check1(inputArray[arrayIndex1][lastIdx - (3 + 3)] , inputArray[arrayIndex2][lastIdx - (3 + 3)]) &&
                	        check1(inputArray[arrayIndex1][lastIdx - (2 + 3)] , inputArray[arrayIndex2][lastIdx - (2 + 3)]) &&
                	        check1(inputArray[arrayIndex1][lastIdx - (1 + 3)] , inputArray[arrayIndex2][lastIdx - (1 + 3)])) {
                	    squaredArray[i][j] = "T";
                	}
                	if (!check1(inputArray[arrayIndex1][1] , inputArray[arrayIndex2][1]) &&
                            !check1(inputArray[arrayIndex1][2] , inputArray[arrayIndex2][2]) &&
                            !check1(inputArray[arrayIndex1][3] , inputArray[arrayIndex2][3]) &&
                            !check1(inputArray[arrayIndex1][4] , inputArray[arrayIndex2][4])	
                			
                			) {
                     squaredArray[i][j] = inputArray[arrayIndex1][1] + "," + inputArray[arrayIndex2][1] + 
                                          "/" + inputArray[arrayIndex1][2] + "," + inputArray[arrayIndex2][2] +"/" +
                                        		  inputArray[arrayIndex1][3] + "," + inputArray[arrayIndex2][3] + 
                                                  "/" + inputArray[arrayIndex1][4] + "," + inputArray[arrayIndex2][4];
                 }if (!check1(inputArray[arrayIndex1][lastIdx - 4-3] , inputArray[arrayIndex2][lastIdx - 4-3]) &&
                		 !check1( inputArray[arrayIndex1][lastIdx - 3-3] , inputArray[arrayIndex2][lastIdx - 3-3]) &&
                		 !check1(inputArray[arrayIndex1][lastIdx - 2-3] , inputArray[arrayIndex2][lastIdx - 2-3]) &&
                		 check1(inputArray[arrayIndex1][lastIdx - 1-3] , inputArray[arrayIndex2][lastIdx - 1-3])) {
             		squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - 4-3] + "," + inputArray[arrayIndex2][lastIdx - 4-3] + 
                             "/" + inputArray[arrayIndex1][lastIdx - 3-3] + "," + inputArray[arrayIndex2][lastIdx - 3-3]    + 
                                      "/" + inputArray[arrayIndex1][lastIdx - 2-3] + "," + inputArray[arrayIndex2][lastIdx - 2-3] ;
             	}

                    else if (!check1(inputArray[arrayIndex1][lastIdx - (4+3)] , inputArray[arrayIndex2][lastIdx - (4+3)]) &&
                    		check1(inputArray[arrayIndex1][lastIdx - (3+3)] , inputArray[arrayIndex2][lastIdx - (3+3)]) &&
                    		check1(inputArray[arrayIndex1][lastIdx - (2+3)] , inputArray[arrayIndex2][lastIdx - (2+3)]) &&
                    		check1(inputArray[arrayIndex1][lastIdx - (1+3)] , inputArray[arrayIndex2][lastIdx - (1+3)])) {
                       squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - (4+3)] + "," + inputArray[arrayIndex2][lastIdx - (4+3)];
               } 
               // Check if the second, third, fourth, and fifth elements are different except the third one
               else if (check1(inputArray[arrayIndex1][lastIdx - (4+3)] , inputArray[arrayIndex2][lastIdx - (4+3)]) &&
            		   !check1(inputArray[arrayIndex1][lastIdx - (3+3)] , inputArray[arrayIndex2][lastIdx - (3+3)]) &&
            		   check1(inputArray[arrayIndex1][lastIdx - (2+3)] , inputArray[arrayIndex2][lastIdx - (2+3)]) &&
            		   check1(inputArray[arrayIndex1][lastIdx - (1+3)] , inputArray[arrayIndex2][lastIdx - (1+3)])) {
                       squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - (3+3)] + "," + inputArray[arrayIndex2][lastIdx - (3+3)];
               } 
               // Check if the second, third, fourth, and fifth elements are different except the fourth one
               else if (check1(inputArray[arrayIndex1][lastIdx - (4+3)] , inputArray[arrayIndex2][lastIdx - (4+3)]) &&
            		   check1(inputArray[arrayIndex1][lastIdx - (3+3)] , inputArray[arrayIndex2][lastIdx - (3+3)]) &&
            		   !check1(inputArray[arrayIndex1][lastIdx - (2+3)] , inputArray[arrayIndex2][lastIdx - (2+3)]) &&
            		   check1(inputArray[arrayIndex1][lastIdx - (1+3)] , inputArray[arrayIndex2][lastIdx - (1+3)])) {
                       squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - (2+3)] + "," + inputArray[arrayIndex2][lastIdx - (2+3)];
               }
               // Check if the second, third, fourth, and fifth elements are different except the fifth one
               else if (check1(inputArray[arrayIndex1][lastIdx - (4+3)] , inputArray[arrayIndex2][lastIdx - (4+3)]) &&
            		   check1(inputArray[arrayIndex1][lastIdx - (3+3)] , inputArray[arrayIndex2][lastIdx - (3+3)]) &&
            		   check1(inputArray[arrayIndex1][lastIdx - (2+3)] , inputArray[arrayIndex2][lastIdx - (2+3)]) &&
            		   !check1(inputArray[arrayIndex1][lastIdx - (1+3)] , inputArray[arrayIndex2][lastIdx - (1+3)])) {
                       squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - (1+3)] + "," + inputArray[arrayIndex2][lastIdx - (1+3)];
               }

                    
      /***********************************************************************************************************/                               
               
              	else if (!check1(inputArray[arrayIndex1][lastIdx - (4+3)] , inputArray[arrayIndex2][lastIdx - (4+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (3+3)] , inputArray[arrayIndex2][lastIdx - (3+3)]) &&
             		   check1(inputArray[arrayIndex1][lastIdx - (2+3)] , inputArray[arrayIndex2][lastIdx - (2+3)]) &&
             		   check1(inputArray[arrayIndex1][lastIdx - (1+3)] , inputArray[arrayIndex2][lastIdx - (1+3)])) {
              		squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - 4-3] + "," + inputArray[arrayIndex2][lastIdx - 4-3] + 
                            "/" + inputArray[arrayIndex1][lastIdx - 3-3] + "," + inputArray[arrayIndex2][lastIdx - 3-3];
              	} 
             
              	else if (!check1(inputArray[arrayIndex1][lastIdx - (4+3)] , inputArray[arrayIndex2][lastIdx - (4+3)]) &&
             		   check1(inputArray[arrayIndex1][lastIdx - (3+3)] , inputArray[arrayIndex2][lastIdx - (3+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (2+3)] , inputArray[arrayIndex2][lastIdx - (2+3)]) &&
             		   check1(inputArray[arrayIndex1][lastIdx - (1+3)] , inputArray[arrayIndex2][lastIdx - (1+3)])) {
              		squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - 4-3] + "," + inputArray[arrayIndex2][lastIdx - 4-3] + 
                            "/" + inputArray[arrayIndex1][lastIdx - 2-3] + "," + inputArray[arrayIndex2][lastIdx - 2-3];
              	} 
              
              	else if (!check1(inputArray[arrayIndex1][lastIdx - (4+3)] , inputArray[arrayIndex2][lastIdx - (4+3)]) &&
             		   check1(inputArray[arrayIndex1][lastIdx - (3+3)] , inputArray[arrayIndex2][lastIdx - (3+3)]) &&
             		   check1(inputArray[arrayIndex1][lastIdx - (2+3)] , inputArray[arrayIndex2][lastIdx - (2+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (1+3)] , inputArray[arrayIndex2][lastIdx - (1+3)])) {
              		squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - 4-3] + "," + inputArray[arrayIndex2][lastIdx - 4-3] + 
                            "/" + inputArray[arrayIndex1][lastIdx - 1-3] + "," + inputArray[arrayIndex2][lastIdx - 1-3];
              		
              	}
              	
              	else if (check1(inputArray[arrayIndex1][lastIdx - (4+3)] , inputArray[arrayIndex2][lastIdx - (4+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (3+3)] , inputArray[arrayIndex2][lastIdx - (3+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (2+3)] , inputArray[arrayIndex2][lastIdx - (2+3)]) &&
             		   check1(inputArray[arrayIndex1][lastIdx - (1+3)] , inputArray[arrayIndex2][lastIdx - (1+3)])) {
              		squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - 3-3] + "," + inputArray[arrayIndex2][lastIdx - 3-3] + 
                            "/" + inputArray[arrayIndex1][lastIdx - 2-3] + "," + inputArray[arrayIndex2][lastIdx - 2-3];
              		
              	}
              	else if (check1(inputArray[arrayIndex1][lastIdx - (4+3)] , inputArray[arrayIndex2][lastIdx - (4+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (3+3)] , inputArray[arrayIndex2][lastIdx - (3+3)]) &&
             		   check1(inputArray[arrayIndex1][lastIdx - (2+3)] , inputArray[arrayIndex2][lastIdx - (2+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (1+3)] , inputArray[arrayIndex2][lastIdx - (1+3)])) {
              		squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - 3-3] + "," + inputArray[arrayIndex2][lastIdx -3-3] + 
                            "/" + inputArray[arrayIndex1][lastIdx - 1-3] + "," + inputArray[arrayIndex2][lastIdx - 1-3];
              	} 
             
              	else if (check1(inputArray[arrayIndex1][lastIdx - (4+3)] , inputArray[arrayIndex2][lastIdx - (4+3)]) &&
             		   check1(inputArray[arrayIndex1][lastIdx - (3+3)] , inputArray[arrayIndex2][lastIdx - (3+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (2+3)] , inputArray[arrayIndex2][lastIdx - (2+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (1+3)] , inputArray[arrayIndex2][lastIdx - (1+3)])) {
              		squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - 2-3] + "," + inputArray[arrayIndex2][lastIdx - 2-3] + 
                            "/" + inputArray[arrayIndex1][lastIdx - 1-3] + "," + inputArray[arrayIndex2][lastIdx - 1-3];
              		
              	}
/*************************************************************/
            	else if (check1(inputArray[arrayIndex1][lastIdx - (4+3)] , inputArray[arrayIndex2][lastIdx - (4+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (3+3)] , inputArray[arrayIndex2][lastIdx - (3+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (2+3)] , inputArray[arrayIndex2][lastIdx - (2+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (1+3)] , inputArray[arrayIndex2][lastIdx - (1+3)])) {
            		squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - 3-3] + "," + inputArray[arrayIndex2][lastIdx - 3-3] + 
                            "/" + inputArray[arrayIndex1][lastIdx - 2-3] + "," + inputArray[arrayIndex2][lastIdx - 2-3]    + 
                                     "/" + inputArray[arrayIndex1][lastIdx - 1-3] + "," + inputArray[arrayIndex2][lastIdx - 1-3] ;
            	} 
            	
            	else if (!check1(inputArray[arrayIndex1][lastIdx - (4+3)] , inputArray[arrayIndex2][lastIdx - (4+3)]) &&
             		   check1(inputArray[arrayIndex1][lastIdx - (3+3)] , inputArray[arrayIndex2][lastIdx - (3+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (2+3)] , inputArray[arrayIndex2][lastIdx - (2+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (1+3)] , inputArray[arrayIndex2][lastIdx - (1+3)])) {
            		squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - 4-3] + "," + inputArray[arrayIndex2][lastIdx - 4-3] + 
                            "/" + inputArray[arrayIndex1][lastIdx - 2-3] + "," + inputArray[arrayIndex2][lastIdx - 2-3]    + 
                                     "/" + inputArray[arrayIndex1][lastIdx - 1-3] + "," + inputArray[arrayIndex2][lastIdx - 1-3] ;
            	} 
            	
            	else if (!check1(inputArray[arrayIndex1][lastIdx - (4+3)] , inputArray[arrayIndex2][lastIdx - (4+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (3+3)] , inputArray[arrayIndex2][lastIdx - (3+3)]) &&
             		   check1(inputArray[arrayIndex1][lastIdx - (2+3)] , inputArray[arrayIndex2][lastIdx - (2+3)]) &&
             		   !check1(inputArray[arrayIndex1][lastIdx - (1+3)] , inputArray[arrayIndex2][lastIdx - (1+3)])) {
            		squaredArray[i][j] = inputArray[arrayIndex1][lastIdx - 4-3] + "," + inputArray[arrayIndex2][lastIdx - 4-3] + 
                            "/" + inputArray[arrayIndex1][lastIdx - 3-3] + "," + inputArray[arrayIndex2][lastIdx - 3-3]    + 
                                     "/" + inputArray[arrayIndex1][lastIdx - 1-3] + "," + inputArray[arrayIndex2][lastIdx - 1-3] ;
            	} 	
                }
                }
            }
        }

/*3rd round*/
// Additional loop for handling cases where the length of the string at squaredArray[i][j] is 3
int counter=3;
while(counter==3) {
counter=2;
for (int i = 0; i < n1; i++) {
    for (int j = 0; j < n1; j++) {
        if (squaredArray[i][j].length() == 3) {
            // Extract temp1 and temp2 from squaredArray[i][j]
             temp1 = squaredArray[i][j].charAt(0);
             temp2 = squaredArray[i][j].charAt(2);   
            // Find the value of the element in squaredArray whose leftmost element in its row is temp2 and bottommost element in its column is temp1
            for (int k = 0; k < n1; k++) {
                for (int m = 0; m < n1; m++) {
                    if ((squaredArray[k][0].charAt(0) == temp1 && squaredArray[n1-1][m].charAt(0) == temp2) ||
                        (squaredArray[k][0].charAt(0) == temp2 && squaredArray[n1-1][m].charAt(0) == temp1)) {
                        if (squaredArray[k][m].equals("X")) {
                            squaredArray[i][j] = "X"; counter =3;}
                        if (squaredArray[k][m].equals("T")) {
                            squaredArray[i][j] = "T"; counter =3;}
                    }
                }
            }
        }
    }
}
for (int i = 0; i < n1; i++) {
    for (int j = 0; j < n1; j++) {
        if (squaredArray[i][j].length() == 7) {
            // Extract temp1, temp2, temp3, temp4 from squaredArray[i][j]
             temp1 = squaredArray[i][j].charAt(0);
             temp2 = squaredArray[i][j].charAt(2);
            char temp3 = squaredArray[i][j].charAt(4);
            char temp4 = squaredArray[i][j].charAt(6);
            
            // Find the value of the element in squaredArray whose leftmost element in its row is temp2 and bottommost element in its column is temp1
            for (int k = 0; k < n1; k++) {
                for (int m = 0; m < n1; m++) {
                    if ((squaredArray[k][0].charAt(0) == temp1 && squaredArray[n1-1][m].charAt(0) == temp2) ||
                        (squaredArray[k][0].charAt(0) == temp2 && squaredArray[n1-1][m].charAt(0) == temp1) ||
                        (squaredArray[k][0].charAt(0) == temp3 && squaredArray[n1-1][m].charAt(0) == temp4) ||
                        (squaredArray[k][0].charAt(0) == temp4 && squaredArray[n1-1][m].charAt(0) == temp3)) {
                        if (squaredArray[k][m].equals("X")) {
                            squaredArray[i][j] = "X"; counter =3;}
                    }
                }
            }
        }
    }
}
//Additional loop for handling cases where the length of the string at squaredArray[i][j] is 11
for (int i = 0; i < n1; i++) {
for (int j = 0; j < n1; j++) {
   if (squaredArray[i][j].length() == 11) {
       // Extract temp1, temp2, temp3, temp4 from squaredArray[i][j]
        temp1 = squaredArray[i][j].charAt(0);
        temp2 = squaredArray[i][j].charAt(2);
       char temp3 = squaredArray[i][j].charAt(4);
       char temp4 = squaredArray[i][j].charAt(6);
       char temp5 = squaredArray[i][j].charAt(8);
       char temp6 = squaredArray[i][j].charAt(10);
       // Find the value of the element in squaredArray whose leftmost element in its row is temp2 and bottommost element in its column is temp1
       for (int k = 0; k < n1; k++) {
           for (int m = 0; m < n1; m++) {
               if ((squaredArray[k][0].charAt(0) == temp1 && squaredArray[n1-1][m].charAt(0) == temp2) ||
                   (squaredArray[k][0].charAt(0) == temp2 && squaredArray[n1-1][m].charAt(0) == temp1) ||
                   (squaredArray[k][0].charAt(0) == temp3 && squaredArray[n1-1][m].charAt(0) == temp4) ||
                   (squaredArray[k][0].charAt(0) == temp4 && squaredArray[n1-1][m].charAt(0) == temp3) ||
                   (squaredArray[k][0].charAt(0) == temp5 && squaredArray[n1-1][m].charAt(0) == temp6) ||
                   (squaredArray[k][0].charAt(0) == temp6 && squaredArray[n1-1][m].charAt(0) == temp5)
              		 ) {
            	   if (squaredArray[k][m].equals("X")) {
                       squaredArray[i][j] = "X"; counter =3;}
               }
           }
       }
   }
}
}
//Additional loop for handling cases where the length of the string at squaredArray[i][j] is 15
for (int i = 0; i < n1; i++) {
for (int j = 0; j < n1; j++) {
 if (squaredArray[i][j].length() == 15) {
     // Extract temp1, temp2, temp3, temp4 from squaredArray[i][j]
      temp1 = squaredArray[i][j].charAt(0);
      temp2 = squaredArray[i][j].charAt(2);
     char temp3 = squaredArray[i][j].charAt(4);
     char temp4 = squaredArray[i][j].charAt(6);
     char temp5 = squaredArray[i][j].charAt(8);
     char temp6 = squaredArray[i][j].charAt(10);
     char temp7 = squaredArray[i][j].charAt(12);
     char temp8 = squaredArray[i][j].charAt(14);
     // Find the value of the element in squaredArray whose leftmost element in its row is temp2 and bottommost element in its column is temp1
     for (int k = 0; k < n1; k++) {
         for (int m = 0; m < n1; m++) {
             if ((squaredArray[k][0].charAt(0) == temp1 && squaredArray[n1-1][m].charAt(0) == temp2) ||
                 (squaredArray[k][0].charAt(0) == temp2 && squaredArray[n1-1][m].charAt(0) == temp1) ||
                 (squaredArray[k][0].charAt(0) == temp3 && squaredArray[n1-1][m].charAt(0) == temp4) ||
                 (squaredArray[k][0].charAt(0) == temp4 && squaredArray[n1-1][m].charAt(0) == temp3) ||
                 (squaredArray[k][0].charAt(0) == temp5 && squaredArray[n1-1][m].charAt(0) == temp6) ||
                 (squaredArray[k][0].charAt(0) == temp6 && squaredArray[n1-1][m].charAt(0) == temp5) ||
                 (squaredArray[k][0].charAt(0) == temp7 && squaredArray[n1-1][m].charAt(0) == temp8) ||
                 (squaredArray[k][0].charAt(0) == temp8 && squaredArray[n1-1][m].charAt(0) == temp7) 
                 
            		 ) {
            	 if (squaredArray[k][m].equals("X")) {
                     squaredArray[i][j] = "X"; counter =3;}
             }
         }
     }
 }
}
}
}/*while counter*/    
    return squaredArray;
}
public static boolean check1(char char1, char char2) {
    return char1 == char2 || char1 == '-' || char2 == '-';
}
public static void removeSimilarCharacters(String[] strings) {
    Map<Character, Integer> charCount = new HashMap<>();

    // Count characters in each string
    for (String str : strings) {
        boolean uniqueChars = true;
        for (char c : str.toCharArray()) {
            charCount.put(c, charCount.getOrDefault(c, 0) + 1);
            if (charCount.get(c) > 1) {
                uniqueChars = false;
            }
        }
        if (uniqueChars) {
            // If string contains only unique characters, leave it unchanged
            continue;
        }
    }
    // Remove characters from strings with lower length
    for (int i = 0; i < strings.length; i++) {
        for (char c : charCount.keySet()) {
            if (charCount.get(c) >= 2 && strings[i].contains(String.valueOf(c))) {
                for (int j = 0; j < strings.length; j++) {
                    if (j != i && strings[j].contains(String.valueOf(c))) {
                        strings[j] = strings[j].replaceFirst(String.valueOf(c), "");
                    }
                }
            }
        }
    }
}
public static void removeRows(char[][] charArray) {
    // Set to keep track of first characters of each row
    Set<Character> firstChars = new HashSet<>();

    // Iterate over the array to determine which rows to remove
    for (int i = 0; i < charArray.length; i++) {
        char firstChar = charArray[i][0];
        if (firstChar != '-') { // Ignore rows with '-' as the first character
            if (!firstChars.add(firstChar)) {
                // Remove current row if its first character has been encountered before
                charArray[i] = null;
            }
        }
    }
    // Shift rows up to fill null spaces
    int shift = 0;
    for (int i = 0; i < charArray.length; i++) {
        if (charArray[i] == null) {
            shift++;
        } else if (shift > 0) {
            charArray[i - shift] = charArray[i];
            charArray[i] = null;
        }
    }
}
public static String[] rearrangeStrings(String[] input) {
    HashMap<Character, String> uniqueCharsMap = new HashMap<>();

    // Identify unique characters and their corresponding strings
    for (String str : input) {
        for (int i = 0; i < str.length(); i++) {
            char ch = str.charAt(i);
            if (!uniqueCharsMap.containsKey(ch)) {
                uniqueCharsMap.put(ch, str);
            } else if (!uniqueCharsMap.get(ch).equals(str)) {
                uniqueCharsMap.put(ch, ""); // Mark the character as not unique if found in another string
            }
        }
    }
    // Sort the strings based on their lengths
    Arrays.sort(input, Comparator.comparingInt(String::length));
    // Rearrange the strings based on the presence of unique characters
    List<String> resultList = new ArrayList<>();
    for (String str : input) {
        boolean hasUniqueChar = false;
        for (char ch : str.toCharArray()) {
            if (uniqueCharsMap.get(ch).equals(str)) {
                hasUniqueChar = true;
                break;
            }
        }
        if (hasUniqueChar) {
            resultList.add(str);
        }
    }
    // Add remaining strings sorted by length
    for (String str : input) {
        if (!resultList.contains(str)) {
            resultList.add(str);
        }
    }
    // Convert list back to array
    return resultList.toArray(new String[0]);
}
}
