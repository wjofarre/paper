# paper
paper
Liam O’Farrell
GA – DAT7
Identifying Crime features
Introduction
In several cities in the United States there has been a concerted effort to organize local criminal activity into meaningful data. For the most part, it has been used as a measure total criminal activity and as a law enforcement performance evaluation tool.  Although the data is useful for these purposes it also contains many features that, if identified, could be used to predict criminal activity. If law enforcement can identify what features have the greatest effect on crime they could better allocate their resources at their disposal to reduce it. 
	For a long time the metric by which crime reduction was measured was the total number of arrests made. This is not necessarily the best metric to determine crime rates, as it does not take into account the rate at which crimes are being committed. It would be more accurate to measure crime by the total number of occurrences and then measure crime reduction effectiveness based on the probability of apprehension, total crimes reported and deterrence rate. This project will only focus on the total number of crimes reported as the response variables with other factors such as weather, neighborhood, distance from a police station, resources and perhaps several others as the features.

Data
	The main data set used in this project is crime data from Chicago, IL USA. It was taken from their online open source data website. It contains all the crimes reported starting in 2007 and through 2015. The data contains information about each crime including location, GPS coordinates, neighborhood, type of crime, time of day, date, whether or not an arrest was made and several other pieces of information. Another data set used is from the Chicago Police Department that contains information about the police stations including the GPS coordinates, address and neighborhood it is in. (Data that still remains to be gathered is the city budget for each year for the city police, the total number of officers and the resources available to them)

Data Cleaning
	The collected data had a lot of missing values in its raw form especially in the earlier years. There are many reasons this might have been the case. For example, when a crime is reported often times the victim cannot recall exactly what occurred and may forget what kind of weapon the assailant used (if at all). Because of the massive amount of missing data from the earlier years, the data had been trimmed to only include crime from 2011 and onward as that is when it starts to get more complete.
	The rows with the remaining missing values where dropped from the analysis. The reasons for this being that the data set is very large so dropping incomplete data should not affect the results to dramatically. Additionally it would be difficult to predict what an appropriate placeholder for these values would be and attempting to do so could alter the results if included in the analysis. 

Approach
	The first thing I did for this project is calculate the distance from each reported to the nearest police station using the GPS coordinates from the crime data and the GPS coordinates from the police station addresses. To do this I created a for loop cross checking each crime location with station location and used the Haversine closest distance formula to calculate the difference between the GPS coordinates. Once I had a list of distances for each crime to the nearest police station I added the distance to the data frame to examine as a feature variable. The thought was that the farther away from a police station a crime occurred the less likely there would be an arrest made. This turned out to not be the case. After running a logistic regression on distance and arrest made I found that distance is very weakly correlated with the probability of apprehension. Meaning that the farther away from a police station a crime occurs the more likely an arrest is going to be made. Below is a graph of this logistic regression. The red line is the regression line and it clearly shows a weak positive correlation with distance and the probability that an arrest will occur. 
 
	The box plots also illustrate this point. The right plot is yes and the left one is no.

 
This is slightly counterintuitive as one would expect the probability of apprehension to increase as distance from a station decreases. However, distance is also correlated with higher crime rates. As distance from a station increases the number of reported crimes also increases. These findings suggest that perhaps this problem may be better solved using a regression model rather than a classification model.
Upon further data exploration, I found that crime rates drastically increase during the summer months. There are several reasons this might be the case. The most interesting features that does have a significant effect is students being released from school. During the school year kids are occupied and have a place to go for most of the day but during the summer schools are closed and for some reason that causes crime rates to increase.
An interesting thing to analyze might be the relationship between areas with after school programs and crime rates. If students being in school is related to crime rates perhaps keeping students in school longer would have an impact on these statistics. It could be that the warmer weather causes crime rates to increase but if we find that areas with after schools programs have lower crime rates that would be an interesting finding.

Next Steps
	The next steps would be to gather more data. Most crucial would be city budget especially as it relates to local law enforcement. It would also be helpful to gather data on schools with after schools programs or schools who offer summer programs and how many students attend these programs. This data is proving very difficult to find as there is no public access cite that lists all these programs. They are listed district to district and matching them up to the specific wards listed in the crime data is complicated and could adversely affect the results if done incorrectly.
	Another thing to do would be to analyze the data from district to distrct and see would crimes are most common in what areas. Splitting the data to do this affectively is tricky because there are so many ways to split it. After a few trials it appears that splitting it by ward would make the most sense as they are slightly bigger areas but it is hard to say for sure without having extensive knowledge of the Chicago landscape.




