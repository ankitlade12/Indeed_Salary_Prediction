# Indeed_Salary_Prediction #

**Aim** To predict salaries based on features such as job Location, job title.

**Models**

* LogisticRegression
* DecisionTree Classifier
* RandomForest Classifier
* AdaBoost Classifier

**Analysis**

* Scraping indeed job website based on parameters title, location, url, date posted, summary.

* Cleaning location column and considering states, salary column with an explicit salary by a year. EDA shows that median salary is 71200 $ a year so splitting of salaries is done between high and low considering the median. Baseline accuracy: 0.5010526315789474.  

* In order to model using location as feature, dummifying is necessary. LogisticRegression with GridSearch CV score 0.5710526315789475, DecisionTree with GridSearch CV score 0.6078947368421053, RandomForest with GridSearch CV score 0.6105263157894736 and AdaBoost with GridSearch CV score 0.5842105263157895. By looking at the coefficients higher salaries are associated with location like CA and DC.

* Categorizing company and job titles by keywords, dummifying variables and joining the new df with dummified location. EDA shows that many job postings include "analyst" in the title.

* Converting df to sparse matrix to make calculations fater(Multi Feature Modelling). LogisticRegression with GridSearch indicate that keywords like "Senior" ,"Scientist" are associated with higher salaries, whereas "Junior", "Analyst" are indicator oflow salaries. DecisionTree with GridSearch CV score 0.6894736842105262, RandomForest with GridSearch CV score 0.6763157894736842 and AdaBoost with GridSearch CV score 0.6131578947368421.

* To address problem of misclassifying a lower paying job rather than telling incorrectly that they would get a high salary job need to minimise false positives by improving precision score and threshold. Increasing threshold to 60% and  classifying anything less than 60% probability as low income makes model less accurate but with a higher precision. Trade-off is shown by the roc curve.
