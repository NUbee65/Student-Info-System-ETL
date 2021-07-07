**Student Info System ETL**

Migrated a student information system (GWSIS) from MySQL on AWS to Salesforce,
maintaining referential integrity using data modeling, data integration, and
even configuration of Salesforce

**Live Web Site Link**

The repository does not contain the live website. That website can be reached at
<https://cooperassetmanagement-dev-ed.lightning.force.com/lightning/page/home>.

**MySQL Workbench ERD Diagram Used to Reverse Engineer MySQL on AWS GWSIS
Database**

![](media/c1aeaa4db54ae5aa24c4113f232fea51.png)

**  
**

**Salesforce Schema Builder Diagram Used to Generate, Map and Recreate GWSIS
Database Using Salesforce Objects (Tables)**

![](media/0f127859621ec7491000fc558c76eaec.png)

**  
**

**Python Scripts Used to Effect the ETL – This Particular Section Relating to
Staff & Staff Assignment Tables and the Joint Lookup Tables**

We effectively started with an SQL database in MySQL and replicated it as an SQL
database in Salesforce. This required coding a series of logical scripts using
both Python and SQL.

From the source GWSIS database, we gathered the following data:

-   Relationships between the tables

-   Fields that are unique for each record with a given table (primary keys)

-   Fields that are common between the tables (foreign keys)

-   One-to-one, one-to-many, and many-to-many relationships

-   Tables that serve as lookup tables

This information informs how we reconstruct in Salesforce (or, for that matter,
any other SQL database):

-   One cannot simply copy individual table data over and expect the new target
    tables (1) to act coherently as a useful database and (2) to maintain
    referential integrity of the dataset

-   Rather, one must start replicate all the relationships and rules that govern
    the source database tables and dataset structures in setting up empty tables
    and dataset structures in the target database.

-   In order to assure that the linkages persist across database replication,
    one must execute (1) one or more database joins first between tables in the
    source database and (2) database joins between tables in the source and
    target databases. This ensures that unique identifiers and data structures
    are preserved across the records that are established in the new database.

-   For clarity’s sake, what I mean is that unique record IDs are automatically
    created fresh in Salesforce (target database) that are wholly different from
    the unique record IDs that were automatically created in MySQL (the source
    database). So, we are therefore forced to create a logic that preserves the
    dataset structure with certainty. And that is the basis for the multiple
    table joins detailed above.

-   All of the above dictates the order of creating tables and defining their
    structures and in replicating records from source to target database.

**![](media/e3115374b834f3691383270655dcab7f.png)**

**  
**

**![](media/7ed354541fc063b4a128442379bacb9a.png)**

**  
**

**![](media/f805d11b5ec3a780d42684738071bf9a.png)**

**  
**

**![](media/bdde552cfc07e385d6fe41f4bff4f74a.png)**

**  
**

**![](media/881f22fc94e20510f73ff9d00fe65789.png)**

**  
**

**![](media/2fcd0f3cefc60738615710cb1d3a2d6b.png)**

**  
**

**![](media/7bacf18c939e83b4a9b0641b877ac20c.png)**

**  
**

**![](media/75b356658dc3532aaaf0282bbcf39332.png)**

**  
**

**Final Solution Example Table – Class Participants Table in Salesforce GWSIS
Database Post ETL**

![](media/60dbf904f7008ba28cdb3f28253126e1.png)
