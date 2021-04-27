Design Document for Hash Table

Problem Statement
We have to implement a Hashtable where multiple accounts with PAN can be stored and retrieved. The Hastable should use 2 level of hashing. First one is based on the type of PAN (Person, Company, Firm etc. ) and the second level of hashing based on the quadratic probing

Solution/Design Details
1.	Input and Output to the Program
The program should have a command line user interface where it will prompt the following to take input data from user
i)	Please provide the file path with account data to load to the hash table
Sample Input C:\\TestData\AccountData.txt
The file which it will read and load the data to the hash table. The file needs to have data on a CSV format as below
ALSPP2346C  , John Doe,  New Delhi ….
ii)	Please provide the file path with account data to load to the hash table
Sample Input C:\\TestData\PANsToSearchFor.txt
This input data will have list of PANs to search for in the loaded hash table.
iii)	Please provide the file path where you want to write the output (optional)
The program will prompt this only when it’s not started with the flag -Console
It will list the account details from the Hashtable either in the Console or in a file given in the above input depending on which mode its started. 
ALSPP2346C , Found, John Doe, New Delhi 
ALKPP2347C , Not Found
The program should do appropriate validation to make sure the file locations and data formats within the file are correct. 

Classes and Methods 
HashTableClient – This class will handle the user input/output and will be the main interface to the Hash table
MyFirstLevelHashTable –  This will be a hash table implementation with following methods
This will internally contain an array with 10 elements with each element of the array pointing to a particular object of SecondLevelHashtable 
public void addEntry ( Account account) – This method uses firstLevelhashCode to identify appropriate SecondLevelHashtable object and call an addEntry method on that.
public void searchDetails(String pan) – This method first identifies which SecondLevelHashtable the account information could be and then uses quadratic probing to find the account details.
SecondLevelHashtable – An implementation of hash table encapsulating an array. The probing sequence is implemented using quadratic probing. 
It should have following methods
public void addEntry ( Account account) – This method calculates a hash value of of the account based on the ASCII values of the different characters in the string and then uses quadratic probing to store the value in the array.  If it cannot find an slot it calls the rehash() method to increase the size of the array.  
private void rehash() – This method is called when the addEntry() method cannot find a slot in the array and then doubles the array size and then copies over the data based on new function. 
public Account searchDetails(Account account) – This method uses quadratic probing to find the account details in the current object
Account – A value object to hold the details of the PAN holder. This will have setter and getter methods. 
public  int firstLevelhashCode() – Returns the first level hash value corresponding to the  first level hash table
public int  secondLevelHashCode() – Should return the second level hash code calculating from a PAN of a given account

Test Cases
-	Test whether initialization happens correctly. 
-	Test whether the first level hashing happens correctly
-	Test whether second level hashing happened correctly
-	Test whether the rehashing happens correctly
-	Test a successful search
-	Test a unsuccessful search





 

  



