# CRISP-DM-model-on-Seatle-Airbnb

1. Installation 
   - Anaconda 4.5.11 distribution 
   - Python 3.6

2. Project Motivation

Using the Cross-Industry Standard Process of Data Mining (CRISP-DM) the Seatle Airbnb dataset is collected, cleaned and engineered, such that a good number of business insights are gathered, of which the following five questions are focused upon:

- How many Airbnb listings does each neighborhood in Seatle posses?

- Which are the neighborhoods with the most expensive listings?

- Which listings were available on December 25 with entire home apartments, which got a review in the last 6 months?

- Which listing hosts, reside in their neighborhood?

- Provide a competitive market price for a newly added Airbnb listing given its attributes?


3.File Descriptions

This repository consists of:
- A Descriptive Jupyter Notebook
- The corresponging python 3.6 file
- Three datasets:
   . Listings (3818 rows by 92 columns)
     Contains a complete description of each listing attributes including the price tag 
   . Calendar (1048575,4)
     Contains all the available listings at some point in time 
   . Reviews (84849,6)
     Contains all possible review related attributes made on each listings and their respective scores
  NB: The Listings and Calendar datasets are using in this project, which much fucos on listings for machine learning modeling

4. How To Interact With Your Project 

This project follows the CRISP-DM approach with ample orientations provided on the Jupyter Notebook and A Medium Blog post on the following link: https://medium.com/@tsakunelsonz/top-5-airbnb-analytical-questions-answered-aa13101a6009?source=friends_link&sk=ebf7dbce9873ebf7853849f4017d9048

Upon fitting and training our LinearRegression Model to predict the Price of a potential Airbnb listing given its attributes, we get an RMSE score of 0.588

The Linear regression Model provides good predictive metrics for prices up to $400, but starts performing for prices from $400 to $1000. Three solution can be adopted to solve this issue:
  - Upsampling the number of listings with prices greater than $400
  - Downsampling the number of listings with prices less than $400
  - Applying stratified cross-validation to improve metric performance
  - Applying the K-Nearest Neighbors model and comparing the metric results from both models.

5. Licensing, Authors, Acknowledgements
Licensing
Code and documentation copyright 2018 the Author's  Code released under Udacity License

Author
Nelson Zange TSAKU 

Acknowledgements 
  Much appreciations to Udacity for hands of advise and Orientation
  Much appreciations to Seattle Airbnb community for prividing relevant datasets
  
