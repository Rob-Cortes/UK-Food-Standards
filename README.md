# nosql-challenge

The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. In this exercise, we perform CRUD operations on the UK Food database. 

## Part 1: Database and Jupyter Notebook Set Up
First, in our Terminal, we import data from the establishments.json file into MongoDB. We name the database 'uk_food' and the collection 'establishments'.

In Jupyter Notebook (NoSQL_setup_starter.ipynb), we import PyMongo so that we can work with the database in Python. After importing PyMongo, we create an instance of the Mongo Client and confirm that the client has connected to the database and loaded the data properly. Then we assign the establishments collection to a variable.

## Part 2: Update the Database
In this section, we add a restaurant to the database. Initially, we have the following information for the restaurant:

{
    "BusinessName":"Penang Flavours",
    "BusinessType":"Restaurant/Cafe/Canteen",
    "BusinessTypeID":"",
    "AddressLine1":"Penang Flavours",
    "AddressLine2":"146A Plumstead Rd",
    "AddressLine3":"London",
    "AddressLine4":"",
    "PostCode":"SE18 7DY",
    "Phone":"",
    "LocalAuthorityCode":"511",
    "LocalAuthorityName":"Greenwich",
    "LocalAuthorityWebSite":"http://www.royalgreenwich.gov.uk",
    "LocalAuthorityEmailAddress":"health@royalgreenwich.gov.uk",
    "scores":{
        "Hygiene":"",
        "Structural":"",
        "ConfidenceInManagement":""
    },
    "SchemeType":"FHRS",
    "geocode":{
        "longitude":"0.08384000",
        "latitude":"51.49014200"
    },
    "RightToReply":"",
    "Distance":4623.9723280747176,
    "NewRatingPending":True
}

We fill in the restaurant's BusinessTypeID by finding another establishment with a BusinessType of "Restaurant/Cafe/Canteen" and returning the corresponding BusinessTypeID. One we know the appropriate BusinessTypeID, we update the new restaurant's information.

Next, we eliminate any establishments located in Dover, an area we are not interested in. After removing these establishments, we call collection.count_documents() to verify that they were deleted.

Lastly, we use collections.update_many() convert certain values from strings to numbers. Specifically, we convert latitude and longitude to decimal numbers, and RatingValue to integer numbers.

## Part 3: Exploratory Analysis
In NoSQL_analysis_starter.ipynb, we explore the database that we set up in the previous section. 

First, we determine which establishments have a hygiene score equal to 20.

Next, we find the establishments in London that have a RatingValue greater than or equal to 4.

Next, we find the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score (a lower hygiene score is better), nearest to the new restaurant added, "Penang Flavours".

Lastly, we find the number of establishments in each Local Authority area that have the best possible hygiene score (i.e., 0). We sort the results from highest to lowest, and print out the top ten local authority areas, as shown below:

![image](https://github.com/Rob-Cortes/nosql-challenge/assets/124944383/2e474e86-44f6-4646-b25c-47d239bcdf1a)
