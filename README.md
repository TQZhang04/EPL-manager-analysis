# New Manager Myth?

## Exploring the Effect of a Managerial Change on a Team's Performance in the Premier League

![Logo of the English Premier League](imgs/EPL-logo.webp "EPL LOGO")

### Project Description

The overall purpose of this project was to determine whether teams in the EPL saw genuine bumps in performance in the short term after bringing in a new manager, a phenomenon known as the "new manager bounce". To do this, we looked at various match statistics and changes in manager for teams in the EPL since 2017. During the exploration phase, we primarily focused on teasing out how our match metrics were distributed, and how they changed over the time period (~2017 to 2022). At the end of this phase, we ultimately hit-up on the metrics that had the most positive and negative effects on the result of the game. In our final analysis, we checked if the first ten games of each newcomer exhibited an increase in performance as compared to their predecessor's entire term. Our results told us that only a very small proportion (~2%) of changes correlated with an increase in performance. Thus, we could not find substantial evidence in our dataset to support the claim that a change in manager causes a bump in short-term performance.

### Setup

### Data Overview

Each dataset includes the following information:
- Dataset #1
  - Dataset Name: English Premier League Match Stats
  - Link to the dataset: https://www.kaggle.com/datasets/saife245/english-premier-league?select=final_dataset.csv
  - Number of observations: 8020
  - Number of variables: 40 total (with 18 relevant)
- Dataset #2
  - Dataset Name: Managerial Changes
  - Link to the dataset: https://www.transfermarkt.us/premier-league/trainerwechsel/wettbewerb/GB1/plus/?saison_id=1992
  - Number of observations: 410
  - Number of variables: 14
  
- Dataset #3
  - Dataset Name: Web-Scraped Passing data for each team per-match. 
  - Link to the dataset: https://fbref.com/en/comps/9/Premier-League-Stats
  - Number of observations: Roughly 2805
  - Number of variables: 3 (Pass completion%, team, and date)

The first dataset was downloaded from kaggle, where the uploader retrieved it from [footystats.org](https://footystats.org/england/premier-league). It includes metrics collected from matches in the Premier League from 2000 to 2022. Each observation corresponds to a single match. It contains a lot of statistics, ranging from goals scored, shots taken, to more abstract betting odds data the home and away teams for each match. The relevant variables included goals scored, match result, shots, shots on target, fouls committed, corners, and red/yellow cards earned. This dataset came pretty cleaned already, but we needed to increase the granularity, ensuring we have one row for each team for each match, not just one row per match.
 - For this data set, our relevant/top variables are:
     - Shots: all attempted shots	
     - ShotsOnTarget: shots that met the goal in some capacity (woodwork doesn't count)	
     - FoulsCommited	
     - Corners 	
     - YellowCardsEarned 	
     - RedCardsEarned 	
     - IsHome 	
     - Won
     - goal_acc (derived metric)
     - PointsWonByResult (derived metric)

The second dataset was scraped from the website [transfermarkt.us](https://www.transfermarkt.us/premier-league/trainerwechsel/wettbewerb/GB1/plus/?saison_id=1992). It includes the data on managerial changes for each team in the Premier League. Each observation corresponds to a manager, and it includes data such as the manager's successor, the date they left, and their first/last match as manager.
- We are just using this dataset for a timeline of succession for each manager for as many clubs as we can.


The third dataset was scraped from the website [fbref.com](https://fbref.com/en/comps/9/Premier-League-Stats). The website includes passing completion data for each club in the premier league on a season-by-season, match-by-match basis. We scraped the passing completion percentage column for each match a team played across as many clubs as the data was available (stretching back to the 2017 season).

### Code Structure
Our project is broken into several steps: Data Cleaning, EDA, and Final Analysis. The code for each step exists in separate notebooks, being DataCleaning.ipynb, EDA.ipynb, and Analysis.ipynb respectively. However, all the code was polished and compiled into the FinalProject.ipynb. There, you'll also find more in-depth descriptions of our process for each step and more insights into how we reached our conclusion.

Code used in webscraping is found in manager_changes.ipynb.

### Conclusion

After having done our analysis, we have come to the conclusion that **NO, there isn’t a trend in teams being more successful in the 10 games post-sacking a manager as compared to the previous reign.** This conclusion is surprising because it flies directly in the face of the prevailing belief among European football fans that a change in manager is akin to a power-up in success. Most fans are always talking about how they can at least expect some sort of short-term success just on the merits of the change alone. 

If anything, this conclusion supports the idea that clubs should be much more patient with their existing coach and try to stick by him through rough patches in form. Moreoever, this conclusion suggests that **when a team is experiencing a genuine lack of success on the pitch, the club should look at revamping other, more fundamental structures (such as scouting, recruitment, investment, etc..) rather than relying on changing just one man’s job.** Often times, the manager becomes the scapegoat for the team’s failures when in reality, as our conclusion supports, the actual source of the problem most likely lies elsewhere.

### Discussion and Future Work

One limitation of the analysis was the fact that we only used a select sample of metrics to form these conclusions. We made the decision to limit our analysis to unbiased data that we could confirm the generation process of, to keep our analysis as objective as possible. Doing further analysis with more complex metrics might have revealed more about what managers can actually affect, such as strategy, team culture, etc.

Additionally, there can be varying reasons as to why the manager change took place in the first place, which can have an effect on the performance of the club after the switch took place. For example, a manager that was sacked probably left because of how badly a team was doing, which primes the results after the switch to improve. On the other hand, if the manager voluntarily stepped down, it might not lead to the “bounce” we are looking for, and more likely would lead to less of a performance increase. Thus, including the reason for a manager change in the analysis might have allowed us to see when exactly there would be a bounce.

Lastly, the presence of confounding variables is especially significant in a broad analysis of club performance, as there are lots of reasons why a team can do better or worse after a manager change that don’t necessarily have anything to do with the manager. Injuries, the strength of the teams they are facing, financing, and general skill level of the team all profoundly affect team performance, with or without the change of a manager. By controlling for these in further analysis, we could zero in on the effect of the manager.

### Individual Contributions

- Clark Yang: Wrote code for webscraping tackle data, created presentation and wrote script
- Erich Then: Webscraped, cleaned, and did analysis for passing data; compiled analyses in conclusion
- Kabir Shergill: Wrote code to combine datasets, wrote descriptions for cleaning and analysis, summarized analyses in conclusion
- Tianqi Zhang: Handled data cleaning for the metrics dataset, wrote code for the final analysis portion, organized final report

### Acknowledgements

We would like to thank Dr. Shannon Ellis and Kunal Rustagi for providing feedback and mentoring on this project. Their invaluable insights helped us create a more polished final product. We would also like to thank the teams at FootyStats and TransferMarkt for providing such clean, workable data from the get-go.