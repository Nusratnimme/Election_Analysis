# Election Analysis

## Project Overview
Tom, a Colorado Board of Election Employee, needs to complete an audit of the results of a recent local congressional election in Colorado. The votes are from three counties cast to three candidates. With some assistance, he needs to write a script in python for analyzing the data.

## Resources
Data Source: election_results.csv
Software: Python 3.7.6, Visual Studio Code: 1.63.2

## Purpose of Election Audit

The purpose of this analysis is to audit the tabulated results for a US congressional precinct in Colorado to get the following:

- Total vote counts;
- The voter turnout for each county and their percentage;
- Votes received by each candidate and their percentage;
- The county with the highest voter turnout;
- The winning candidate.

## Analysis of Election Audit

**Creating variables, list and dictionaries to store results:** using some dependenies, the election data was imported to Python and a text file was opened to save the results of the analyses. Next, a variable to count total votes, and lists and dictionaries for candidates and counties were created to hold vote counts, percentages, etc. Variables were also created to determine the winning candidate, winning vote count and percentage, as well as vote counts by county and largest county by voter turnout.

```
# Initialize a total vote counter.
total_votes = 0

# Candidate Options and candidate votes.
candidate_options = []
candidate_votes = {}

# 1: Create a county list and county votes dictionary.
county_options = []
county_votes = {}

# Track the winning candidate, vote count and percentage
winning_candidate = ""
winning_count = 0
winning_percentage = 0

# 2: Track the largest county and county voter turnout.
winning_county = ""
winning_county_count = 0
winning_county_percentage = 0
```

**Reading the data:** the csv.reader function below converts the file into a list of dictionaries and then we exclude the header row.

```
with open(file_to_load) as election_data:
    reader = csv.reader(election_data)

    # Read the header
    header = next(reader)
```

**Counting total votes:** the for loop below extraxts the candidate name and county name for each record and adds the vote to the total votes count.

```
# For each row in the CSV file.
for row in reader:

        # Add to the total vote count
        total_votes = total_votes + 1

        # Get the candidate name from each row.
        candidate_name = row[2]

        # 3: Extract the county name from each row.
        county_name = row[1]
```

**Counting votes by county and candidate:** within the for loop, we run an if statement to get all unique county names and add corresponding votes to them. Next, these results were saved in the txt file and printed to the command line. Similar approach was applied to count votes by candidates.

```
  # 4a: Write an if statement that checks that the
        # county does not match any existing county in the county list.
        if county_name not in county_options:
           
            # 4b: Add the existing county to the list of counties.
            county_options.append(county_name)

            # 4c: Begin tracking the county's vote count.
            county_votes[county_name] = 0

        # 5: Add a vote to that county's vote count.
        county_votes[county_name] += 1
```

**Calculating percentage of votes by county and candidate:** to get total votes and percentage of votes for each county, we use another for loop which iterates over all counties. Next, the results are saved in the text file and printed to the command line as before. Similar method is applied to get votes and their percentages by candidates.

```
# 6a: Write a for loop to get the county from the county dictionary.
    for county_name in county_votes:
        # 6b: Retrieve the county vote count.
        votes = county_votes.get(county_name)
        
        # 6c: Calculate the percentage of votes for the county.
        vote_percentage = float(votes) / float(total_votes) * 100

         # 6d: Print the county results to the terminal.
        county_results = (
            f"{county_name}: {vote_percentage:.1f}% ({votes:,})\n")

        print(county_results, end="")
        
         # 6e: Save the county votes to a text file.
        txt_file.write(county_results)
```

**Determining the winner:** by using an if statement within the for loop, we determine the county with the largets turnout, save the result in the text file and print it to the command line. The winning candidate, votes received by them and their percentage are determined similarly.

```
 # 6f: Write an if statement to determine the winning county and get its vote count.
        if(votes > winning_county_count) and (vote_percentage > winning_county_percentage):
            winning_county_count = votes
            winning_county = county_name
            winning_county_percentage = vote_percentage

    # 7: Print the county with the largest turnout to the terminal.
    largest_county_turnout = (
        f"\n-------------------------\n"
        f"Largest County Turnout: {winning_county}\n"
        f"--------------------------\n"
    )
    print(largest_county_turnout)

    # 8: Save the county with the largest turnout to a text file.
    txt_file.write(largest_county_turnout)
```

## Election Audit Results
- There were **369,711** votes cast in the congressional election.

- County Results

    - Jefferson county accounted for 10.5% of total votes (38,855 votes).
    - Denver county accounted for 82.8% of total votes (306,055 votes).
    - Arapahoe county accounted for 6.7% of total votes (24,801 votes).

- The county of **Denver** had the largest turnout.

![County_Results](https://github.com/Nusratnimme/Election_Analysis/blob/main/Resources/County_Results.png)

- Results of the candidates were:

    - Charles Casper Stockham received 23.0% of total votes (85,213 votes).
    - Diana DeGette received 73.8% of total votes (272,892 votes).
    - Raymon Anthony Doane received 3.1% of total votes (11,606 votes).

- Winning candidate

    - Name of the candidate: **Diana DeGette**
    - Winning vote Count: 272,892
    - Winning vote percentage: 73.8%

![Candidate_Results](https://github.com/Nusratnimme/Election_Analysis/blob/main/Resources/Candidate_Results.png)

- Election-Audit Results

![Election_Audit_Results](https://github.com/Nusratnimme/Election_Analysis/blob/main/Resources/Final_Election_Results.png)

## Election-Audit Summary
It is possible to make the script used to do this analysis more generic to analyze any election data.

Below are the hardcoded assumptions in this script:
- that the data are in a file called election_results.csv (separated by comma) which is within a folder called Resources at the same level of the script;
- that the first row is the header;
- that second and third fields contain the county and candidate name, respectively.

To enable the script to analyse any election data, we need to add questions or instructions in the script about the file name and path, the separator, whether it has a header, and which columns (titles or positions) contain county and candidate name.

For example, the user can be asked to save the file in the same folder as the script, provide file name separator which can be used later to read the file as below:

```
print("Please save the data file in the same folder as this script.")
file_name = input("Please provide name of the file election data are contained in (including extension):")
sep = input("Please specify the separator of the fields/columns (e.g. , \t):")

with open(file_name) as election_data:
    reader = csv.reader(election_data, delimiter = sep)
```

Another example could be to ask the user to specify the position of the county name column and then use it to extract the county name:

```
county_col = int(input("Enter position of column containing county names:"))
county_name = row[county_col]
```
