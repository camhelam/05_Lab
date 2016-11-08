# 05_Lab

Main Lab #5 - Hot plate
Background

In this lab you will compute the steady state temperature distribution over a piece of metal. This steady state analysis is used in solving many physics problems. Similar matrix algorithms are also used in analyzing airplane wing and automobile surface pressure. These types of calculations are intended to ensure that everything works correctly in such applications. Though the full analysis may be complicated, pieces of it are quite simple, such as the problem described below.
Requirements
Part 1 - Initialize and Print 2D Array (25 points)

In this lab you will write a program to determine the temperature distribution for a two-dimensional plate with constant boundary conditions. Use a 20 X 20 two-dimensional array of numbers to represent the temperature at different places on a (square) plate. The elements on the boundaries have fixed temperatures. The elements on the top and bottom row have a fixed temperature of 100 degrees. The elements on the leftmost and rightmost columns have a temperature of zero degrees. (The corner elements have a temperature of zero degrees.)

For part one you must initialize the 2D array and print it to the screen. Print the numbers in the array with a fixed precision of 4 and width 10.

For example, an initialized 5 X 5 matrix (note: yours should be 20x20) would look like this.

    0.0000,  100.0000,  100.0000,  100.0000,    0.0000
    0.0000,    0.0000,    0.0000,    0.0000,    0.0000
    0.0000,    0.0000,    0.0000,    0.0000,    0.0000
    0.0000,    0.0000,    0.0000,    0.0000,    0.0000
    0.0000,  100.0000,  100.0000,  100.0000,    0.0000

You must initialize the plate programmatically using loops. You may not use a large number of assignment statements. You must also use a 2-d array, not a vector and not a large number of independent variables.

Note also that there is one comma (just a comma) after each number, except the last number in the row
Part 2 - Update Elements Once (25 points)

The job of the algorithm is to find the steady-state temperature distribution of the interior elements which are constantly changing to become the average of the temperature of their neighbors. Steady state means that the temperature of any cell is virtually unchanging and approximately equal to the average of the temperatures of its four neighbors on the north, south, east, and west directions (do not worry about the diagonal neighbors). Note that the steady state temperatures will be the same regardless of what the beginning temperatures are for the interior elements.

To calculate the new temperature value of an array element, take the average of the values in the 4 neighbors of that cell from the previous iteration. This value will be placed in the output array.

For example, suppose the current state of the plate is (it won't be like this to start out with, but suppose it were):

    0.0000,  100.0000,  100.0000,  100.0000,    0.0000
    0.0000,   40.6250,   50.0000,   40.6250,    0.0000
    0.0000,   25.0000,   31.2500,   25.0000,    0.0000
    0.0000,   40.6250,   50.0000,   40.6250,    0.0000
    0.0000,  100.0000,  100.0000,  100.0000,    0.0000

In this example, the cell at position array[1][3] currently has a value of 40.6250 degrees. At the current iteration, this element in the output array will be set to the average of the current value of its 4 neighbors, that is, array[0][3] + array[1][4] + array[2][3] + array[1][2])/4 or (100.0000 + 0.0000 + 25.0000 + 50.0000)/4 which is 43.7500.

For Part 2, Print the first iteration. (Note that the first iteration is NOT the initialized matrix, it is the matrix obtained after one update to each cell in the array).

If you think about it you will realize that the value at array[2][3] depends upon the value at array[1][3]. One could ask, should the computation of array[2][3] use the value of array[1][3] as it was at the start of the current iteration, or the already updated value. This is an interesting theoretical question, but for our purposes you need to use the value as it was at the start of the iteration. Thus you will need two 2D arrays, one of which should contain the values as they were before the computations (an "old values" array), and one where the new values are being placed (a "new values" array).

For Part 2, compute the values of the first iteration and print them out. Note that the first iteration is NOT just the initialized matrix, it is the matrix obtained after one update to each cell in the array.
Part 3 - Repeat update until Stable (25 points)

After printing the results from the first iteration, continue to iterate (calculating the temperature for all interior cells) until no cell in the array changes by more than 0.1 degrees. Your program should monitor the largest change for any cell in the array in order to determine when to stop iterating. At the end of each iteration you will copy the values from the "new values" array into the "old values" array, to be ready for the next iteration.

