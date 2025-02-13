# SUTT_Backend_Task1
This code can be used to parse the Mess Menu details for a particular timeframe from an Excel file and write them to a JSON file, such that the information is presented in a much neater, readable format.
First, the openpyxl and json modules are imported, to utilise their functionalities.
Then, the workbook is opened by specifying its path on the machine, after which the sheet, which is to be worked on, is assigned to the object "sheet".
The maximum number of columns in the sheet, which is going to help us iterate through them as per our requirement, is obtained through the max_column method of the sheet object. This number is usually 1 greater than the actual number of columns, as per the functionality of the max_column method (it returns 1 for a sheet with no non-empty columns).
After this, a dictionary object "data" is created in order to store all the parsed data.
Now, we enter a for loop with range as 1 to the column_no, which iterates through the columns, and also contains 3 other for loops which iterate through the rows as per certain conditions.
For example, when i=1, we work with just column no. 1.
Then, according to the spreadsheet, breakfast items begin from row 4, and continue till a particular row depending on how many items are present in the excel. to tackle this, a
function is created which would determine at which row the last breakfast/lunch/dinner item is present, by checking when the "day" repeats in that column.
In each loop, we obtain the required cell values using the syntax, and then check for two conditions:
1) whether the cell is blank (we verify this by checking if the item turns to be of NoneType)
2) whether the cell contains ******* (we verify this by checking if the item contains * )
once both conditions are satisfied, the items are appended to the respective list objects created beforehand (breakfast,lunch,dinner) as per the correct logic.
Next, the lists are inserted into the menu dictionary (also created beforehand), with the proper keys.
Finally, the menu dictionary is inserted to the main data dictionary, with key being the date. This is done how many ever times the loop executes.
now that the dataset is ready, it needs to be written to the json file. for this, json.dump() method is utilised. to write the dictionary object in the proper format, indent=2 is added to the argument of the method.
