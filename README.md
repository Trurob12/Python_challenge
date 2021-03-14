# Python_challenge
""" Python Homework  PyPoll
    Python Script that will input election data formated in a csv
    file containing voterId, county, candidate.
    Output to screen and file lists each candidates votes and % of total
    and states total votes and winner


        Truman Roberts """
import os
import csv

# request file names for input and output, declair the subfolder for holding the data
# If i had time I would add an IF statement to prompt again if file not found

input_file = input(" Please enter the name of the data file: ")
input_file = input(" Please enter the name of the data file (with csv ext): ")
csvpath = os.path.join("raw_data", input_file)
output_file = input("Please enter the name of the Text file to hold the election results (with txt ext): ")

# open the data file into the csv reader

@@ -16,9 +31,11 @@

    candidates = {}

# loop through the data, adding the candidates and running a vote count 
# for each (held as value to the candidate Key)
# skipping the header line, then loop through the data, adding the  
# candidates and running a vote countfor each 
# (held as value to the candidate Key) 

    next(csvreader)
    for row in csvreader:
        if row[2] not in candidates.keys():
            candidates[row[2]] = 0
@@ -33,22 +50,31 @@
    for votes in candidates.values():
        total_votes = total_votes + votes

   # Output formating for the election results 

   # Output formating for the election results & create the output file for the results
    text_file = open(output_file, "w")
    print(" ")
    text_file.write(" \n")
    print("  ")
    text_file.write(" \n")
    print("         Election Results")
    text_file.write("         Election Results\n")
    print("------------------------------------------")
    text_file.write("------------------------------------------\n")
    print("   Total Votes : " + str(total_votes))
    text_file.write("   Total Votes : " + str(total_votes)+ "\n")
    print("------------------------------------------")
    text_file.write("------------------------------------------\n")

   # calculate and format the candidates percentage of total votes

    for each, votes in candidates.items():
        rate = votes/total_votes
        print(each + " : " + '{:.1%}'.format(votes/total_votes) + " ( " + str(votes) + ")")
        text_file.write(each + " : " + '{:.1%}'.format(votes/total_votes) + " ( " + str(votes) + ")\n")        
    print("------------------------------------------")
    text_file.write("------------------------------------------\n")
    print("  ")
    text_file.write(" \n ")

   # to determin the winner, loop through the candidates setting the candidate
   # with the most votes as the winner
@@ -60,6 +86,11 @@
            most_votes= candidates[politician]

    print('The winner is : ' + winner) 
    text_file.write('The winner is : ' + winner + "\n") 
    print(" ")       
    text_file.write("\n ")
    print("------------------------------------------")
    print("  ") 
    text_file.write("------------------------------------------\n")
    print("  ")
    text_file.write("  \n")
    text_file.close() 


