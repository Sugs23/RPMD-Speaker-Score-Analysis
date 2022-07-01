# Speaker-Score-Analysis
Debate Speaker Score Analysis

This R code is highly specific and has very narrow usage. It is used to access speaker scoring consistency in parliamentary debate tournaments.
It was made on RPMD debate data (link: https://rpmd2021.calicotab.com/rpmd21/).
For using on any other tourney, data preprocessing and cleaning will be required.

It will be difficult to understand what this code does without context on how Debating tournaments work.
I will therefore try to provide a brief explanation.

In debating tournaments there are multiple rounds where teams are matched against each other and recieve points based on whether they win or not. 
Additionally every speaker in the debate also gets speaker points, the higher the speaker points, the better the debater is deemed to be.
As teams win the rounds, they are matched with other teams who have won the same number of rounds, and similarly for teams who have lost rounds.

This means that 'good' debaters get paired up with 'good' debaters and 'bad' debaters get paired up with 'bad' debaters. 
Being in a round where all debaters are good also means that the individual speaker scores will be higher for them.
As this is done more times, the scores of good debaters shows a slow albeit positive trend and vice versa for bad debaters.
There needs to be a positive high correlation between subsequent rounds if the judges score the participants perfectly.

WORKING:

FUNCTION 1
The code calculates a correlation matrix that has correlation coefficients between the speaker scores awarded in all the rounds.
It takes the weighted mean of all the correlations using a factor of 1/2^(r_a-r_b + 1) where r_a and r_b are the position of 2 rounds and r_a > r_b.
If the result is very small it means the judges are marking arbitrarily for individual speakers
i.e, good debaters getting lower scores and worse debaters getting higher scores.

FUNCTION 2
The code calculates the consistency in the total team speaker scores with their final rank in the tournament.
In debate tournaments a teams rank is first decided by their points (how many rounds they won) and then their speaker scores in case of tie.
If a team is ranked above another team, it is implied they are better and hence they should also have higher scores.
This code calculates another index to account for every time a team ranks higher to a team it lower scores than and scales that according the difference in ranks.
If the result is lower it means that teams with low speaker points are getting higher team points .
which means judges from lower rooms are marking teams in those rooms higher and vice versa

FUNCTION 3
The code creates a .txt file and saves the output there.

Assumptions:
1) Debater will have uniform debating skills throughout the tournament 
i.e, good debaters will consistently give good speeches and vice versa
2) Rooms that have bad debaters will have bad debates and hence an overall lower score