Once all of the values in the plate have ceased to change by more than 0.1 degrees, print the plate, in the same comma separated form used above.
Part 4 - Using Excel to Display the Results (Extra Credit 5 Points)

Print the values in the stable plate one more time but in tab separated form, like this:

0.0000    100.0000    100.0000    100.0000    0.0000
0.0000    49.8535 62.3047 49.8535 0.0000
0.0000    37.3047 49.7070 37.3047 0.0000
0.0000    49.8535 62.3047 49.8535 0.0000
0.0000    100.0000    100.0000    100.0000    0.0000

where there is a tab (created using the escape sequence "\t") between pairs of values, but not at the end of the lines. Fixed precision of 4 still applies, but the width of each item is not set for this part.

In a blank excel spreadsheet import these values by using copy and paste. Copy the tab separated values using your mouse and the copy menu in your browser. Then, in a new workbook in Excel, use the "Edit" menu and select "Paste Special..." then select "Text" in the "As:" block and push the "Ok" button. This should load the values into the cells of the spreadsheet. Select the data you just pasted in and select "Insert" then "Chart" then "Surface". This should add a nice surface plot of the steady state values into your excel workbook. We hope this gives you a warm feeling (it's a hotplate!).
Items Evaluated by the TA's Inspection (25 points)

    Adherence to the style guidelines
    You do NOT need to write three test cases for this lab
    Use 2 dimensional arrays of doubles (not vectors nor any other mechanism) to manage the plate values. (25 points)
    You must use all of the values in the array to determine if it is time to stop iterating in part 3 (for example, you may not just check one value). (15 points)

Notes

Be careful setting fixed, precision and width.

The output is wide and thus a little hard to read. Running your code in Visual Studio gives you more room to see the output but eventually you will have to run it in zybooks for submission. If you are having trouble seeing the output in zybooks, you can select in the results box and move your mouse to the right or use the arrow keys (depending on your browser). You can also copy your results from the results box and pasting them into notepad, wordpad, textedit or some other editor so that you can see more of the true width.

As usual we have provided sample output below, but that is output from a smaller 5X5 plate. If you correctly used a constant for the size of the plate, you should be able to easily also run your code at 5X5 and compare your output to the output given below. This might help you with debugging. Also, in the 20X20 plate, the final value at plate[3][3] (that is, 4 in and 4 down) is 48.3696.

Some of the submission tests do not show the entire output. Some of the values will remain hidden.
Sample Output

Your output should look like the output shown below; but of course your output will be for a 20 X 20 array not just the 5 X 5 shown here.

Hotplate simulator

Printing initial plate...
    0.0000,  100.0000,  100.0000,  100.0000,    0.0000
    0.0000,    0.0000,    0.0000,    0.0000,    0.0000
    0.0000,    0.0000,    0.0000,    0.0000,    0.0000
    0.0000,    0.0000,    0.0000,    0.0000,    0.0000
    0.0000,  100.0000,  100.0000,  100.0000,    0.0000

Printing plate after one iteration...
    0.0000,  100.0000,  100.0000,  100.0000,    0.0000
    0.0000,   25.0000,   25.0000,   25.0000,    0.0000
    0.0000,    0.0000,    0.0000,    0.0000,    0.0000
    0.0000,   25.0000,   25.0000,   25.0000,    0.0000
    0.0000,  100.0000,  100.0000,  100.0000,    0.0000

Printing final plate...
    0.0000,  100.0000,  100.0000,  100.0000,    0.0000
    0.0000,   49.8535,   62.3047,   49.8535,    0.0000
    0.0000,   37.3047,   49.7070,   37.3047,    0.0000
    0.0000,   49.8535,   62.3047,   49.8535,    0.0000
    0.0000,  100.0000,  100.0000,  100.0000,    0.0000

Printing final plate for excel...
0.0000    100.0000    100.0000    100.0000    0.0000
0.0000    49.8535 62.3047 49.8535 0.0000
0.0000    37.3047 49.7070 37.3047 0.0000
0.0000    49.8535 62.3047 49.8535 0.0000
0.0000    100.0000    100.0000    100.0000    0.0000
