# Graph-Theory-Project-2017
## Neo4J Project 3rd Year Graph Theory GMIT timetable

> Student Name: Donal McGahon

> Student Number: G00299627

> Lecturer: Ian McLoughlin

## Table of Contents:

1. Introduction
1. What is Neo4j
1. What is Cypher
1. Creating the Database Using CSV File
1. Nodes
1. Relationships
1. Design
1. Conclusion


## Introduction
For my Third Year Graph Theory Project I have been asked to design and prototype a Neo4j database for use
in a timetabling system for a third level institute. The minimum standard for this project is a document detailing the design of the database and a prototype Neo4j database following that design and using data from GMIT. I based my project on the timetabling system of my course year, which is Software Development Year 3 semester 2.

The timetable system that I am to devise is to contain nodes, relationships, labels, relationship types and properties in Neo4j. When coming up with the idea for my project I made sure to keep this in mind and use them wisely in my database.

## What is Neo4j
Neo4j is an open source graph database managaement system developed by Neo Technology Inc. It is designed for storage and optimizing fast management. It is highly scalable, delivers constant real-time performance, which enables enterprises to build applications to meet today’s evolving data challenges.

It provides a server and Domain Specific Language (DSL) called Cypher that you use to create, update, query, explore and discover new data and relationships. Cypher is something like SQL, but designed to manage graph data.

### Three Main elements of Neo4j:
1. Nodes - It is like table of Relational Database where you can store the data. e.g. Person, Place.

1. Relationships - Is a connection between Data which can be mapped between two nodes e.g. He "Knows" her.

1. Properties - These are basically tags that can be attached to both Nodes and Relationships e.g. Node Person can have properties like Name, Age, Height.

## What is Cypher
Cypher is a declarative graph query language that allows for expressive and efficient querying and updating of the graph store. Cypher is a relatively simple but still very powerful language. Very complicated database queries can easily be expressed through Cypher

A simple example of a Cypher command is as follows:

`MATCH (n) RETURN n`

What this does is looks for all the nodes inside the database and returns them. You will then be able to visually see all the nodes in the database.

A more complex Cypher query could be as follows:

`MATCH (sean {name: 'Sean'})-[:friend]->()-[:friend]->(fof)
RETURN sean.name, fof.name`

What this Cypher query does is it finds a user called 'Sean' and 'Sean’s' friends, returning both 'John' and any friends-of-friends that are found in the database.

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


## Nodes
When I uploaded the CSV file as shown above, this created the nodes for me. The nodes that I used are as followes:
* SubjectGroup - The subject and the group associated with that subject e.g Group A
* Begin - The day and time
* Rooms - The room number
* Staff - Name of Lecturer

## Relationships
The relationships I used in this project are as follows:
* Attends
* Lecturing
* Room_For

To create these relationships I used the following command:

`LOAD CSV WITH headers from "file:///Timetable.csv" as timetable match (a:SubjectGroup {SubjectGroup: timetable.SubjectGroup}), (b:Begin {Begin: timetable.Begin}) CREATE (a) - [r:Attends]-> (b)`

This created a relationship between SubjectGroup and Begin. SubjectGroup Attends Begin.

`LOAD CSV WITH headers from "file:///Timetable.csv" as timetable match (a:Staff {Staff: timetable.Staff}), (b:Begin {Begin: timetable.Begin}) CREATE (a) - [r:Lecturing]-> (b)`

This created a relationship between Staff and Begin. Staff Lecturing at Begin.

`LOAD CSV WITH headers from "file:///Timetable.csv" as timetable match (a:Rooms {Rooms: timetable.Rooms}), (b:Begin {Begin: timetable.Begin}) CREATE (a) - [r:Room_For]-> (b)`

This created a relationship between Rooms and Begin. Rooms has Rooms_For Begin.

## Design
* Below is the design I used for my Neo4j Timetable. I based everything around the time.
* So at a certain time slot e.g Monday 12:00, I have a Node Room e.g PF05, with the realtionship Room_for with Begin. This would mean PF05 will be available for the time slot Monday 12:00.
* For that same time slot I have a lecturer e.g Ian McLoughlin, with the relationship lecturing with Begin. This would mean this lecturer is to be at PF05 at 12:00.
* Also for that same time slot I have a Node SubjectGroup for example KSOFG73 GRAPH THEORY Gr A/P, with the relationship Attends with Begin. This means KSOFG73 GRAPH THEORY Gr A/P are to attend PF05 with the lecturer Ian McLoughlin at 12:00.

![image](https://cloud.githubusercontent.com/assets/14197773/25279749/6481db80-269f-11e7-96d4-e41ad3ba8bf4.png)


## Conclusion
Throughout the process of working with Neo4j and creating the Timetable database I learned a lot. I learned how to use Neo4j efficiently and learned many useful Cypher queries that I will be able to use again. Uploading a CSV file to Neo4j was a learning curve for me as I learnt how comma delimited files are used and how to use them to your advantage while working with Neo4j. I enjoyed using Neo4j as being able to see your database visually in front of you in a graph style made working on it easier. I feel I learned how to plan projects better after working with Neo4j because for each step in making the Neo4j database I was always thinking of my next step. I feel graph databases like Neo4j will become increasingly popular in the coming years because they are enjoyable to use and are visually easy to understand.
