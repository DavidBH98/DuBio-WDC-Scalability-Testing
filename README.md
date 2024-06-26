# DuBio-WDC-Scalability-Testing

This is a ReadMe for the code utilized in my report on the limitations of the PostgreSQL extension DuBio while at the University of Twente.

To whoever is reading this, if you go looking into my code, I apologize in advance for the mess you will find.

# Overview

This repo is made up of four significant files, 3 jupyter notebook files and a template for an ini file.

database.ini.tmpl is a template for the ini file that must be copied then edited in order for the other files to work properly with the database the code is to be connected to.

duBio_building.ipynb is the primary code, which converts a base database table of clusters of size 2, 3 or 4, into a probabilistic table.

wdctest3.ipynb is a basic setup code meant to extract all data from a specific .json file and insert it into a database over the course of several hours.

graphs v2.ipynb is a basic plotting file that contains a large amount of the data generated over the course of this research and is the method by which I generated the graphs used in the report.

# Usage

To use this repo correctly, follow these instructions:

1) Duplicate database.ini.tmpl and rename it to remove the .tmpl from the end. Then edit the .ini file to connect to your desired PostgreSQL server.

2) Add the .json file including the data you wish to add to your database. The one used in this research can be found at: https://data.dws.informatik.uni-mannheim.de/largescaleproductcorpus/data/v2/offers_corpus_english_v2.json.gz and for simplicity, it will be assumed that you use the same.

3) Run the first block of wdctest3.ipynb and then edit the __main__ function of the second block so that the convert_json() function points to the correct .json file and gives the desired name for your new table.

4) Run the second block of wdctest3.ipynb and wait. If you use the given .json file, this will take 5-6 hours on average.

5) Create a base table filled with the requisite number of ID-clusters of a specific size, and a probabilistic table which should be empty. Also make sure that a _dict table exists as well, though that should be auto-created normally during installation of the DuBio extension. Exactly how to create these tables should be explained in the report, and if you don't have that, figure it out yourself from the code. Good luck.

6) Run the first four blocks of duBio_building.ipynb. Then, edit the __main__ function in the final block to connect to the database and the correct base and probabilistic tables, alongside a name for your dictionary. The dictionary does not need to exist in the _dict table prior to running. CompleteTable2() is for tables with cluster size of 2, CompleteTable3() is for tables of cluster size 3, and CompleteTable4() is for tables of cluster size 4.

7) Good luck, and for those of you who wish to edit and improve this code: Godspeed and I'm sorry.
