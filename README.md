# Exploring Factors Influencing Survival on the Titanic Using Python

## Introduction
There were 2224 passengers and crew members on the Titanic that sank in 1912. Of those on board, 1502 survived. In this project we are going to use data provided by [Kaggle](https://www.kaggle.com/competitions/titanic) to see which demographics were more likely to survive the crash. There are two parts to this projects. In the [first part](#), the dataset was cleaned up and prepared for further analysis. In the [second part](#), we took a deeper dive into the data and performed some explantory analysis.

## Original dataset
The data sets consist of an ID column, a response variable and various features. This is the information provided by the source:
- `PassengerId`: unique ID number for each passenger;
- `Survived`: 1 if passenger survived the disaster, 0 otherwise (target);
- `Pclass`: ticket class (1 = 1st, 2 = 2nd, 3 = 3rd);
- `Sex`: sex of the passenger;
- `Age`: age in years;
- `SibSp`: number of siblings/spouses aboard the Titanic;
- `Parch`: number of parents/children aboard the Titanic;
- `Ticket`: ticker number;
- `Fare`: passenger fare;
- `Cabin`: cabin number;
- `Embarked`: port of embarkation (C = Cherbourg, Q = Queenstown, S = Southampton).

In the folder [nationality](https://github.com/manalelabdellaoui/titanic_eda/tree/main/nationality), you'll find the nationalities of the passengers predicted using their names. These predictions were done by [Warren Elder](https://www.kaggle.com/warrenelder) who shared his findings [here](https://www.kaggle.com/datasets/warrenelder/titanic-passenger-nationalities/data). We used these predictions to create another column for our dataset:
- `Nationality`: nationality predicted using passengers' names.

## Findings
- 👶 **Age**: survivors were slightly older on average, though infants had a higher survival rate.
- 🚻 **Sex**: a strong predictor. Most women survived, while most men did not.
- 🎫 **Ticket class & fare**: higher-class passengers and those with more expensive tickets had better survival odds. Fare was adjusted to account for shared tickets.
- 👨‍👩‍👧 **Relatives & companions**: traveling with 1–2 family members or companions improved survival odds. Large groups had lower survival rates. A new `Solo` feature was created.
- 🎩 **Titles**: Common titles (Mr., Miss, Mrs., Master) aligned closely with sex and age, offering no additional predictive power beyond those variables.
- ⚓ **Port of embarkation**: passengers from Cherbourg had the highest survival rate, likely due to a higher proportion of 1st class and female passengers.
- 🛏️ **Deck information**: passengers with a known cabin deck had significantly higher survival rates. A new binary feature `DeckKnown` was created.
- 🌍 **Nationality**: apparent differences in survival across ethnic backgrounds were largely explainable by sex and class distribution. The feature was dropped due to unreliability.

## Feature Selection

After analysis, several features were dropped due to redundancy, unreliability, or low predictive power and new features were engineered. This is the selection of features we ended up with:
- `PassengerId`: unique ID number for each passenger; 
- `Survived`: 1 if passenger survived the disaster, 0 otherwise (target); 
- `Pclass`: ticket class (1 = 1st, 2 = 2nd, 3 = 3rd); 
- `Sex`: sex of the passenger; 
- `Age`: age in years; 
- `Embarked`: port of embarkation (C = Cherbourg, Q = Queenstown, S = Southampton);
- `Missing_Age`: 1 if age is known, 0 otherwise; 
- `SharedTicket`: 1 if ticket is shared with other passengers, 0 otherwise; 
- `TicketGroupSize`: number of passengers sharing passenger's ticket; 
- `IndividualFare`: individual passenger fare;
- `Solo`: 1 if traveling without a companion, 0 otherwise; 
- `DeckKnown`: 1 if deck of the cabin is known, 0 otherwise.
