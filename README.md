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
