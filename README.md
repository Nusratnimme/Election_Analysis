# Election_Analysis

## Project Overview
Tom, a Colorado Board of Election Employee, needs to complete an audit of the results of a recent local congressional election in Colorado. With the help of an assistant he will write a script in python for analyzing the data. At the end of the analyses the python script will be able to give the following details:

1. Total number of votes cast.
2. Complete list of candidates who received votes.
3. Total number of votes each candidate received.
4. Percentage of votes each candidate received.
5. Winner of the election based on popular vote.

## Resources
Data Source: election_results.csv
Software: Python 3.7.6, Visual Studio Code: 1.63.2

## Initial Summary
The analyses of the election show that:

- A total of 369,711 votes were cast in the election.

- The candidates were:

    - Charles Casper Stockham
    - Diana DeGette
    - Raymon Anthony Doane

- Results of the candidates were:

    - Charles Casper Stockham received 85,213 votes, accounting for 23.0% of total votes.
    - Diana DeGette received 272,892 votes, accounting for 73.8% of total votes.
    - Raymon Anthony Doane received 11,606 votes, accounting for 3.1% of total votes.

- The winner of the election was: **Diana DeGette**

## Purpose of Election Audit

The purpose of this analysis is to audit the tabulated results for a US congressional precinct in Colorado. The data are from three counties, on votes received by three candidates. By analyzing the data, the script will provide the following:

- The voter turnout for each county.
- The percentage of votes from each county out of the total count.
- The county with the highest turnout from the data source.

## Election Audit Results
- There were 369,711 votes cast in this congressional election, which matches with the initial election summary.

- County Results

    - Jefferson county accounted for 10.5% of total votes with 38,855 votes.
    - Denver county accounted for 82.8% of total votes with 306,055 votes.
    - Arapahoe county accounted for 6.7% of total votes with 24,801 votes.

- The county of Denver had the largest turnout.

[Screenshot]

- Results of the candidates were:

    - Charles Casper Stockham received 23.0% of total votes (85,213 votes).
    - Diana DeGette received 73.8% of total votes (272,892 votes).
    - Raymon Anthony Doane received 3.1% of total votes (11,606 votes).

- Winning candidate

    - Name of the candidate: Diana DeGette
    - Winning vote Count: 272,892
    - Winning vote percentage: 73.8%

[Screenshot]

- The final result of the election is as follows:
  
  - The county of Denver had the largest turnout with 82.8% of total votes (306,055 votes).
  - Diana DeGette won the election receiving 73.8% of total votes (272,892 votes).

[Screenshot]

## Election-Audit Summary
It is possible to make the script used to do this analysis more generic to analyze any election data.

Below are the hardcoded assumptions in this script:
- that the data are in a .txt file separated by comma;
- that the first row is the header;
- that second and third fields contain the county and candidate name, respectively.

To enable the script to analyse any election data, we need to add questions in the script about the format of the file (.txt, .csv, etc.), whether it has a header, and which columns (titles or positions) contain county and candidate name.

For example, the user can be asked about the title of the county name column and the answer can be saved as below:

```
print("Enter title of column containing county names:")
county_col = input()
```
