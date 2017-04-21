# Graph-Theory-Project-2017
## Neo4J Project 3rd Year Graph Theory GMIT timetable

> Student Name: Donal McGahon

> Student Number: G00299627

> Lecturer: Ian McLoughlin

## Table of Contents:

1. Introduction
1. What is Neo4j
1. Creating the Database Using CSV File
1. Nodes
1. Relationships
1. Labels
1. Properties
1. Design
1. Conclusion


## Introduction
For my Third Year Graph Theory Project I have been asked to design and prototype a Neo4j database for use
in a timetabling system for a third level institute. The minimum standard for this project is a document detailing the design of the database and a prototype Neo4j database following that design and using data from GMIT. I based my project on the timetabling system of my course year, which is Software Development Year 3.

The timetable system that I am to devise is to contain nodes, relationships, labels, relationship types and properties in Neo4j. When coming up with the idea for my project I made sure to keep this in mind and use them wisely in my database.

## What is Neo4j
Neo4j is an open source graph database managaement system developed by Neo Technology Inc. It is designed for storage and optimizing fast management. It is highly scalable, delivers constant real-time performance, which enables enterprises to build applications to meet today’s evolving data challenges.

It provides a server and Domain Specific Language (DSL) called Cypher that you use to create, update, query, explore and discover new data and relationships. Cypher is something like SQL, but designed to manage graph data.

### Three Main elements of Neo4j:
1. Nodes - It is like table of Relational Database where you can store the data. e.g. Person, Place.

1. Relationships - Is a connection between Data which can be mapped between two nodes e.g. He "Knows" her.

1. Properties - These are basically tags that can be attached to both Nodes and Relationships e.g. Node Person can have properties like Name, Age, Height.

## Creating Database using CSV file
At the beginning of my project I was unsure as to how I was going to get the information I was going to use for my database. I read up on Neo4j on websites such as [Neo4j](https://neo4j.com/) and found a page on their webside about using CSV files [Neo4j CSV](https://neo4j.com/developer/guide-import-csv/). You are able to upload files containing a large amount of data such as a CSV file to Neo4j. The information I needed for my project was on the [GMIT Timetable page](http://timetable.gmit.ie/sws1617/(S(2dls2h552rxryjzjgw1znh55))/default.aspx). I got the information for my timetable on this website and I copied it into an excel file. I then saved that file as a CSV (Comma delimited) file, which caused the file to be put into row that are separated by commas. Some of the rows inside of the timetable I did not need for my project for example row Type. When finishing editing the file it looked like this:

![image](https://cloud.githubusercontent.com/assets/14197773/25277602/4cf4ce1c-2697-11e7-858b-daf82c6c4191.png)

To upload this CSV file to Neo4j I used the following commands in the Neo4j command line:

`LOAD CSV WITH headers from "file:///Timetable.csv" as timetable create (a:SubjectGroup {SubjectGroup: timetable.SubjectGroup })`

This line of code uploaded using headers, the SoftwareGroup section to Neo4j as a node. All of the subject groups under this heading were now nodes on neo4j. To get the rest of the file uploaded I used the same piece of code except I changed them appropriately:

`LOAD CSV WITH headers from "file:///Timetable.csv" as timetable create (a:Staff {Staff: timetable.Staff })`

`LOAD CSV WITH headers from "file:///Timetable.csv" as timetable create (a:Begin {Begin: timetable.Begin })`

`LOAD CSV WITH headers from "file:///Timetable.csv" as timetable create (a:Rooms {Rooms: timetable.Rooms })`

I learned how to do this from reseaching and using the following link as a guide - [Importing CSV to Neo4j]( https://neo4j.com/docs/developer-manual/current/get-started/cypher/importing-csv-files-with-cypher/)
