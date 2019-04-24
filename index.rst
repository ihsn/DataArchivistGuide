.. image:: media/image1.png

**International Household Survey Network**

**IHSN**

Quick Reference Guide for Data Archivists
=========================================

**DRAFT - Version 2019 -04**

Content
=======

`Introduction 1 <#introduction>`__

`1. Gathering and preparing the data set
2 <#gathering-and-preparing-the-data-set>`__

`2. Gathering and preparing the documentation
5 <#gathering-and-preparing-the-documentation>`__

`3. Importing data and establishing relationships
5 <#importing-data-and-establishing-relationships>`__

`4. Importing external resources 8 <#importing-external-resources>`__

`5. Completing metadata 9 <#completing-metadata>`__

`5.1. Good practices for completing the Document Description
10 <#good-practices-for-completing-the-document-description>`__

`5.2. Good practices for completing the Study Description
11 <#good-practices-for-completing-the-study-description>`__

`5.3. Good practices for completing the File Description
23 <#good-practices-for-completing-the-file-description>`__

`5.4. Good practices for completing the Variables Description
24 <#good-practices-for-completing-the-variables-description>`__

`5.5. Good practices for completing the External Resources description
28 <#good-practices-for-completing-the-external-resources-description>`__

`6. Creating variable groups 29 <#creating-variable-groups>`__

`7. Running validations and diagnostics
30 <#running-validations-and-diagnostics>`__

`8. Generating the survey documentation in PDF
31 <#generating-the-survey-documentation-in-pdf>`__

`9. Producing the final output 31 <#producing-the-final-output>`__

`10. Independent quality review 32 <#independent-quality-review>`__

Introduction
-------------

This *Quick Reference Guide for Data Archivists* provides data
archivists with guidelines to document a micro-dataset in compliance
with the Data Documentation Initiative (DDI) and the Dublin Core (DCMI)
metadata standards, using the World Bank Metadata Editor.

The World Bank Metadata Editor is an application designed to help document
data collection operations undertaken for different kinds of research
projects. The application is developed as an open-source tool by the World
Bank. A number of Metadata standards recognized as global models for
defining and describing different types of data have been integrated into
the Metadata Editor, these are: The Data Documentation Initiative
(DDI Codebook), The Dublin Core Metadata Initiative (DCMI) and the ISO
19139 for geospatial data.

The Metadata Editor is modelled on the Nesstar Publisher. As such it should
provide a familiar environment for the Nesstar users. As an added benefit,
the Metadata Editor is flexible and can support the documentation of
multiple-data types. Out of the box it supports the documentation of survey
data, time Series data, geospatial data, statistical tables, images,
analytical scripts and standalone publications or documents.

This Guide summarizes the process in 10 chronological steps:

1.  Gathering and preparing the data set

2.  Gathering and preparing the documentation

3.  Importing data and establishing relationships

4.  Importing external resources

5.  Adding metadata

6.  Creating variable groups (optional)

7.  Running diagnostics

8.  Generating the standard survey documentation using the PDF generator

9.  Quality assessment

10. Producing the output for publication

Also provided (in appendix) is the *IHSN DDI Reviewers’ Feedback Form*
which provides a standard tool for the assessment of survey metadata by
an external reviewer.

This Guide is not a Metadata Editor reference or training manual. It is
assumed that users are already familiar with the Editor. A *Metadata*
*Editor User’s Guide* is available at 
https://metadata-editor.readthedocs.io/en/latest/.

Before you start: organizing your files
---------------------------------------

Documentation of a dataset will be most efficient if you
organize your data and other files properly. We recommend that, before
anything else, you create the necessary directories as follows:

+------------+--------------+------------------------------------------+
|.. image:: media/Page2.png |- Create a directory for the survey.      |
|                           |  We suggest you name it using the        |
|                           |                                          |
|                           |  country, survey’s year and the          |
|                           |  abbreviated name, e.g. “UGA_2018_HIES”  |
|                           |                                          |
|                           |  for “Household Income and Expenditure   | 
|                           |  Survey” of Uganda collected in 2018.    |
+                           +------------------------------------------+
|                           |- Create various sub-directories for the. |
|                           |  data files (and for the various versions|
|                           |  of the dataset if relevant)             |
|                           +------------------------------------------+
|                           |- Create sub-directories for the          |
|                           |  documentation and for the program files |
|                           |  if relevant (see example).              |
+------------+--------------+------------------------------------------+

1. Gathering and preparing the data set
=======================================

Gathering and preparing data is a process that requires great care. 
Prior to documenting a dataset, it is important to ensure that you are
working with the most appropriate version of all the concerned data
files. If the dataset is meant for public release, one should work with
the final, edited, anonymous version of the dataset. If the dataset is
being documented for archiving and internal use only, one may include
the raw data as well as the final, fully edited files. The Metadata
Editor provides you with the possibility of documenting the specificity
of each version of the dataset.

Much of the quality of the output generated by the Editor will depend
upon the prior preparatory work. Although the Editor can make some
changes to the data, it is highly recommended that the necessary checks
and changes be made in advance using a statistical package and a script.
This ensures accurate and replicable results. 

This section describes the various checks and balances involved in the
data preparation process, such as: making a diagnostic on the structure
of your data, cleaning it and identifying the various variables at the
outset. Listed below are some common data problems that users encounter:

-  Absence of variables that uniquely identify each record of the dataset
-  Duplicate observations
-  Errors from merging multiple datasets
-  Encountering incomplete data when comparing the content of the data
   files with the original survey questionnaire
-  Unlabelled data
-  Variables with missing values
-  Unnecessary or temporary variables in the data files
-  Data with sensitive information or direct identifiers

Some practical examples using a statistical package are provided in
*Section A “Data Validations in Stata: Practical Examples*.

+--------------------------------------------------------------------+
| *Note*                                                             |
|                                                                    |
| If you are working in a data archive, be careful not to overwrite  |
| your original variables. Since managing databases involves several |
| data-checking procedures, archive a new version in addition to the |
| original. Work on this new version, leaving the original data files|
| untouched.                                                         |
+--------------------------------------------------------------------+

The following procedures are recommended for preparing your dataset(s):

1.2. Data files should be organized in a hierarchical format
------------------------------------------------------------

Look at your data and visualize it to understand its structure.
It is preferable to organize your files in a hierarchical format
instead of a flat format. In a hierarchical format, columns
contain specific information about all possible units of analysis
and rows form the individual observations (households,
establishments, products, communities/countries, or any
combination of those). Hierarchical files are easier to analyse,
as they contain fewer columns that store the same information and
are more compact. A flat format contains multiple columns with
information on only one specific unit of analysis, so the
information becomes redundant. For example, the information
provided in one column is about the household head, and the row
provides information on the child in the household.

**Table 1. Flat Format**

.. image:: media/Page4_1.png

**Table 2. Hierarchical Format**

.. image:: media/Page4_2.png

*Tables 1 and 2* illustrate the two data structures. They
contain the same information about six people on age and their
relationship with the head of the household. The flat dataset
(Table 1) stores the information on each family member in a new
column. Note that for every additional member or characteristic,
the dataset gets flatter and wider. The hierarchical dataset
(see Table 2) has one observation and one row per person.
Each variable contains a value that measures the same attribute
across people and each record contains all values measured on the
same person across variables. For every additional member
characteristic, the dataset maintains the same number of columns,
gains additional rows and gets longer and less flat compared to
*Table 1*. The first two columns of this dataset have a
hierarchical structure, where the ID member column is nested
inside the ID household column. 

Hierarchical files are easier to manage. Suppose in this example
that there were many characteristics measured for everyone, the
hierarchical structure would be a more convenient format because
for each new characteristic, the dataset creates only one
additional column, whereas, in the flat structure, it would
create as many columns as there are people in the data with such
characteristics.

1.2. Datasets with multiple units of analysis should be stored in different data files 
--------------------------------------------------------------------------------------
It is recommended that you store your data in different files
when you have multiple observational units. For example, *Table 3*
shows a dataset that has both household-level data (columns on
the type of dwelling and walls material) and individual-level
data (columns on the marital status, work status, and worker
category). Note that storing both levels of information in one
dataset will result in a repetition of household characteristics
for each household member. In Table 3, the information about the
columns ‘type of dwelling’ and ‘wall material’ is repeated for
everyone. Sometimes, this duplication is inefficient, and it is
easier to have the dataset broken down by observational unit, into
multiple files. In this example, it would be simpler to create two
files:  one for the household characteristics and another for the
individual characteristics. The two files can be connected through
a unique identifier, which in this case will be the household ID and
member ID. We discuss the need for this unique identifier further on
in this text as well. 

**Table 3. Single data set with more than one observational unit**

.. image:: media/Page5.png

1.3. Columns in a dataset should represent variables, not values
----------------------------------------------------------------

It is recommended that columns represent variables (e.g., sex, age,
marital status) and rows represent observations (e.g., individuals,
households, firms, products and so forth). In some datasets, columns
instead of describing variables or attributes, describe values, which
means that one variable is broken into segments and each one is
stored in different columns. While this dataset structure can be
useful for some analysis, the standard data structure where columns
are variables and not values is the norm. 

For example, *Table 4* (options 1 and 2) gives information at the
individual-level on marital status, relationship with the head of
the household and age. The difference between both tables is how the
variable ‘age’ is reported. Option 1 had broken the variable ‘age’
into segments. This practice makes your data: i) messier, it has
values of the variable as headings, and ii) inefficient, it increases
the size of the dataset. Option 2 is recommended since there is only
one heading and store of the information occupies less space, allowing
the user to identify the structure of the data in a clear manner.

**Table 4. Data Structures: Hypothetical datasets**

.. image:: media/Page6_1.png

1.4. Each observation in every file must have a unique identifier
-----------------------------------------------------------------

Before you check for uniqueness of the identifiers in your files, you
need to figure out the unit of analysis. Even if you are not the data
producer, it is often easy to identify it. You can always review the
documentation to see if the information has been provided. Below, some
examples of units of analysis:

**Table 5. Unit of Analysis by Study type**

.. image:: media/Page6_2.png

Once you recognize the unit of analysis, the next step is to identify
the column that uniquely identifies each record. If a dataset contains
multiple related files, each record in every file must have a unique
identifier. The data producer can also choose multiple variables to
define a unique identifier. In that case, more than one column in a
dataset is used to guarantee uniqueness. These identifiers are also
called **key variables** or **ID variables**. The variable(s) should
not contain missing values or have any duplicates. They are used by
statistical packages such as SPSS, R or Stata when data files need
to be merged for analysis

The absence of a unique identifier is a data quality issue, so one
needs to ensure that the unique IDs remain fixed/present during the
data cleaning process. If this correction is not possible, the archivist
should note the anomalies in the documentation process.

+--------------------------------------------------------------------+
|*Best Practices*                                                    |
|                                                                    |
|- It is recommended that ID variables be defined as a numeric since |
|  sorting and filtering records is much more efficient when         |
|  variables are numeric.                                            |
|- ID variables should not contain spaces, special characters or     |
|  accents, since they may suffer modifications when the dataset is  |
|  converted in different formats.                                   |
|- For the convenience of users of the data, avoid identifiers       |
|  consisting of too many variables. For example, in a household     |
|  survey, the household identifier should ideally be a single       | 
|  variable (which you may create by concatenating a group of        |
|  variables [3]_), and the individual identifier should be the      |
|  combination of only two variables (the household ID, and the      | 
|  sequential number of each member).                                |
|- It is recommended that you generate an ID based on a sequential   |
|  number, however, keep in mind that it should not be too long      |
|  because statistical packages and spreadsheet programs store a     |
|  number of digits of precision, so opening a data set that contains|
|  ID variables with many characters, might result in truncated      |
|  fields. For instance, the limit of the number of characters in    |
|  Microsoft Excel is 15, so it changes any digits past the fifteenth|
|  place to zeroes.                                                  |
|- If you prepare your data files for public dissemination, it may be|
|  preferable to generate a unique household identification that     |
|  would **not** be a compilation of geographic codes (because       |
|  geographic codes are highly identifying). This recommendation is  |
|  to ensure anonymity and will be explained in further detail later |
|  on in this text. The following example shows how to construct a   |
|  unique identifier without using detailed information provided by  |
|  the geographic codes.                                             |
+--------------------------------------------------------------------+

Example
  -  Suppose the unique identification of a household is a combination of
     of variables PROV (Province), DIST (District), EA (Enumeration Area),
     HHNUM (Household Number). Options 2 and 3 are recommended. Note that
     if option 3 is chosen, it is crucial o preserve (but not distribute)
     a file that would provide the mapping between the original codes and
     the new HHID.

=====  =====  =====  ========== ==================== =====================
 Option 1: Use a combination of Option 2: Generate a  Option 3: Generate a
              four variables       concatenated ID       sequential number
------------------------------- -------------------- ---------------------
PROV   DIST    EA    HHNUM      HHID                 HHID
=====  =====  =====  ========== ==================== =====================
12     01     014    004        1201014004           1
12     01     015    001        1201015001           2
13     07     008    112        1307008112           3
Etc    Etc    Etc    Etc        Etc                  Etc
=====  =====  =====  ========== ==================== =====================

Once you recognize the unit of analysis and the variable that uniquely 
identifies it, the following checks are suggested:

-  Even if the data set has a variable with a label "unique identifier",
   it is important to confirm that this variable truly does uniquely
   identify each record. To confirm or even to find out what the unique
   identifier is, you can make use of the *-duplicate-* function in SPSS or
   the *-isid-* command in Stata (for R, do as shown in *Table 6*). For more
   details, refer to *Example 1 and Example 2 of Section A*.

**Table 6. Check for unique identifiers: STATA/R/SPSS Commands**

+---------------------+---------------------------+----------------------+
|   **STATA Code**    |         **R Code**        |  **SPSS Function**   |
+---------------------+---------------------------+----------------------+
|*use “household.dta”*|*my_data<-*                |*GET*                 |
|                     |*read_dta("household.dta")*|*FILE='household.sav'*|
|*isid "key1" "key2"* |                           |                      |
|                     |                           |*execute.*            |
|                     |*id <-c( "key1" , " key2")*|                      |
|                     |                           |From the menu choose: |
|                     |*isid(my_data, id,*        |                      |
|                     |*verbose = FALSE)*         |- Data>Indentify      |
|                     |                           |  Duplicate Cases     |
|                     |                           |- Select Key Variables|
+---------------------+---------------------------+----------------------+

-  Finally, check that the ID variable for the unit of observation doesn't
   have missing or assigned zero/null values. Ensure that the datasets are
   sorted and arranged by their unique identifiers.
   
*Table 7* below gives a hypothetical example. In this dataset, the
highlighted columns (hh1, hh2, hh3) are the key variables, which means that
they are supposed to make up the unique identifier. However, looking at
those variables, we can identify some problems: the key variables do not
uniquely identify each observation as they have the same values in rows 4
and 5, they also have some missing values (represented by asterisks), 
assigned zero values and some null values (those that say NA, don’t know).
All these issues suggest that those variables are not the key variables,
and one needs to go back and double-check the data documentation.
Alternatively, the archivist could check with the data producer and ask
them how to fix these variables, in case those are indeed the key variables.

**Table 7. Check for unique identifiers: Hypothetical data set**

.. image:: media/Page8_2.png

*Example 3* provides further details and describes the steps involved in
performing a validation when the identifier is made of multiple variables
(see *Section A*).

1.5. Identifying duplicate observations
---------------------------------------

One way to rule out problems with the unique identifier is to check if
there are duplicate observations (records with identical values for all
variables, not just the unique identifiers). Duplicate observations can
generate erroneous analysis and cause data management problems. Some
possible reasons for duplicate data are, for example, the same record
being entered twice during data collection. They could also arise from
an incorrect reading of the questionnaires during the scanning process
if paper-based methods are being used. 

Identifying duplicate observations is a crucial step. Correcting this
issue may involve eliminating the duplicates from the dataset or giving
them some other appropriate treatment.

Statistical packages have several commands that help identify duplicates.
*Table 8* shows examples of these commands in STATA, R and SPSS. The STATA
command *-duplicates report-* generates a table that summarizes the number
of copies for each record (across all variables). The command
*-duplicates tag-* allows us to distinguish between duplicates and unique
observations. For more details, refer to *Example 4* of *Section A*.

**Table 8. Check for duplicates observations: STATA/R/SPSS Commands**

+---------------------+---------------------------+----------------------+
|   **STATA Code**    |         **R Code**        |  **SPSS Function**   |
+---------------------+---------------------------+----------------------+
|*use “household.dta”*|*my_data<-*                |*GET*                 |
|                     |*load("household.rda")*    |*FILE='household.sav'*|
|*duplicates report*  |                           |                      |
|                     |*household*                |*execute.*            |
|*duplicates tag,*    |*[duplicated(household),]* |                      |
|*generate(newvar)*   |                           |From the menu choose: |
|                     |                           |                      |
|                     |                           |- Data>Indentify      |
|                     |                           |  Duplicate Cases     |
+---------------------+---------------------------+----------------------+

1.6. Ensure that each individual dataset can be combined into a single database 
-------------------------------------------------------------------------------

For organizational purposes, surveys are often stored in different datasets.
Therefore, checking the relationship between the data files is an essential
step to keep in mind throughout the data validation process. The role of
the data producer is to store the information as efficiently as possible,
which implies storing data in different files. The role of the data user is
to analyse the data as holistically as possible, which could sometimes mean
that they might have to join all the different data files into a single
file to facilitate analysis. It is essential to ensure that each of the
separate files can be combined (merged or appended depending on the case)
into a single file, should the data user want to undertake this step. 

Use statistical software to validate that all files can be combined into
one. For a household survey, for example, verify that all records in the
individual-level files have a corresponding household in the household-level
master file. Also, verify that all households have at least on
e corresponding record in the household-roster file that lists all
individuals. Below, some considerations to keep in mind before merging data
files:

- The variable name of the identifier should be the same across all datasets.
- The ID variables need to be the same type (either both numeric or both 
  string) across all databases.
- Except for ID variables, it is highly recommended that the databases don't
  share the same variable names or labels.

Example
 - A household survey is disseminated in two datasets; one contains
   information about household characteristics and the other contains
   information on the children (administered only to mothers or caretakers).
   To build a dataset containing all the information about the household
   characteristics, including where the children live, one needs to combine
   these files. Users are thus assured that all observations in the
   child-level file have corresponding household information.
  
 **Joining data files: Hypothetical data set** 
  
.. image:: media/Page10_1.png
  
.. image:: media/Page10_2.png
  
Statistical packages have some commands that allows us to combine datasets
using one or multiple unique identifiers. *Table 9* shows examples of 
these commands/functions in STATA, R and SPSS. For more details, refer to
*Example 5* of *Section A*. 

**Table 9. Joining data files: STATA/R/SPSS Commands**

+---------------------+---------------------------+----------------------+
|   **STATA Code**    |         **R Code**        |  **SPSS Function**   |
+---------------------+---------------------------+----------------------+
|*use “household.dta”*|*household<-*              |*GET*                 |
|                     |*load("household.rda")*    |*FILE='household.sav'*|
|*merge 1:m hh1 hh2*  |                           |                      |
|*hh3 using*          |*individuals<-*            |                      |
|*"individuals.dta"*  |*load("individuals.rda")*  |*execute.*            |
|                     |                           |                      |
|                     |*md<-merge(household,*     |From the menu choose: |
|                     |*individuals, by=c("hh1",  |                      |
|                     |"hh2", “hh3”),all=TRUE)*   |- Data>Merge Files>   |
|                     |                           |  Add Variables       |
|                     |                           |                      |
|                     |                           |- Select the data file|
|                     |                           |  to merge            |
|                     |                           |                      |
|                     |                           |- Select Key Variables|
+---------------------+---------------------------+----------------------+

Panel datasets should be stored in different files as well. Having one
file per data collection period is a good practice. To combine the different
periods of a panel dataset, the data user could merge them (Adding variables
to the existing observations for the same period) or append them (Adding
observations for a different period to the existing variables). To make sure
that panels can be properly appended, the following checks are suggested: 

- Check for the column(s) that identifies the period of the data (Year, Wave,
  Serie, etc.).
- The variable names and variable types should be the same across all datasets.
- Ensure that the variables use the same label and the same coding across all
  datasets.
  
 In SPSS, use the function *“Append new records”* and in STATA the command
 *-append-* to combine datasets vertically.

1.7. Check for variables with missing values 
--------------------------------------------

Getting data ready for documentation also involves checking for variables
that do not provide complete information because they are full of missing
values. This step is important because missing values can have unexpected
effects on the data analysis process. Typically, missing values are defined
as a character (.a, .b, single period or asterisks), special numeric
(-1, -2) or blanks. Variables entirely comprised of missing values should
ideally not be included in the dataset. However, before excluding them, it
is useful to check whether the missing values are expected according to the
questionnaire, and the skip patterns.

For example, a hypothetical household survey at the individual-level
(Table 10) provides information about the respondent’s employment status.
The survey identifies if the respondent is employed in Column D, and then
provides information about the worker category in Column E, but only for
those who reported being employed in Column D. This means that those who
answered ‘unemployed’ in column D should have a valid missing value in
column E. In other words, this is a pattern in the missing values that
should be observed and duly noted. 

On the other hand, Columns F and G are used to determine if the people who
are not employed are looking for a job and are actively seeking it. These
questions are not asked to the employed people (those who answered “yes”
in Column D), which mean that again, the missing values in those columns
correspond with what is expected. However, Column H contains information
for all employed individuals, so missing values in this column suggest
that there is a problem in the data and should be addressed. Therefore,
one should not blindly delete missing values at the outset without checking
for these patterns. 

**Table 10. Checking for Missing Values: Hypothetical data set**

.. image:: media/Page12.png

In SPSS, use the function *“Missing Value Analysis”* and in R, do as shown
in *Table 11*. You can also use the STATA command *-misstable summarize-*
that produces a report that counts all the missing values. You can also use
the *-rowmiss()-* command with *-egen-* to generate the number of missing 
values among the specified variables. For more details, refer to
*Example 6* of *Section A*.

**Table 11. Counting Missing Values: STATA/R/SPSS Commands**

+----------------------+---------------------------+---------------------+
|   **STATA Code**     |         **R Code**        |  **SPSS Function**  |
+----------------------+---------------------------+---------------------+
|*use "individual.dta”*|*individual<-*             |*GET*                |
|                      |*load("individual.rda")*   |*FILE=*              |
|*misstable summarize* |                           |*'individual.sav'*   |
|                      |*colSums*                  |                     |
|                      |*(is.na(individual))*      |*execute.*           |
|                      |                           |                     |
|                      |*colMeans*                 |From the menu choose:|
|                      |*(is.na(individual))*      |                     |
|                      |                           |- Data>Analyze>      |
|                      |                           |  Missing Value      |
|                      |                           |  Analysis           |
|                      |                           |                     |
|                      |                           |- Select “Use All    |
|                      |                           |  Variables”         |
+----------------------+---------------------------+---------------------+

+--------------------------------------------------------------------+
|*Best Practices*                                                    |
|                                                                    |
|Since there are different reasons for missing values, data producer |
|should code them with negative integers or letters to distinguish   |
|the missing values and valid data. For instance, (− 1) might be the |
|code for “Don’t Know”, (-2) the code for “Refused to Answer” and    |
|(-9) code for “Not Applicable”.                                     |
+--------------------------------------------------------------------+

1.8. Check Improper value ranges 
--------------------------------

It is helpful to generate descriptive statistics for all variables
(frequencies for discrete variables; min/max/mean for continuous
variables) and verify that these statistics look reasonable. Just as
there are variables that must take on only specific values, such as “F”
and “M” for gender, there are also some variables that can take on
several values (such as age or height). However, those values must fit
a particular range. For example, we don't expect negative values, or
typically see values over 115 years for age. 

Values for categorical variables should be guided by the questionnaire
(or separate documentation for constructed variables). If we have an
education variable that has 9 response options in the questionnaire,
the corresponding ‘education’ variable in the dataset should have 9
categories. We should not observe more than 9 unique values for this
variable. Similarly, for any questions in the survey for which the
options are only “yes”, “no” and “other”, we should not observe more
than these 3 unique values.  When out of range values exist, this might
signal data cleaning issues. 

*Table 12* shows examples of some commands/functions in STATA, R and
SPSS.

**Table 12. Generate descriptive statistics: STATA/R/SPSS Commands**

+----------------------+---------------------------+---------------------+
|   **STATA Code**     |         **R Code**        |  **SPSS Function**  |
+----------------------+---------------------------+---------------------+
|*use "individual.dta”*|*individual<-*             |*GET*                |
|                      |*load("individual.rda")*   |*FILE=*              |
|*summarize*           |                           |*'individual.sav'*   |
|                      |*summary(individual)*      |                     |
|                      |                           |*execute.*           |
|                      |                           |                     |
|                      |                           |From the menu choose:|
|                      |                           |                     |
|                      |                           |- Data>Analyze>      |
|                      |                           |  Descriptive        |
|                      |                           |  Statistics>        |
|                      |                           |  Frequencies        |
|                      |                           |                     |
|                      |                           |- Select “Statistics"|
+----------------------+---------------------------+---------------------+

1.9. Verify that the number of records in each file corresponds to what is expected 
-----------------------------------------------------------------------------------

The technical documentation helps to form some expectations about the size
of the dataset. Make sure that in all the files, the number of records is
the same as (or is similar to) what is explicitly stated in the sample
design of your survey.

Suppose that you have a household survey and according to the documentation
the sample size is 50,321 households. Consequently, the file that contains
the household-level information should have a similar number of observations.
When this is not the case, you should be able to account for this difference
in data documentation.

On the other hand, even if the number of individual records is not available
in the documentation, you can still perform a rough check on the files. For
example, if you have the household level file and the person level file, the
latter should be between 2 or 6 times larger than the former, depending on
the average household size in the country for which the information has been
collected. Another example is to compare the household level file of an
expenditure survey with the consumption level file (at the product-level).

The latter should have n times the number of observations than the former,
where n is the average number of products that each household records in the
survey.

1.10. Datasets must contain all variables from the questionnaire and be in a logic sequence 
-------------------------------------------------------------------------------------------

Verify the completeness of your data files by comparing the content of these
files with the survey questionnaire. All variables in the questionnaire should
appear in the dataset, except those excluded on purpose by the producer of the
data because of reasons of confidentiality (see numeral *1.15*). 
Cross-checking with the questionnaire(s) is needed to ensure that all sections
are included in the dataset. 

Additionally, it is a good practice to make sure that the database is sorted
in the same order as the questionnaire. This practice will help users navigate
seamlessly across the dataset using the questionnaire as a route map. 

The Stata command *-describe-* displays the names, variable labels and other
characteristics, which helps us verify that no variables have been omitted in
the database. It simultaneously confirms that all variables are correctly
ordered. Refer to *Example 7* of *Section A* for further details.

1.11. Include the relevant weighting coefficients and variables identifying the stratification levels 
-----------------------------------------------------------------------------------------------------

All data files of a sample survey should have clearly labelled variable(s)
with information on the survey weights. Sample surveys need to be
representative of a broader population for which the data is collected,
and the user needs the survey weights for almost every analysis performed.
In the case of household surveys, the survey weights are equal among
members of the same household but differ across households. Weights are
positive and strictly higher than zero. They should not have a larger
value than the population for which the survey is representative.

A more detailed description of how the survey weights would look like
should be provided in the documentation of the survey.  Based on it, you
can perform some basic range checks. Notice that Census datasets do not
need weights since a census collects data on all the individuals in the
population. There are however some exceptions, for example in the case of
IPUMS, the data collected are not full censuses but census samples, so
weights are required in this context. 

Additionally, for sample surveys, verify that the variables identifying
the various levels of stratification and the primary sampling unit are
included and easily identifiable in at least one of the data files. These
variables are needed for the calculation of sampling errors.

1.12. Variables and codes for categorical variables must be labelled 
--------------------------------------------------------------------

**Variable labels**

Labels should be short and precise. They should provide a clear
indication of what information is contained in the variables. Variable
labels are brief descriptions or attributes of each variable. Without
variable labels, users are not able to link the variables in the
database to the questions of the questionnaire. So, one should ensure
that all variables are labelled.
 
Additionally, even if variables are fully labelled, the following
practices must be considered: 

- Variable labels can be up to 80 characters long in Stata and 255 in
  SPSS, however, it is recommended that labels be informative,  short
  and accurate.
- It is a common practice to have a literal question from the survey as
  a variable label. However, the literal questions are usually longer
  than the maximum number of characters, so this is not an advisable
  practice. 
- The same label should not be used for two different variables. 

**Value labels**

Label values are used for categorical variables. To ensure the correct
encoding of data, it is important to check that the stored values in
those variables correspond to what is expected according to the
questionnaire. In the case of continuous variables, we also suggest the
checking of ranges. For instance, if the question is about the number of
working hours, the variable should not have negative values. 

You can compare variable labels in the dataset to those in the
questionnaire using the *–codebook-* Stata command or *–labelbook*-. 
Refer to *Example 8* of *Section A* for further details.

1.13.  Temporary, calculated or derived variables should not be disseminated 
----------------------------------------------------------------------------

Remove all unnecessary or temporary variables from the data files. These
variables are not collected in the field and present no interest for users.

The data producer could generate variables that are only needed during the
quality control process but are not relevant to the final data user. For
example, the variable “_merge” in Stata is generated automatically after
performing the check described in the Numeral *1.6*, when the data producer
wants to see if the datasets match properly. Variables that group categories
of a question, dummy variables that identify a question’s category are all
variables produced during the coding process that are not relevant once the 
analysis is completed. 

There are cases in which calculated variables may be useful to the users, so
they must be documented in the metadata. For example, most Labor Force Surveys
(LFS) contain derived dummy variables to identify the sections of the
population that are employed or unemployed. These variables are generated
using multiple questions from the dataset and are essential elements of any 
LFS. Most data users prefer to make use of them instead of computing them on
their own, to reduce the risk of error. This is a strong argument to make a
case for keeping these variables in the dataset, despite them being a
by-product of other original variables.

To be useful, those variables that remain in the dataset must be well
documented, else they, they may be useless to or misunderstood by users.

1.14. Check that the data types are correct
-------------------------------------------

Do not include string variables if they can be converted into numeric
variables. Look at your data and check the variables' types, particularly
for those that you expect to be numeric (age, years, number of
persons/employees/hours, income, purchases/expenditures, weights, and so
forth). If there are numeric variables stored as string variables, your
data needs cleaning.

For example, *Table 13* contains a data set at the individual-level with
some variables that should be numeric. The columns B (Age) and E
(Working Weeks) are stored as numeric variables, which is fine. However,
the variables ‘Number of working of hours per week’ (Column G), ‘Number
of persons working at the business’ (Column H) and ‘Monthly Income’
(Column I) are loaded as strings because there are non-numeric values
(don't know, skip, refused to answer) and some missing values present.
Those variables need to be cleaned and converted from string variables
to numeric variables.

**Table 13. Checking Data Types: Hypothetical data set**

.. image:: media/Page16.png

Statistical packages have some commands that allows us to make such
conversions. *Table 14* shows examples of these commands/functions in
STATA, R and SPSS.

**Table 14. Convert string variables to numeric: STATA/R/SPSS Commands**

+----------------------+---------------------------+---------------------+
|   **STATA Code**     |         **R Code**        |  **SPSS Function**  |
+----------------------+---------------------------+---------------------+
|*use "individual.dta”*|*individual<-*             |*GET*                |
|                      |*load("individual.rda")*   |*FILE=*              |
|*destring (varname),* |                           |*'individual.sav'*   |
|*{generate|replace}*  |*Individual $varname =*    |                     |
|                      |*as.numeric(Individual*    |*execute.*           |
|                      |*$varname)*                |                     |
|                      |                           |From the menu choose:|
|                      |                           |                     |
|                      |                           |- Data>Transform>    |
|                      |                           |  Recode into Same|  |
|                      |                           |  Different Variables|
|                      |                           |                     |
|                      |                           |- Select the variable|
|                      |                           |                     |
|                      |                           |- Select “Old and New|
|                      |                           |  Values” and Recode |
|                      |                           |  it                 |
|                      |                           |                     |
|                      |                           |- Select “Convert    |
|                      |                           |  numeric strings to |
|                      |                           |  numbers (‘5’->5)   |
+----------------------+---------------------------+---------------------+

1.15. Datasets must not have directed identifiers
-------------------------------------------------

One must verify that in all data files, sensitive information or direct
identifiers that could reveal the identity of the respondent directly
(names, addresses, GPS coordinates, phone numbers, etc.) have been removed.
Check to ensure this information is not in the dataset(s). If it is, those
variables need to be removed from shared datasets. 

Keep in mind that if you are preparing a dataset for public release, you
need a cleaned, anonymous dataset.  Removing all direct identifiers is the
first key step to ensuring the anonymity of the participants. However,
before you start any privacy procedures, you should always check your data.

For more information on how to apply statistical disclosure control (SDC)
methods to data before release, see the document "Introduction to
Statistical Disclosure Control (SDC)" available at
http://ihsn.org/sites/default/files/resources/ihsn-working-paper-007-Oct27.pdf 

1.16. Compress the variables to reduce the file size
----------------------------------------------------

Compress the variables consist of reducing the size of the data file without
loss of precision or modifying the information that it provides. Listed
below are some reasons why compressing a data set may be a useful practice
for at least three reasons: First, it makes faster the process of creating
backups, uploading and downloading data files from your data repository or
any Survey Catalog. Second, it reduces the time that data users will need
to spend working with the data. Additionally, it will make the data more
accessible to the different type of users; sometimes the data size will
impose restrictions on those users who lack high computational power.
Third, it will help to free up disk space in the server where you store
your data

Example
 - *Table 15* shows two versions of one dataset that provides 
   individual-levelinformation about the year of the first union, age, 
   school attendance,and health insurance. There is no difference in 
   the appearance of both datasets. However, version 1 was saving 
   uncompressed and version 2compressed. In the uncompressed version, 
   the variables “ID” and “Year” are stored as double, which means that
   they can store number with high decimal precision, but they
   are designed to only record information of integer numbers between
   -32,767 and 32,740. So, the compressed version changed the storage
   type of these variables to int and saves 6 bytes per observation.
   Similarly, other variables like “age” and “school attendance” are
   stored as a byte in the compressed version, which saves 7 bytes
   per observation when are compared to the uncompressed version.
   Let’s suppose that one has a data set with 500 variables like these,
   the total savings would be 3500 bytes per observation; if this data set
   has 50.000 observations, it means that the savings in memory space
   would be around 175 megabytes. 
   
 **Table 15. Compressing the Variables: Hypothetical data set**
   
.. image:: media/Page18_1.png

.. image:: media/Page18_2.png

Use the *compress* command in Stata, or the *compress* option when you
save a SPSS data file.

+--------------------------------------------------------------------+
| *Suggestion:*                                                      |
|                                                                    |
| If you are in the process of establishing a data archive and plan  |
| to document a collection of surveys, undertake a full inventory of |
| all existing data and metadata before you start the documentation. |
| Use the IHSN Inventory Guidelines and Forms to before you start the|
| documentation. Use the *IHSN Inventory Guidelines and Forms* to    |
| facilitate this inventory (available at www.surveynetwork.org).    |
+--------------------------------------------------------------------+

2. Gathering and preparing the documentation
============================================

All information related to the survey may be useful and should be
archived (even if not all will be disseminated to the public). This
includes not only technical documents such as the questionnaires or list
of codes (obviously needed by data users), but also administrative
reports (potentially useful for implementation of future surveys), and
other documents such as a compilation of the comments provided by
stakeholders at the time the questionnaire was designed, etc. Resources
to be included if available include:

-  The survey questionnaire(s); make sure that the cover page and all
   sections are included. If the questionnaire exists in multiple
   languages, provide all versions.

-  All technical, analytical and administrative documents

   -  Sampling information

   -  Interviewers and supervisor’s manuals

   -  List of codes

   -  Instructions for data editing

   -  Survey report (tabulation and analysis)

   -  Analytical papers and policy briefs that made use of the data

   -  Survey budget and other key planning documents

   -  PowerPoint presentations and other related material

-  Computer programs (used for data entry, editing, tabulation and
   analysis)

-  Photos

-  Tables

-  Maps

-  Survey promotional/informational materials (flyers, videos, posters,
   songs, etc.)

Documents available in electronic format (MS-Word, Excel, and others)
must be preserved in their original format and in PDF format.

All documents available only on hard copy must be scanned. Use low
resolution graphics, and black & white option (unless it is crucial to
preserve colours) to avoid large file sizes. A scanning resolution of
300 dpi is recommended. Save the scanned documents in PDF format. OCR is
useful, although not required.

Scan all resources with an updated virus detection application.

3. Importing data and establishing relationships
================================================

After all data and documentation files are gathered and checked, import
the data files in the Editor. In the Metadata Editor, order the files
in a logical fashion (e.g., sequentially through sections).

.. note::
   If you are documenting a population census and have very large
   data files, it is recommended to split the files by geographic area.
   Typically, you will have a file at individual level, one at the
   household level, and possibly one at the community level, for each
   State or Province. In such case, import all files for one State or
   Province only. You will import the other data files after you
   complete the documentation of the files. This will considerably
   reduce the time needed to save your files. The Metadata Editor will 
   allow you to replicate the metadata from the documented files to all 
   other data files that you will import later.

After all files are imported and ordered in a proper sequence, define
the key variables for each data file. The base key variable(s) in a data
file is (are) the variable(s) that provide the unique identifier of each
record in that specific data file.

Then establish the relations and validate them using the *Tool >
Validate Dataset Relations* in the Editor. This automatic validation is 
a way to check the structural integrity of the identifier variables and
assure there are no duplicates in the data.

+--------------------------------------------------------------------+
| Establishing relationships – An example                            |
+====================================================================+
|In this example, we assume that the dataset is obtained from a      |
|household budget survey and comprises:                              |
|                                                                    |
|- A household-level file “hhld.dat” with the household              |
|  characteristics (one record per household). Each household is     |
|  identified by a variable named *hhid*.                            |
|                                                                    |
|- A household-level file “hhld.dat” with the household (one record  |
|  per person).Each household member is identified by the combination|
|  of variables *hhid and memno*.                                    |
|                                                                    |
|- A consumption data file “cons.dat”, with one record per item      |
|  (goods and services) per household. Each record is uniquely       |
|  identified by the combination of variables *hhid* and *itemno*.   |
|  The file also contains a variable *district* identifying the      |
|  district where the household resides.                             |
|                                                                    |
|- A data file “prices.dat” with average price per commodity, per    |
|  district (one record per item per district). Each record is       |
|  uniquely identified by variables *district* and *itemno*.         |
+--------------------------------------------------------------------+
|                   .. image:: media/image5.png                      |
+--------------------------------------------------------------------+
|In the Metadata Editor, these relationships will be established as  |
|follows in the “Key variables and relationships” section of each    |
|data file:                                                          |
+--------------------------------------------------------------------+
|                   .. image:: media/Page21.png                      |
+--------------------------------------------------------------------+

If you have imported your data from any format other than fixed ASCII,
re-sequence the data using the *Variables* > *Resequence* option in the
Editor. This re-sequencing tool will automatically fill the “StartCol”
and “EndCol” columns in the variable description section. This must be
done for each data file.

.. image:: media/Page22.png

Before going further, quickly browse all variables in all data files to
visually check the frequencies. This will allow you to easily spot some
outliers or invalid codes, which will require recoding (which can be
done in the Editor or in the source data files which will then have to
be re-imported).

.. image:: media/Page22_2.png

Save the project. The Editor saves the full project, the associated data
and documentation in one zip file. We recommend you save the project using
the survey abbreviation, year and version number as project name
(e.g., UGA_2018_HIES_v01_M). Note that it is good practice to avoid using
spaces in a file name (use underscore characters instead).

4. Importing external resources
===============================

+----------------------------+-----------------------+------------------+
|Before importing your external resources, create folders in the Editor |
|as necessary (these are directories in the External Resources section  |
|in the Editor, not new directories on your hard drive). If you have    |
|very few external resources, all resources can be listed in the root   |
|directory. If you have many, organize them by type of resources (in the|
|example below, we have created separate directories for the            |
|Questionnaires, Technical Documents, Computer Programs, Reports,       |
|Tables, Photos and Maps).                                              |
+----------------------------+-----------------------+------------------+
|.. image:: media/image11.png| Create an entry for each resource by     |
|                            | entering a label in the Resource         |
|                            |                                          |
|                            | Information field. This label should be  |
|                            | short but explicit. Then identify the    |
|                            |                                          |
|                            | resource file in the  “Resource” field.  |
|                            | The field “Resource” is used to indicate |
|                            |                                          |
|                            | the filename or URL location (website) of|
|                            | the external resource. The resource      |
|                            |                                          |
|                            | consists of the filename, and a relative |
|                            | path. The reason for entering a relative |
|                            |                                          |
|                            | path is that it will allow you to move   |
|                            | the whole study directory and its        |
|                            |                                          |
|                            | subdirectories to another location or    |
|                            | another drive, without having to re-enter|
|                            |                                          |
|                            | the location of the files.               |
+----------------------------+-----------------------+------------------+
|Example:                                                               |
|                                                                       |
|Let’s assume your study is a Household Budget Survey conducted in 2018.| 
|If you followed the recommendations made in the introductory chapter   |
|“Before you start – Organizing your files”, you will have created a    |
|directory like C:\ UGA_2018_HIES. Suppose also that a document titled  |
|Report2018.pdf is saved in a directory C:\ UGA_2018_HIES\Doc. When you |
|fill the resource field in the External Resources page, do NOT enter   |
|“C:\ UGA_2018_HIES\Doc\Report2018.pdf.pdf. Enter the file name as      |
|follows: Doc\Reports\Report2018.pdf                                    |
|                                                                       |
|.. image:: media/Page22_3.png                                          |
+----------------------------+-----------------------+------------------+

Some resources might be composed of more than one file (for example, the
CSPro data entry application includes multiple files that should not be
separated). In such cases, zip them into one single file, and import it
as a single resource.

For documents available in multiple formats (for example, a
questionnaire available in Excel and in PDF), you may create two
separate resources, or zip the files into one single file. In such case,
list the different formats available in the “Content/ Description”
field.

+--------------------------------------------------------------------+
|*Best Practices – Naming Convention for External Resources*         |
|                                                                    |
|- Use file names short, but self-explanatory about the content of   |
|  the document.                                                     |
|- Preferably, use lower cases.                                      |
|- Avoid spaces to delimit words.                                    |
|- Be consistent with your method of naming across all files. For    |
|  instance, if you use underscores to delimit words, keep it that   |
|  way in all files.                                                 |
|- Use only alphanumeric characters, underscores or dashes. Avoid    |
|  using special characters (!@#$%^&*()~) or any accented characters.|
|- If you intend to have an archive useable and downloadable across  |
|  multiple countries, use English names for your files.             |
+--------------------------------------------------------------------+

5. Completing metadata
======================

The Metadata Editor makes use of the Data Documentation Initiative
(DDI Version 2.5), the Dublin Core (DCMI version X) metadata standards
and ISO 19139 for geospatial information. 

The table below provides an overview of the different metadata standards
as related to the project. Each metadata standard is integrated into the
template that will define the project.


.. image:: media/Page23.png

A thorough completion of the DDI and DCMI elements will significantly
raise the value of the archiving work by providing users with the
necessary information to put the study into its proper context and to
understand its purpose.

The DDI requires completion of the following sections: Document
Description, Study Description, Datasets, Variables Groups, and
External Resources. Recommendations for each field included in the
IHSN template are provided below. 

+--------------------------------------------------------------------+
| The IHSN recommends using the standardized IHSN DDI/DCMI templates |
| (Study Template and External Resources Template). This Quick       |
| Reference Guide is based on these two templates. Visit the IHSN    |
| website to download the latest version of these templates,         |
| available in multiple languages.                                   |
+--------------------------------------------------------------------+

**Overall recommendations:**

-  As an archivist, you may need to seek assistance from key experts
   involved in some of the technical aspects of the survey.

-  As a general rule, avoid using ALL CAPS when you fill DDI fields.
   Also, check the spelling of all entries. The Editor does not provide
   (yet) an automatic spell checker.

-  Some of the examples below present an optimal documentation of some
   fields. In many cases, for past surveys, you will not find such
   detailed information. Try to provide as much detail as possible. For
   future surveys, the information should be compiled and provided
   during the whole life cycle of the survey. This will ensure that the
   best possible documentation is available at completion of that
   survey.

5.1. Good practices for completing the Document Description
-----------------------------------------------------------

Documenting a study using the DDI and DCMI metadata standards consists
of generating a metadata file which will be saved in XML format in what
is called an *XML Document*. The *Document Description* described below
is a description of that XML file. The IHSN Template selected 4 elements
to describe the DDI document.

+-----------------------------------+-----------------------------------+
| Metadata Producer                 |Name of the person(s) or           |
|                                   |organization(s) who documented     |
|                                   |the dataset. Use the "role"        |
|                                   |attribute to distinguish           |
|                                   |different stages of involvement    |
|                                   |in the production process.         |
|                                   |                                   |
|                                   |Example:                           |
|                                   +----------------+------------------+
|                                   |   *Name*       |*Role*            |
|                                   +----------------+------------------+
|                                   | *National      |*Documentation    |
|                                   | Statistics     |of the            |
|                                   | Office         |study*            |
|                                   | (NSO)*         |                  |
|                                   +----------------+------------------+
|                                   | *International |*Review of        |
|                                   | Household      |the               |
|                                   | Survey         |metadata*         |
|                                   | Network        |                  |
|                                   | (IHSN)*        |                  |
|                                   |                |                  |
+-----------------------------------+----------------+------------------+
| Date of Production                |This is the date (in ISO format    |
|                                   |YYYY-MM-DD) the DDI document was   |
|                                   |produced (not distributed or       |
|                                   |archived). This date will be       |
|                                   |automatically imputed when you     |
|                                   |save the file.                     |
+-----------------------------------+-----------------------------------+
| DDI Document Version              |Documenting a dataset is not a     |
|                                   |trivial exercise. Producing        |
|                                   |“perfect” metadata is probably     |
|                                   |impossible. It may therefore       |
|                                   |happen that, having identified     |
|                                   |errors in a DDI document or        |
|                                   |having received suggestions for    |
|                                   |improvement, you decide to modify  |
|                                   |the Document even after a first    |
|                                   |version has been disseminated.     |
|                                   |This element is used to identify   |
|                                   |and describe the current version   |
|                                   |of the document. It is good        |
|                                   |practice to provide a version      |
|                                   |number (and date), and             |
|                                   |information on what distinguishes  |
|                                   |this version from the previous     |
|                                   |one(s) if relevant.                |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  *Version 02 (July 2017). This    |
|                                   |  version is identical to version  |
|                                   |  01, except for the section on    |
|                                   |  Data Appraisal which was         |
|                                   |  updated.*                        |
+-----------------------------------+-----------------------------------+
| DDI Document ID Number            |The ID number of a DDI document    |
|                                   |is a unique number that is used    |
|                                   |to identify this DDI file. Define  |
|                                   |and use a consistent scheme to     |
|                                   |use. Such an ID could be           |
|                                   |constructed as follows:            |
|                                   |DDI-country-producer-survey-year   |
|                                   |where                              |
|                                   |                                   |
|                                   |-  *country* is the 3-letter ISO   |
|                                   |   country abbreviation            |
|                                   |                                   |
|                                   |-  *producer* is the abbreviation  |
|                                   |   of the producing agency         |
|                                   |                                   |
|                                   |-  *survey* is the survey          |
|                                   |   abbreviation                    |
|                                   |                                   |
|                                   |-  *year* is the reference year    |
|                                   |   (or the year the survey         |
|                                   |   started)                        |
|                                   |                                   |
|                                   |- DDI document version number      |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  *The DDI file related to the     |
|                                   |  Demographic and Health Survey    |
|                                   |  documented by staff from the     |
|                                   |  Uganda Bureau of Statistics in   |
|                                   |  2005 would have the following    |
|                                   |  ID:                              |
|                                   |  DDI-UGA-UBOS-DHS-2005-v01. If    |
|                                   |  the same survey is documented by |
|                                   |  a staff from the IHSN, this      |
|                                   |  would be                         |
|                                   |  DDI-UGA-IHSN-DHS-205-v01.*       |
+-----------------------------------+-----------------------------------+

5.2. Good practices for completing the Study Description
--------------------------------------------------------

In the DDI standard, the Study Description is the section that contains
all elements needed to describe the study itself (investigators, dates
and methods, scope and coverage, etc.)

+-----------------------------------+-----------------------------------+
| **Identification**                                                    |
+-----------------------------------+-----------------------------------+
| Title                             |The title is the official name of  |
|                                   |the survey as it is stated on the  |
|                                   |questionnaire or as it appears in  |
|                                   |the design documents. The          |
|                                   |following items should be noted:   |
|                                   |                                   |
|                                   |-  Include the reference year(s)   |
|                                   |   of the survey in the title.     |
|                                   |                                   |
|                                   |-  Do not include the              |
|                                   |   abbreviation of the survey      |
|                                   |   name in the title.              |
|                                   |                                   |
|                                   |-  As the survey title is a        |
|                                   |   proper noun, the first letter   |
|                                   |   of each word should be          |
|                                   |   capitalized (except for         |
|                                   |   prepositions or other           |
|                                   |   conjunctions).                  |
|                                   |                                   |
|                                   |-  Including the country name in   |
|                                   |   the title is optional.          |
|                                   |                                   |
|                                   |The title will in most cases be    |
|                                   |identical to the Document Title    |
|                                   |(see above).                       |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  -  *National Household Budget    |
|                                   |     Survey 2002-2003*             |
|                                   |                                   |
|                                   |  -  *Popstan Multiple Indicator   |
|                                   |     Cluster Survey 2002*          |
+-----------------------------------+-----------------------------------+
| Subtitle                          |Subtitle is optional and rarely    |
|                                   |used. A subtitle can be used to    |
|                                   |add information usually            |
|                                   |associated with a sequential       |
|                                   |qualifier for a survey.            |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  *Title: Welfare Monitoring       |
|                                   |  Survey 2007*                     |
|                                   |                                   |
|                                   |  *Subtitle: Fifth round*          |
+-----------------------------------+-----------------------------------+
| Abbreviation                      |The abbreviation of a survey is    |
|                                   |usually the first letter of each   |
|                                   |word of the titled survey. The     |
|                                   |survey reference year(s) may be    |
|                                   |included.                          |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  -  *DHS 2000 for “Demographic and|
|                                   |     Health Survey 2005”*          |
|                                   |                                   |
|                                   |  -  *HIES 2002-2003 for “Household|
|                                   |     Income and Expenditure Survey |
|                                   |     2003”*                        |
+-----------------------------------+-----------------------------------+
| Study type                        |The study type or *survey type*    |
|                                   |is the broad category defining     |
|                                   |the survey. This item has a        |
|                                   |controlled vocabulary (you may     |
|                                   |customize the IHSN template to     |
|                                   |adjust this controlled vocabulary  |
|                                   |if needed).                        |
+-----------------------------------+-----------------------------------+
| Series information                |A survey may be repeated at        |
|                                   |regular intervals (such as an      |
|                                   |annual labour force survey), or    |
|                                   |be part of an international        |
|                                   |survey program (such as the MICS,  |
|                                   |CWIQ, DHS, LSMS and others). The   |
|                                   |Series information is a            |
|                                   |description of this “collection”   |
|                                   |of surveys. A brief description    |
|                                   |of the characteristics of the      |
|                                   |survey, including when it          |
|                                   |started, how many rounds were      |
|                                   |already implemented, and who is    |
|                                   |in charge would be provided here.  |
|                                   |If the survey does not belong to   |
|                                   |a series, leave this field empty.  |
|                                   |                                   |
|                                   |Example:                           |
|                                   | *The Multiple Indicator Cluster   |
|                                   | Survey, Round 3 (MICS3) is the    |
|                                   | third round of MICS surveys,      |
|                                   | previously conducted around 1995  |
|                                   | (MICS1) and 2000 (MICS2). MICS    |
|                                   | surveys are designed by UNICEF,   |
|                                   | and implemented by national       |
|                                   | agencies in participating         |
|                                   | countries. MICS was designed to   |
|                                   | monitor various indicators        |
|                                   | identified at the World Summit    |
|                                   | for Children and the Millennium   |
|                                   | Development Goals.                |
|                                   | Many questions and indicators in  |
|                                   | MICS3 are consistent and          |
|                                   | compatible with the prior round   |
|                                   | of MICS (MICS2) but less so with  |
|                                   | MICS1, although there have been a |
|                                   | number of changes in definition   |
|                                   | of indicators between rounds.*    |
|                                   |                                   |
|                                   | *Round 1 covered X countries,     |
|                                   | round 2 covered Y countries, and  |
|                                   | Round Z covered N countries.*     |
+-----------------------------------+-----------------------------------+
| Translated title                  |In countries with more than one    |
|                                   |official language, a translation   |
|                                   |of the title may be provided.      |
|                                   |Likewise, the translated title     |
|                                   |may simply be a translation into   |
|                                   |English from a country’s own       |
|                                   |language. Special characters       |
|                                   |should be properly displayed       |
|                                   |(such as accents and other stress  |
|                                   |marks or different alphabets).     |
+-----------------------------------+-----------------------------------+
| ID Number                         |The ID number of a dataset is a    |
|                                   |unique number that is used to      |
|                                   |identify a particular survey.      |
|                                   |Define and use a consistent        |
|                                   |scheme to use. Such an ID could    |
|                                   |be constructed as follows:         |
|                                   |country-producer-survey-year-vers  |
|                                   |ion                                |
|                                   |where                              |
|                                   |                                   |
|                                   |-  *country* is the 3-letter ISO   |
|                                   |   country abbreviation            |
|                                   |                                   |
|                                   |-  *producer* is the abbreviation  |
|                                   |   of the producing agency         |
|                                   |                                   |
|                                   |-  *survey* is the survey          |
|                                   |   abbreviation                    |
|                                   |                                   |
|                                   |-  *year* is the reference year    |
|                                   |   (or the year the survey         |
|                                   |   started)                        |
|                                   |                                   |
|                                   |-  *version* is the number         |
|                                   |   dataset version number (see     |
|                                   |   Version Description below)      |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  *The Demographic and Health      |
|                                   |  Survey implemented by the Uganda |
|                                   |  Bureau of Statistics in 2005     |
|                                   |  could have the following ID:*    |
|                                   |                                   |
|                                   |  *UGA-UBOS-DHS-2005-v01.*         |
+-----------------------------------+-----------------------------------+
| **Version**                                                           |
+-----------------------------------+-----------------------------------+
| Description                       |The version description should     |
|                                   |contain a version number followed  |
|                                   |by a version label. The version    |
|                                   |number should follow a standard    |
|                                   |convention to be adopted by the    |
|                                   |institute. We recommend that       |
|                                   |larger series be defined by a      |
|                                   |number to the left of a decimal    |
|                                   |and iterations of the same series  |
|                                   |by a sequential number that        |
|                                   |identifies the release. Larger     |
|                                   |series will typically include (0)  |
|                                   |the raw, unedited dataset; (1)     |
|                                   |the edited dataset, non            |
|                                   |anonymized, for internal use at    |
|                                   |the data producing agency; and     |
|                                   |(2) the edited dataset, prepared   |
|                                   |for dissemination to secondary     |
|                                   |users (possibly anonymized).       |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  -  *v0.1: Basic raw data,        |
|                                   |     obtained from data entry      |
|                                   |     (before editing)*.            |
|                                   |                                   |
|                                   |  -  *v1.2: Edited data, second    |
|                                   |     version, for internal use     |
|                                   |     only*.                        |
|                                   |                                   |
|                                   |  -  *v2.1: Edited, anonymous      |
|                                   |     dataset for public            |
|                                   |     distribution*.                |
|                                   |                                   |
|                                   |A brief description of the version |
|                                   |should follow the numerical        |
|                                   |identification.                    |
+-----------------------------------+-----------------------------------+
| Production date                   |This is the date in ISO format     |
|                                   |(yyyy-mm-dd) of actual and final   |
|                                   |production of the data.            |
|                                   |Production dates of all versions   |
|                                   |should be carefully tracked.       |
|                                   |Provide at least the month and     |
|                                   |year. Use the calendar icon in     |
|                                   |the Metadata editor to assure      |
|                                   |that the date selected is in       |
|                                   |compliance with the ISO format.    |
+-----------------------------------+-----------------------------------+
| Notes                             |Version notes should provide a     |
|                                   |brief report on the changes made   |
|                                   |through the versioning process.    |
|                                   |The note should indicate how this  |
|                                   |version differs from other         |
|                                   |versions of the same dataset.      |
+-----------------------------------+-----------------------------------+
| **Overview**                                                          |
+-----------------------------------+-----------------------------------+
| Abstract                          |The abstract should provide a      |
|                                   |clear summary of the purposes,     |
|                                   |objectives and content of the      |
|                                   |survey. It should be written by a  |
|                                   |researcher or survey statistician  |
|                                   |aware of the survey.               |
+-----------------------------------+-----------------------------------+
| Kind of data                      |This field is a broad              |
|                                   |classification of the data and it  |
|                                   |is associated with a drop down     |
|                                   |box providing controlled           |
|                                   |vocabulary. That controlled        |
|                                   |vocabulary includes 9 items but    |
|                                   |is not limited to them.            |
+-----------------------------------+-----------------------------------+
| Unit of analysis                  |A survey could have various units  |
|                                   |of analysis. These are fairly      |
|                                   |standard and are usually:          |
|                                   |                                   |
|                                   |-  Household (household survey,    |
|                                   |   census)                         |
|                                   |                                   |
|                                   |-  Person (household survey,       |
|                                   |   census)                         |
|                                   |                                   |
|                                   |-  Enterprise (enterprise survey)  |
|                                   |                                   |
|                                   |-  Commodity (household survey,    |
|                                   |   price survey)                   |
|                                   |                                   |
|                                   |-  Plots of land (agricultural     |
|                                   |   survey)                         |
+-----------------------------------+-----------------------------------+
| **Scope**                                                             |
+-----------------------------------+-----------------------------------+
| Description of scope              |The scope is a description of the  |
|                                   |themes covered by the survey. It   |
|                                   |can be viewed as a summary of the  |
|                                   |modules that are included in the   |
|                                   |questionnaire. The scope does not  |
|                                   |deal with geographic coverage.     |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  The scope of the Multiple        |
|                                   |  Indicator Cluster Survey         |
|                                   |  includes:                        |
|                                   |                                   |
|                                   |  -  *HOUSEHOLD: Household         |
|                                   |     characteristics, household    |
|                                   |     listing, orphaned and         |
|                                   |     vulnerable children,          |
|                                   |     education, child labour, water|
|                                   |     and sanitation, household use |
|                                   |     of insecticide treated        |
|                                   |     mosquito nets, and salt       |
|                                   |     iodization, with optional     |
|                                   |     modules for child discipline, |
|                                   |     child disability, maternal    |
|                                   |     mortality and security of     |
|                                   |     tenure and durability of      |
|                                   |     housing.*                     |
|                                   |                                   |
|                                   |  -  *WOMEN: Women's               |
|                                   |     characteristics, child        |
|                                   |     mortality, tetanus toxoid,    |
|                                   |     maternal and newborn health,  |
|                                   |     marriage, polygyny, female    |
|                                   |     genital cutting,              |
|                                   |     contraception, and HIV/AIDS   |
|                                   |     knowledge, with optional      |
|                                   |     modules for unmet need,       |
|                                   |     domestic violence, and sexual |
|                                   |     behavior.*                    |
|                                   |                                   |
|                                   |  -  *CHILDREN: Children's         |
|                                   |     characteristics, birth        |
|                                   |     registration and early        |
|                                   |     learning, vitamin A,          |
|                                   |     breastfeeding, care of        |
|                                   |     illness, malaria,             |
|                                   |     immunization, and             |
|                                   |     anthropometry, with an        |
|                                   |     optional module for child     |
|                                   |     development.*                 |
+-----------------------------------+-----------------------------------+
| Topic classifications             |A topic classification             |
|                                   |facilitates referencing and        |
|                                   |searches in electronic survey      |
|                                   |catalogs. Topics should be         |
|                                   |selected from a standard           |
|                                   |thesaurus, preferably an           |
|                                   |international, multilingual        |
|                                   |thesaurus. The IHSN recommends     |
|                                   |the use of the thesaurus used by   |
|                                   |the Council of European Social     |
|                                   |Science Data Archives (CESSDA).    |
|                                   |The CESSDA thesaurus has been      |
|                                   |introduced as a controlled         |
|                                   |vocabulary in the IHSN Study       |
|                                   |Template version 1.3 (available    |
|                                   |`www.surveynetwork.org/toolkit <h  |
|                                   |ttp://www.surveynetwork.org/toolk  |
|                                   |it>`__).                           |
+-----------------------------------+-----------------------------------+
| Keywords                          |Keywords summarize the content or  |
|                                   |subject matter of the survey. As   |
|                                   |topic classifications, these are   |
|                                   |used to facilitate referencing     |
|                                   |and searches in electronic survey  |
|                                   |catalogs. Keywords should be       |
|                                   |selected from a standard           |
|                                   |thesaurus, preferably an           |
|                                   |international, multilingual        |
|                                   |thesaurus. Entering a list of      |
|                                   |keywords is tedious. This option   |
|                                   |is provided for advanced users     |
|                                   |only.                              |
+-----------------------------------+-----------------------------------+
| **Coverage**                                                          |
+-----------------------------------+-----------------------------------+
| Country                           | Enter the country name, even in   |
|                                   | cases where the survey did not    |
|                                   | cover the entire country. In the  |
|                                   | field “Abbreviation”, we          |
|                                   | recommend that you enter the      |
|                                   | 3-letter ISO code of the country. |
|                                   | If the dataset you document       |
|                                   | covers more than one country,     |
|                                   | enter all in separate rows.       |
+-----------------------------------+-----------------------------------+
| Geographic coverage               |This filed aims at describing at   |
|                                   |what geographic level the data     |
|                                   |are representative. Typical        |
|                                   |entries will be “National          |
|                                   |coverage”, “Urban (or rural)       |
|                                   |areas only”, “state of …”,         |
|                                   |“Capital city”, etc.               |
|                                   |                                   |
|                                   |Note that we do not describe here  |
|                                   |where the data was collected. For  |
|                                   |example, as sample survey could    |
|                                   |be declared as “national           |
|                                   |coverage” even in cases where      |
|                                   |some districts where not included  |
|                                   |in the sample, as long as the      |
|                                   |sampling strategy was such that    |
|                                   |the representativity is national.  |
+-----------------------------------+-----------------------------------+
| Universe                          |We are interested here in the      |
|                                   |survey universe (not the universe  |
|                                   |of particular sections of the      |
|                                   |questionnaires or variables),      |
|                                   |i.e. in the identification of the  |
|                                   |population of interest in the      |
|                                   |survey. The universe will rarely   |
|                                   |be the entire population of the    |
|                                   |country. Sample household          |
|                                   |surveys, for example, usually do   |
|                                   |not cover homeless, nomads,        |
|                                   |diplomats, community households.   |
|                                   |Population censuses do not cover   |
|                                   |diplomats. Try to provide the      |
|                                   |most detailed information          |
|                                   |possible on the population         |
|                                   |covered by the survey/census.      |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  *The survey covered all de jure  |
|                                   |  household members (usual         |
|                                   |  residents), all women aged 15-49 |
|                                   |  years resident in the household, |
|                                   |  and all children aged 0-4 years  |
|                                   |  (under age 5) resident in the    |
|                                   |  household.*                      |
+-----------------------------------+-----------------------------------+
| **Producers and Sponsors**                                            |
+-----------------------------------+-----------------------------------+
| Primary investigator              |The primary investigator will in   |
|                                   |most cases be an institution, but  |
|                                   |could also be an individual in     |
|                                   |the case of small-scale academic   |
|                                   |surveys. The two fields to be      |
|                                   |completed are the Name and the     |
|                                   |Affiliation fields. Generally, in  |
|                                   |a survey, the Primary              |
|                                   |Investigator will be the           |
|                                   |institution implementing the       |
|                                   |survey. If various institutions    |
|                                   |have been equally involved as      |
|                                   |main investigators, then all       |
|                                   |should be mentioned. This only     |
|                                   |includes the agencies responsible  |
|                                   |for the implementation of the      |
|                                   |survey, not its funding or         |
|                                   |technical assistance. The order    |
|                                   |in which they are listed is        |
|                                   |discretionary. It can be           |
|                                   |alphabetic or by significance of   |
|                                   |contribution. Individual persons   |
|                                   |can also be mentioned. If persons  |
|                                   |are mentioned use the appropriate  |
|                                   |format of Surname, First name.     |
+-----------------------------------+-----------------------------------+
| Other producers                   |This field is provided to list     |
|                                   |other interested parties and       |
|                                   |persons that have played a         |
|                                   |significant but not the leading    |
|                                   |technical role in implementing     |
|                                   |and producing the data. The        |
|                                   |specific fields to be competed     |
|                                   |are: Name of the organization,     |
|                                   |Abbreviation, Affiliation and      |
|                                   |Role. If any of the fields are     |
|                                   |not applicable these can be left   |
|                                   |blank. The abbreviations should    |
|                                   |be the official abbreviation of    |
|                                   |the organization. The role should  |
|                                   |be a short and succinct phrase or  |
|                                   |description on the specific        |
|                                   |assistance provided by the         |
|                                   |organization in order to produce   |
|                                   |the data. The roles should be      |
|                                   |standard vocabulary such as:       |
|                                   |                                   |
|                                   |-  [Technical assistance in]       |
|                                   |   questionnaire design            |
|                                   |                                   |
|                                   |-  [Technical assistance in]       |
|                                   |   sampling methodology /          |
|                                   |   selection                       |
|                                   |                                   |
|                                   |-  [Technical assistance in] data  |
|                                   |   collection                      |
|                                   |                                   |
|                                   |-  [Technical assistance in] data  |
|                                   |   processing                      |
|                                   |                                   |
|                                   |-  [Technical assistance in] data  |
|                                   |   analysis                        |
|                                   |                                   |
|                                   |Do not include here the financial  |
|                                   |sponsors.                          |
+-----------------------------------+-----------------------------------+
| Funding                           |List the organizations (national   |
|                                   |or international) that have        |
|                                   |contributed, in cash or in kind,   |
|                                   |to the financing of the survey.    |
|                                   |The government institution that    |
|                                   |has provided funding should not    |
|                                   |be forgotten.                      |
+-----------------------------------+-----------------------------------+
| Other acknowledgements            |This optional field can be used    |
|                                   |to acknowledge any other people    |
|                                   |and institutions that have in      |
|                                   |some form contributed to the       |
|                                   |survey.                            |
+-----------------------------------+-----------------------------------+
| **Sampling**                                                          |
+-----------------------------------+-----------------------------------+
| Sampling procedure                |This field only applies to sample  |
|                                   |surveys. Information on sampling   |
|                                   |procedure is crucial (although     |
|                                   |not applicable for censuses and    |
|                                   |administrative datasets). This     |
|                                   |section should include summary     |
|                                   |information that includes though   |
|                                   |is not limited to:                 |
|                                   |                                   |
|                                   |-  Sample size                     |
|                                   |                                   |
|                                   |-  Selection process (e.g.,        |
|                                   |   probability proportional to     |
|                                   |   size or over sampling)          |
|                                   |                                   |
|                                   |-  Stratification (implicit and    |
|                                   |   explicit)                       |
|                                   |                                   |
|                                   |-  Stages of sample selection      |
|                                   |                                   |
|                                   |-  Design omissions in the sample  |
|                                   |                                   |
|                                   |-  Level of representation         |
|                                   |                                   |
|                                   |-  Strategy for absent             |
|                                   |   respondents/not found/refusals  |
|                                   |   (replacement or not)            |
|                                   |                                   |
|                                   |-  Sample frame used, and listing  |
|                                   |   exercise conducted to update    |
|                                   |   it                              |
|                                   |                                   |
|                                   |It is useful also to indicate      |
|                                   |here what variables in the data    |
|                                   |files identify the various levels  |
|                                   |of stratification and the primary  |
|                                   |sample unit. These are crucial to  |
|                                   |the data users who want to         |
|                                   |properly account for the sampling  |
|                                   |design in their analyses and       |
|                                   |calculations of sampling errors.   |
|                                   |                                   |
|                                   |This section accepts only text     |
|                                   |format; formulae cannot be         |
|                                   |entered. In most cases, technical  |
|                                   |documents will exist that          |
|                                   |describe the sampling strategy in  |
|                                   |detail. In such cases, include     |
|                                   |here a reference                   |
|                                   |(title/author/date) to this        |
|                                   |document, and make sure that the   |
|                                   |document is provided in the        |
|                                   |External Resources.                |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  *5000 households were selected   |
|                                   |  for the sample. Of these, 4996   |
|                                   |  were occupied households and 4811|
|                                   |  were successfully interviewed for|
|                                   |  a response rate of 96.3%. Within |
|                                   |  these households, 7815 eligible  |
|                                   |  women aged 15-49 were identified |
|                                   |  for interview, of which 7505 were|
|                                   |  successfully interviewed         |
|                                   |  (response rate 96.0%), and 3242  |
|                                   |  children aged 0-4 were identified|
|                                   |  for whom the mother or caretaker |
|                                   |  was successfully interviewed for |
|                                   |  3167 children (response rate     |
|                                   |  97.7%). These give overall       |
|                                   |  response rates (household        |
|                                   |  response rate times individual   |
|                                   |  response rate) for the women's   |
|                                   |  interview of 92.5% and for the   |
|                                   |  children's interview of 94.1%.*  |
+-----------------------------------+-----------------------------------+
| Deviation from sample design      |This field only applies to sample  |
|                                   |surveys.                           |
|                                   |                                   |
|                                   |Sometimes the reality of the       |
|                                   |field requires a deviation from    |
|                                   |the sampling design (for example   |
|                                   |due to difficulty to access to     |
|                                   |zones due to weather problems,     |
|                                   |political instability, etc). If    |
|                                   |for any reason, the sample design  |
|                                   |has deviated, this should be       |
|                                   |reported here.                     |
+-----------------------------------+-----------------------------------+
| Response rates                    |Response rate provides that        |
|                                   |percentage of households (or       |
|                                   |other sample unit) that            |
|                                   |participated in the survey based   |
|                                   |on the original sample size.       |
|                                   |Omissions may occur due to         |
|                                   |refusal to participate,            |
|                                   |impossibility to locate the        |
|                                   |respondent, or other. Sometimes,   |
|                                   |a household may be replaced by     |
|                                   |another by design. Check that the  |
|                                   |information provided here is       |
|                                   |consistent with the sample size    |
|                                   |indicated in the “Sampling         |
|                                   |procedure field” and the number    |
|                                   |of records found in the dataset    |
|                                   |(for example, if the sample        |
|                                   |design mention a sample of 5,000   |
|                                   |households and the data on         |
|                                   |contain data on 4,500 households,  |
|                                   |the response rate should not be    |
|                                   |100 percent).                      |
|                                   |                                   |
|                                   |Provide if possible the response   |
|                                   |rates by stratum. If information   |
|                                   |is available on the causes of      |
|                                   |non-response (refusal/not          |
|                                   |found/other), provide this         |
|                                   |information as well.               |
|                                   |                                   |
|                                   |This field can also in some cases  |
|                                   |be used to describe non-responses  |
|                                   |in population censuses.            |
+-----------------------------------+-----------------------------------+
| Weighting                         |This field only applies to sample  |
|                                   |surveys.                           |
|                                   |                                   |
|                                   |Provide here the list of           |
|                                   |variables used as weighting        |
|                                   |coefficient. If more than one      |
|                                   |variable is a weighting variable,  |
|                                   |describe how these variables       |
|                                   |differ from each other and what    |
|                                   |the purpose of each one of them    |
|                                   |is.                                |
|                                   |                                   |
|                                   |Example:                           |
|                                   | *Sample weights were calculated   |
|                                   | for each of the data files.*      |
|                                   |                                   |
|                                   | *Sample weights for the household |
|                                   | data were computed as the inverse |
|                                   | of the probability of selection   |
|                                   | of the household, computed at the |
|                                   | sampling domain level             |
|                                   | (urban/rural within each region). |
|                                   | The household weights were        |
|                                   | adjusted for non-response at the  |
|                                   | domain level, and were then       |
|                                   | normalized by a constant factor   |
|                                   | so that the total weighted number |
|                                   | of households equals the total    |
|                                   | unweighted number of households.  |
|                                   | The household weight variable is  |
|                                   | called HHWEIGHT and is used with  |
|                                   | the HH data and the HL data.*     |
|                                   |                                   |
|                                   | *Sample weights for the women's   |
|                                   | data used the un-normalized       |
|                                   | household weights, adjusted for   |
|                                   | non-response for the women's      |
|                                   | questionnaire, and were then      |
|                                   | normalized by a constant factor   |
|                                   | so that the total weighted number |
|                                   | of women's cases equals the total |
|                                   | unweighted number of women's      |
|                                   | cases.*                           |
|                                   |                                   |
|                                   | *Sample weights for the           |
|                                   | children's data followed the same |
|                                   | approach as the women's and used  |
|                                   | the un-normalized household       |
|                                   | weights, adjusted for             |
|                                   | non-response for the children's   |
|                                   | questionnaire, and were then      |
|                                   | normalized by a constant factor   |
|                                   | so that the total weighted number |
|                                   | of children's cases equals the    |
|                                   | total unweighted number of        |
|                                   | children's cases.*                |
+-----------------------------------+-----------------------------------+
| **Data Collection**                                                   |
+-----------------------------------+-----------------------------------+
| Dates of data collection          |Enter the dates (at least month    |
|                                   |and year) of the start and end of  |
|                                   |the data collection. They should   |
|                                   |be in the standard ISO format of   |
|                                   |YYYY-MM-DD.                        |
|                                   |                                   |
|                                   |In some cases, data collection     |
|                                   |for a same survey can be           |
|                                   |conducted in waves. In such case,  |
|                                   |you should enter the start and     |
|                                   |end date of each wave separately,  |
|                                   |and identify each wave in the      |
|                                   |“cycle” field.                     |
+-----------------------------------+-----------------------------------+
| Time period                       |This field will usually be left    |
|                                   |empty. Time period differs from    |
|                                   |the dates of collection as they    |
|                                   |represent the period for which     |
|                                   |the data collected are applicable  |
|                                   |or relevant.                       |
+-----------------------------------+-----------------------------------+
| Mode of data collection           |The mode of data collection is     |
|                                   |the manner in which the interview  |
|                                   |was conducted or information was   |
|                                   |gathered. This field is a          |
|                                   |controlled vocabulary field. Use   |
|                                   |the drop-down button in the        |
|                                   |Toolkit to select one option. In   |
|                                   |most cases, the response will be   |
|                                   |“face to face interview”. But for  |
|                                   |some specific kinds of datasets,   |
|                                   |such as for example data on rain   |
|                                   |falls, the response will be        |
|                                   |different.                         |
+-----------------------------------+-----------------------------------+
| Notes on data collection          |This element is provided in order  |
|                                   |to document any specific           |
|                                   |observations, occurrences or       |
|                                   |events during data collection.     |
|                                   |Consider stating such items like:  |
|                                   |                                   |
|                                   |-  Was a training of enumerators   |
|                                   |   held? (elaborate)               |
|                                   |                                   |
|                                   |-  Any events that could have a    |
|                                   |   bearing on the data quality?    |
|                                   |                                   |
|                                   |-  How long did an interview take  |
|                                   |   on average?                     |
|                                   |                                   |
|                                   |-  Was there a process of          |
|                                   |   negotiation between             |
|                                   |   households, the community and   |
|                                   |   the implementing agency?        |
|                                   |                                   |
|                                   |-  Are anecdotal events recorded?  |
|                                   |                                   |
|                                   |-  Have the field teams            |
|                                   |   contributed by supplying        |
|                                   |   information on issues and       |
|                                   |   occurrences during data         |
|                                   |   collection?                     |
|                                   |                                   |
|                                   |-  In what language was the        |
|                                   |   interview conducted?            |
|                                   |                                   |
|                                   |-  Was a pilot survey conducted?   |
|                                   |                                   |
|                                   |-  Were there any corrective       |
|                                   |   actions taken by management     |
|                                   |   when problems occurred in the   |
|                                   |   field?                          |
|                                   |                                   |
|                                   |Example:                           |
|                                   | *The pre-test for the survey took |
|                                   | place from August 15, 2006 -      |
|                                   | August 25, 2006 and included 14   |
|                                   | interviewers who would later      |
|                                   | become supervisors for the main   |
|                                   | survey.*                          |
|                                   |                                   |
|                                   | *Each interviewing team comprised |
|                                   | of 3-4 female interviewers (no    |
|                                   | male interviewers were used due   |
|                                   | to the sensitivity of the subject |
|                                   | matter), together with a field    |
|                                   | editor and a supervisor and a     |
|                                   | driver. A total of 52             |
|                                   | interviewers, 14 supervisors and  |
|                                   | 14 field editors were used. Data  |
|                                   | collection took place over a      |
|                                   | period of about 6 weeks from      |
|                                   | September 2, 2006 until October   |
|                                   | 17, 2006. Interviewing took place |
|                                   | everyday throughout the fieldwork |
|                                   | period, although interviewing     |
|                                   | teams were permitted to take one  |
|                                   | day off per week.*                |
|                                   |                                   |
|                                   | *Interviews averaged 35 minutes   |
|                                   | for the household questionnaire   |
|                                   | (excluding salt testing), 23      |
|                                   | minutes for the women's           |
|                                   | questionnaire, and 27 for the     |
|                                   | under five children's             |
|                                   | questionnaire (excluding the      |
|                                   | anthropometry). Interviews were   |
|                                   | conducted primarily in English    |
|                                   | and Mumbo-jumbo, but occasionally |
|                                   | used local translation in         |
|                                   | double-Dutch, when the respondent |
|                                   | did not speak English or          |
|                                   | Mumbo-jumbo.*                     |
|                                   |                                   |
|                                   | *Six staff members of GenCenStat  |
|                                   | provided overall fieldwork        |
|                                   | coordination and supervision. The |
|                                   | overall field coordinator was     |
|                                   | Mrs. Doe.*                        |
+-----------------------------------+-----------------------------------+
| Questionnaires                    |This element is provided to        |
|                                   |describe the questionnaire(s)      |
|                                   |used for the data collection. The  |
|                                   |following should be mentioned:     |
|                                   |                                   |
|                                   |-  List of questionnaires and      |
|                                   |   short description of each (all  |
|                                   |   questionnaires must be          |
|                                   |   provided as External            |
|                                   |   Resources)                      |
|                                   |                                   |
|                                   |-  In what language were the       |
|                                   |   questionnaires published?       |
|                                   |                                   |
|                                   |-  Information on the              |
|                                   |   questionnaire design process    |
|                                   |   (based on a previous            |
|                                   |   questionnaire, based on a       |
|                                   |   standard model questionnaire,   |
|                                   |   review by stakeholders). If a   |
|                                   |   document was compiled that      |
|                                   |   contains the comments provided  |
|                                   |   by the stakeholders on the      |
|                                   |   draft questionnaire, or a       |
|                                   |   report prepared on the          |
|                                   |   questionnaire testing, a        |
|                                   |   reference to these documents    |
|                                   |   should be provided here and     |
|                                   |   the documents should be         |
|                                   |   provided as External            |
|                                   |   Resources.                      |
|                                   |                                   |
|                                   |Example:                           |
|                                   | *The questionnaires for the       |
|                                   | Generic MICS were structured      |
|                                   | questionnaires based on the MICS3 |
|                                   | Model Questionnaire with some     |
|                                   | modifications and additions. A    |
|                                   | household questionnaire was       |
|                                   | administered in each household,   |
|                                   | which collected various           |
|                                   | information on household members  |
|                                   | including sex, age, relationship, |
|                                   | and orphanhood status. The        |
|                                   | household questionnaire includes  |
|                                   | household characteristics,        |
|                                   | support to orphaned and           |
|                                   | vulnerable children, education,   |
|                                   | child labour, water and           |
|                                   | sanitation, household use of      |
|                                   | insecticide treated mosquito      |
|                                   | nets, and salt iodization, with   |
|                                   | optional modules for child        |
|                                   | discipline, child disability,     |
|                                   | maternal mortality and security   |
|                                   | of tenure and durability of       |
|                                   | housing.*                         |
|                                   |                                   |
|                                   | *In addition to a household       |
|                                   | questionnaire, questionnaires     |
|                                   | were administered in each         |
|                                   | household for women age 15-49 and |
|                                   | children under age five. For      |
|                                   | children, the questionnaire was   |
|                                   | administered to the mother or     |
|                                   | caretaker of the child.*          |
|                                   |                                   |
|                                   | *The women's questionnaire        |
|                                   | include women's characteristics,  |
|                                   | child mortality, tetanus toxoid,  |
|                                   | maternal and newborn health,      |
|                                   | marriage, polygyny, female        |
|                                   | genital cutting, contraception,   |
|                                   | and HIV/AIDS knowledge, with      |
|                                   | optional modules for unmet need,  |
|                                   | domestic violence, and sexual     |
|                                   | behavior.*                        |
|                                   |                                   |
|                                   | *The children's questionnaire     |
|                                   | includes children's               |
|                                   | characteristics, birth            |
|                                   | registration and early learning,  |
|                                   | vitamin A, breastfeeding, care of |
|                                   | illness, malaria, immunization,   |
|                                   | and anthropometry, with an        |
|                                   | optional module for child         |
|                                   | development.*                     |
|                                   |                                   |
|                                   | *The questionnaires were          |
|                                   | developed in English from the     |
|                                   | MICS3 Model Questionnaires, and   |
|                                   | were translated into Mumbo-jumbo. |
|                                   | After an initial review the       |
|                                   | questionnaires were translated    |
|                                   | back into English by an           |
|                                   | independent translator with no    |
|                                   | prior knowledge of the survey.    |
|                                   | The back translation from the     |
|                                   | Mumbo-jumbo version was           |
|                                   | independently reviewed and        |
|                                   | compared to the English original. |
|                                   | Differences in translation were   |
|                                   | reviewed and resolved in          |
|                                   | collaboration with the original   |
|                                   | translators.*                     |
|                                   |                                   |
|                                   | *The English and Mumbo-jumbo      |
|                                   | questionnaires were both piloted  |
|                                   | as part of the survey pretest.*   |
|                                   |                                   |
|                                   | *All questionnaires and modules   |
|                                   | are provided as external          |
|                                   | resources.*                       |
+-----------------------------------+-----------------------------------+
| Data collectors                   |This element is provided in order  |
|                                   |to record information regarding    |
|                                   |the persons and/or agencies that   |
|                                   |took charge of the data            |
|                                   |collection. This element includes  |
|                                   |3 fields: Name, Abbreviation and   |
|                                   |the Affiliation. In most cases,    |
|                                   |we will record here the name of    |
|                                   |the agency, not the name of        |
|                                   |interviewers. Only in the case of  |
|                                   |very small-scale surveys, with a   |
|                                   |very limited number of             |
|                                   |interviewers, the name of person   |
|                                   |will be included as well. The      |
|                                   |field Affiliation is optional and  |
|                                   |not relevant in all cases.         |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  *Abbreviation: CSO*              |
|                                   |                                   |
|                                   |  *Affiliation: Ministry of        |
|                                   |  Planning*                        |
+-----------------------------------+-----------------------------------+
| Supervision                       |This element will provide          |
|                                   |information on the oversight of    |
|                                   |the data collection. The           |
|                                   |following should be considered:    |
|                                   |                                   |
|                                   |-  Were the enumerators organized  |
|                                   |   in teams that included a        |
|                                   |   controller and a supervisor?    |
|                                   |   With how many                   |
|                                   |   controllers/supervisors per     |
|                                   |   interviewer?                    |
|                                   |                                   |
|                                   |-  What were the main roles of     |
|                                   |   the controllers/supervisors?    |
|                                   |                                   |
|                                   |-  Were there visits to the field  |
|                                   |   by upper management? How        |
|                                   |   often?                          |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  *Interviewing was conducted by   |
|                                   |  teams of interviewers. Each      |
|                                   |  interviewing team comprised of   |
|                                   |  3-4 female interviewers, a field |
|                                   |  editor and a supervisor, and a   |
|                                   |  driver. Each team used a 4 wheel |
|                                   |  drive vehicle to travel from     |
|                                   |  cluster to cluster (and where    |
|                                   |  necessary within cluster).*      |
|                                   |                                   |
|                                   |  *The role of the supervisor was  |
|                                   |  to coordinator field data        |
|                                   |  collection activities, including |
|                                   |  management of the field teams,   |
|                                   |  supplies and equipment, finances,|
|                                   |  maps and listings, coordinate    |
|                                   |  with local authorities concerning|
|                                   |  the survey plan and make         |
|                                   |  arrangements for accommodation   |
|                                   |  and travel. Additionally, the    |
|                                   |  field supervisor assigned the    |
|                                   |  work to the interviewers, spot   |
|                                   |  checked work, maintained field   |
|                                   |  control documents, and sent      |
|                                   |  completed questionnaires and     |
|                                   |  progress reports to the central  |
|                                   |  office.*                         |
|                                   |                                   |
|                                   |  *The field editor was responsible|
|                                   |  for reviewing each questionnaire |
|                                   |  at the end of the day, checking  |
|                                   |  for missed questions, skip       |
|                                   |  errors, fields incorrectly       |
|                                   |  completed, and checking for      |
|                                   |  inconsistencies in the data. The |
|                                   |  field editor also observed       |
|                                   |  interviews and conducted review  |
|                                   |  sessions with interviewers.*     |
|                                   |                                   |
|                                   |  *Responsibilities of the         |
|                                   |  supervisors and field editors are|
|                                   |  described in the Instructions for|
|                                   |  Supervisors and Field Editors,   |
|                                   |  together with the different field|
|                                   |  controls that were in place to   |
|                                   |  control the quality of the       |
|                                   |  fieldwork.*                      |
|                                   |                                   |
|                                   |  *Field visits were also made by a|
|                                   |  team of central staff on a       |
|                                   |  periodic basis during fieldwork. |
|                                   |  The senior staff of GenCenStat   |
|                                   |  also made 3 visits to field teams|
|                                   |  to provide support and to review |
|                                   |  progress.*                       |
+-----------------------------------+-----------------------------------+
| **Data Processing**               |                                   |
+-----------------------------------+-----------------------------------+
| Data editing                      |The data editing should contain    |
|                                   |information on how the data was    |
|                                   |treated or controlled for in       |
|                                   |terms of consistency and           |
|                                   |coherence. This item does not      |
|                                   |concern the data entry phase but   |
|                                   |only the editing of data whether   |
|                                   |manual or automatic.               |
|                                   |                                   |
|                                   |-  Was a hot deck or a cold deck   |
|                                   |   technique used to edit the      |
|                                   |   data?                           |
|                                   |                                   |
|                                   |-  Were corrections made           |
|                                   |   automatically (by program), or  |
|                                   |   by visual control of the        |
|                                   |   questionnaire?                  |
|                                   |                                   |
|                                   |-  What software was used?         |
|                                   |                                   |
|                                   |If materials are available         |
|                                   |(specifications for data editing,  |
|                                   |report on data editing, programs   |
|                                   |used for data editing), they       |
|                                   |should be listed here and          |
|                                   |provided as external resources.    |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  *Data editing took place at a    |
|                                   |  number of stages throughout the  |
|                                   |  processing, including:*          |
|                                   |                                   |
|                                   |  *a) Office editing and coding*   |
|                                   |                                   |
|                                   |  *b) During data entry*           |
|                                   |                                   |
|                                   |  *c) Structure checking and       |
|                                   |  completenes*                     |
|                                   |                                   |
|                                   |  *d) Secondary editing*           |
|                                   |                                   |
|                                   |  *e) Structural checking of SPSS  |
|                                   |  data files*                      |
|                                   |                                   |
|                                   |  *Detailed documentation of the   |
|                                   |  editing of data can be found in  |
|                                   |  the “Data processing guidelines” |
|                                   |  document provided as an external |
|                                   |  resource.*                       |
+-----------------------------------+-----------------------------------+
| Other processing                  |Use this field to provide as much  |
|                                   |information as possible on the     |
|                                   |data entry design. This includes   |
|                                   |such details as:                   |
|                                   |                                   |
|                                   |-  Mode of data entry (manual or   |
|                                   |   by scanning, in the field/in    |
|                                   |   regions/at headquarters)        |
|                                   |                                   |
|                                   |-  Computer architecture (laptop   |
|                                   |   computers in the field,         |
|                                   |   desktop computers, scanners,    |
|                                   |   PDA, other; indicate the        |
|                                   |   number of computers used)       |
|                                   |                                   |
|                                   |-  Software used                   |
|                                   |                                   |
|                                   |-  Use (and rate) of double data   |
|                                   |   entry                           |
|                                   |                                   |
|                                   |-  Average productivity of data    |
|                                   |   entry operators; number of      |
|                                   |   data entry operators involved   |
|                                   |   and their work schedule         |
|                                   |                                   |
|                                   |Information on tabulation and      |
|                                   |analysis can also be provided      |
|                                   |here.                              |
|                                   |                                   |
|                                   |All available materials (data      |
|                                   |entry/tabulation/analysis          |
|                                   |programs; reports on data entry)   |
|                                   |should be listed here and          |
|                                   |provided as external resources.    |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  *Data were processed in clusters,|
|                                   |  with each cluster being processed|
|                                   |  as a complete unit through each  |
|                                   |  stage of data processing. Each   |
|                                   |  cluster goes through the         |
|                                   |  following steps:*                |
|                                   |                                   |
|                                   |1.  *Questionnaire reception*      |
|                                   |                                   |
|                                   |2.  *Office editing and coding*    |
|                                   |                                   |
|                                   |3.  *Data entry*                   |
|                                   |                                   |
|                                   |4.  *Structure and completeness    |
|                                   |    checking*                      |
|                                   |                                   |
|                                   |5.  *Verification entry*           |
|                                   |                                   |
|                                   |6.  *Comparison of verification    |
|                                   |    data*                          |
|                                   |                                   |
|                                   |7.  *Back up of raw data*          |
|                                   |                                   |
|                                   |8.  *Secondary editing*            |
|                                   |                                   |
|                                   |9.  *Edited data back up*          |
|                                   |                                   |
|                                   |*After all clusters are            |
|                                   |processed, all data is             |
|                                   |concatenated together and then     |
|                                   |the following steps are completed  |
|                                   |for all data files:*               |
|                                   |                                   |
|                                   |10.  *Export to SPSS in 4 files    |
|                                   |     (hh - household, hl -         |
|                                   |     household members, wm - women,|
|                                   |     ch - children under 5)*       |
|                                   |                                   |
|                                   |11.  *Recoding of variables needed |
|                                   |     for analysis*                 |
|                                   |                                   |
|                                   |12.  *Adding of sample weights*    |
|                                   |                                   |
|                                   |13.  *Calculation of wealth        |
|                                   |     quintiles and merging into    |
|                                   |     data*                         |
|                                   |                                   |
|                                   |14.  *Structural checking of SPSS  |
|                                   |     files*                        |
|                                   |                                   |
|                                   |15.  *Data quality tabulations*    |
|                                   |                                   |
|                                   |16.  *Production of analysis       |
|                                   |     tabulations*                  |
|                                   |                                   |
|                                   |*Details of each of these steps    |
|                                   |can be found in the data           |
|                                   |processing documentation, data     |
|                                   |editing guidelines, data           |
|                                   |processing programs in CSPro and   |
|                                   |SPSS, and tabulation guidelines.*  |
|                                   |                                   |
|                                   |*Data entry was conducted by 12    |
|                                   |data entry operators in tow        |
|                                   |shifts, supervised by 2 data       |
|                                   |entry supervisors, using a total   |
|                                   |of 7 computers (6 data entry       |
|                                   |computers plus one supervisors’    |
|                                   |computer). All data entry was      |
|                                   |conducted at the GenCenStat head   |
|                                   |office using manual data entry.    |
|                                   |For data entry, CSPro version      |
|                                   |2.6.007 was used with a highly     |
|                                   |structured data entry program,     |
|                                   |using system controlled approach   |
|                                   |that controlled entry of each      |
|                                   |variable. All range checks and     |
|                                   |skips were controlled by the       |
|                                   |program and operators could not    |
|                                   |override these. A limited set of   |
|                                   |consistency checks were also       |
|                                   |included in the data entry         |
|                                   |program. In addition, the          |
|                                   |calculation of anthropometric      |
|                                   |Z-scores was also included in the  |
|                                   |data entry programs for use        |
|                                   |during analysis. Open-ended        |
|                                   |responses ("Other" answers) were   |
|                                   |not entered or coded, except in    |
|                                   |rare circumstances where the       |
|                                   |response matched an existing code  |
|                                   |in the questionnaire.*             |
|                                   |                                   |
|                                   |*Structure and completeness        |
|                                   |checking ensured that all          |
|                                   |questionnaires for the cluster     |
|                                   |had been entered, were             |
|                                   |structurally sound, and that       |
|                                   |women's and children's             |
|                                   |questionnaires existed for each    |
|                                   |eligible woman and child.*         |
|                                   |                                   |
|                                   |*100% verification of all          |
|                                   |variables was performed using      |
|                                   |independent verification, i.e.     |
|                                   |double entry of data, with         |
|                                   |separate comparison of data        |
|                                   |followed by modification of one    |
|                                   |or both datasets to correct        |
|                                   |keying errors by original          |
|                                   |operators who first keyed the      |
|                                   |files.*                            |
|                                   |                                   |
|                                   |*After completion of all           |
|                                   |processing in CSPro, all           |
|                                   |individual cluster files were      |
|                                   |backed up before concatenating     |
|                                   |data together using the CSPro      |
|                                   |file concatenate utility.*         |
|                                   |                                   |
|                                   |*For tabulation and analysis SPSS  |
|                                   |versions 10.0 and 14.0 were used.  |
|                                   |Version 10.0 was originally used   |
|                                   |for all tabulation programs,       |
|                                   |except for child mortality. Later  |
|                                   |version 14.0 was used for child    |
|                                   |mortality, data quality            |
|                                   |tabulations and other analysis     |
|                                   |activities.*                       |
|                                   |                                   |
|                                   |*After transferring all files to   |
|                                   |SPSS, certain variables were       |
|                                   |recoded for use as background      |
|                                   |characteristics in the tabulation  |
|                                   |of the data, including grouping    |
|                                   |age, education, geographic areas   |
|                                   |as needed for analysis. In the     |
|                                   |process of recoding ages and       |
|                                   |dates some random imputation of    |
|                                   |dates (within calculated           |
|                                   |constraints) was performed to      |
|                                   |handle missing or "don't know"     |
|                                   |ages or dates. Additionally, a     |
|                                   |wealth (asset) index of household  |
|                                   |members was calculated using       |
|                                   |principal components analysis,     |
|                                   |based on household assets, and     |
|                                   |both the score and quintiles were  |
|                                   |included in the datasets for use   |
|                                   |in tabulations.*                   |
+-----------------------------------+-----------------------------------+
| **Data Appraisal**                                                    |
+-----------------------------------+-----------------------------------+
| Estimate of sampling error        |For sampling surveys, it is good   |
|                                   |practice to calculate and publish  |
|                                   |sampling error. This field is      |
|                                   |used to provide information on     |
|                                   |these calculations. This           |
|                                   |includes:                          |
|                                   |                                   |
|                                   |-  A list of ratios/indicators     |
|                                   |   for which sampling errors were  |
|                                   |   computed.                       |
|                                   |                                   |
|                                   |-  Details regarding the software  |
|                                   |   used for computing the          |
|                                   |   sampling error, and reference   |
|                                   |   to the programs used (to be     |
|                                   |   provided as external            |
|                                   |   resources) as the program used  |
|                                   |   to perform the calculations.    |
|                                   |                                   |
|                                   |-  Reference to the reports or     |
|                                   |   other document where the        |
|                                   |   results can be found (to be     |
|                                   |   provided as external            |
|                                   |   resources).                     |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  *Estimates from a sample survey  |
|                                   |  are affected by two types of     |
|                                   |  errors: 1) non-sampling errors   |
|                                   |  and 2) sampling errors.          |
|                                   |  Non-sampling errors are the      |
|                                   |  results of mistakes made in the  |
|                                   |  implementation of data collection|
|                                   |  and data processing. Numerous    |
|                                   |  efforts were made during         |
|                                   |  implementation of the 2005-2006  |
|                                   |  MICS to minimize this type of    |
|                                   |  error, however, non-sampling     |
|                                   |  errors are impossible to avoid   |
|                                   |  and difficult to evaluate        |
|                                   |  statistically.*                  |
|                                   |                                   |
|                                   |  *If the sample of respondents had|
|                                   |  been a simple random sample, it  |
|                                   |  would have been possible to use  |
|                                   |  straightforward formulae for     |
|                                   |  calculating sampling errors.     |
|                                   |  However, the 2005-2006 MICS      |
|                                   |  sample is the result of a        |
|                                   |  multi-stage stratified design,   |
|                                   |  and consequently needs to use    |
|                                   |  more complex formulae. The SPSS  |
|                                   |  complex samples module has been  |
|                                   |  used to calculate sampling errors|
|                                   |  for the 2005-2006 MICS. This     |
|                                   |  module uses the Taylor           |
|                                   |  linearization method of variance |
|                                   |  estimation for survey estimates  |
|                                   |  that are means or proportions.   |
|                                   |  This method is documented in the |
|                                   |  SPSS file CSDescriptives.pdf     |
|                                   |  found under the Help, Algorithms |
|                                   |  options in SPSS.*                |
|                                   |                                   |
|                                   |  *Sampling errors have been       |
|                                   |  calculated for a select set of   |
|                                   |  statistics (all of which are     |
|                                   |  proportions due to the           |
|                                   |  limitations of the Taylor        |
|                                   |  linearization method) for the    |
|                                   |  national sample, urban and rural |
|                                   |  areas, and for each of the five  |
|                                   |  regions. For each statistic, the |
|                                   |  estimate, its standard error, the|
|                                   |  coefficient of variation (or     |
|                                   |  relative error -- the ratio      |
|                                   |  between the standard error and   |
|                                   |  the estimate), the design effect,|
|                                   |  and the square root design effect|
|                                   |  (DEFT -- the ratio between the   |
|                                   |  standard error using the given   |
|                                   |  sample design and the standard   |
|                                   |  error that would result if a     |
|                                   |  simple random sample had been    |
|                                   |  used), as well as the 95 percent |
|                                   |  confidence intervals (+/-2       |
|                                   |  standard errors).*               |
|                                   |                                   |
|                                   |  *Details of the sampling errors  |
|                                   |  are presented in the sampling    |
|                                   |  errors appendix to the report and|
|                                   |  in the sampling errors table     |
|                                   |  presented in the external        |
|                                   |  resources.*                      |
+-----------------------------------+-----------------------------------+
| Other forms data appraisal        |This section can be used to        |
|                                   |report any other action taken to   |
|                                   |assess the reliability of the      |
|                                   |data, or any observations          |
|                                   |regarding data quality. This item  |
|                                   |can include:                       |
|                                   |                                   |
|                                   |-  For a population census,        |
|                                   |   information on the post         |
|                                   |   enumeration survey (a report    |
|                                   |   should be provided in external  |
|                                   |   resources and mentioned here).  |
|                                   |                                   |
|                                   |-  For any survey/census, a        |
|                                   |   comparison with data from       |
|                                   |   another source.                 |
|                                   |                                   |
|                                   |-  Etc.                            |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  *A series of data quality tables |
|                                   |  and graphs are available to      |
|                                   |  review the quality of the data   |
|                                   |  and include the following:*      |
|                                   |                                   |
|                                   |-  *Age distribution of the        |
|                                   |   household population*           |
|                                   |                                   |
|                                   |-  *Age distribution of eligible   |
|                                   |   women and interviewed women*    |
|                                   |                                   |
|                                   |-  *Age distribution of eligible   |
|                                   |   children and children for whom  |
|                                   |   the mother or caretaker was     |
|                                   |   interviewed*                    |
|                                   |                                   |
|                                   |-  *Age distribution of children   |
|                                   |   under age 5 by 3 month groups*  |
|                                   |                                   |
|                                   |-  *Age and period ratios at       |
|                                   |   boundaries of eligibility*      |
|                                   |                                   |
|                                   |-  *Percent of observations with   |
|                                   |   missing information on          |
|                                   |   selected variables*             |
|                                   |                                   |
|                                   |-  *Presence of mother in the      |
|                                   |   household and person            |
|                                   |   interviewed for the under 5     |
|                                   |   questionnaire*                  |
|                                   |                                   |
|                                   |-  *School attendance by single    |
|                                   |   year age*                       |
|                                   |                                   |
|                                   |-  *Sex ratio at birth among       |
|                                   |   children ever born, surviving   |
|                                   |   and dead by age of respondent*  |
|                                   |                                   |
|                                   |-  *Distribution of women by time  |
|                                   |   since last birth*               |
|                                   |                                   |
|                                   |-  *Scatter plot of weight by      |
|                                   |   height, weight by age and       |
|                                   |   height by age*                  |
|                                   |                                   |
|                                   |-  *Graph of male and female       |
|                                   |   population by single years of   |
|                                   |   age*                            |
|                                   |                                   |
|                                   |-  *Population pyramid*            |
|                                   |                                   |
|                                   |*The results of each of these      |
|                                   |data quality tables are shown in   |
|                                   |the appendix of the final report   |
|                                   |and are also given in the          |
|                                   |external resources section.*       |
|                                   |                                   |
|                                   |*The general rule for              |
|                                   |presentation of missing data in    |
|                                   |the final report tabulations is    |
|                                   |that a column is presented for     |
|                                   |missing data if the percentage of  |
|                                   |cases with missing data is 1% or   |
|                                   |more. Cases with missing data on   |
|                                   |the background characteristics     |
|                                   |(e.g. education) are included in   |
|                                   |the tables, but the missing data   |
|                                   |rows are suppressed and noted at   |
|                                   |the bottom of the tables in the    |
|                                   |report (not in the SPSS output,    |
|                                   |however).*                         |
+-----------------------------------+-----------------------------------+
| **Data Access**                                                       |
+-----------------------------------+-----------------------------------+
| Access authority                  |This section is composed of        |
|                                   |various sections:                  |
|                                   |Name-Affiliation-email-URI. This   |
|                                   |information provides the contact   |
|                                   |person or entity to gain           |
|                                   |authority to access the data. It   |
|                                   |is advisable to use a generic      |
|                                   |email contact such as              |
|                                   |data@popstatsoffice.org whenever   |
|                                   |possible to avoid tying access to  |
|                                   |a particular individual whose      |
|                                   |functions may change over time.    |
+-----------------------------------+-----------------------------------+
| Confidentiality                   |If the dataset is not anonymized,  |
|                                   |we may indicate here what          |
|                                   |Affidavit of Confidentiality must  |
|                                   |be signed before the data can be   |
|                                   |accessed. Another option is to     |
|                                   |include this information in the    |
|                                   |next element (Access conditions).  |
|                                   |If there is no confidentiality     |
|                                   |issue, this field can be left      |
|                                   |blank.                             |
|                                   |                                   |
|                                   |An example of statement could be   |
|                                   |the following:                     |
|                                   |                                   |
|                                   |*Confidentiality of respondents    |
|                                   |is guaranteed by Articles N to NN  |
|                                   |of the National Statistics Act of  |
|                                   |[date].*                           |
|                                   |                                   |
|                                   |*Before being granted access to    |
|                                   |the dataset, all users have to     |
|                                   |formally agree:*                   |
|                                   |                                   |
|                                   |1.  *To make no copies of any      |
|                                   |    files or portions of files to  |
|                                   |    which s/he is granted access   |
|                                   |    except those authorized by the |
|                                   |    data depositor.*               |
|                                   |                                   |
|                                   |2.  *Not to use any technique in   |
|                                   |    an attempt to learn the        |
|                                   |    identity of any person,        |
|                                   |    establishment, or sampling     |
|                                   |    unit not identified on public  |
|                                   |    use data files.*               |
|                                   |                                   |
|                                   |3.  *To hold in strictest          |
|                                   |    confidence the identification  |
|                                   |    of any establishment or        |
|                                   |    individual that may be         |
|                                   |    inadvertently revealed in any  |
|                                   |    documents or discussion, or    |
|                                   |    analysis. Such inadvertent     |
|                                   |    identification revealed in     |
|                                   |    her/his analysis will be       |
|                                   |    immediately brought to the     |
|                                   |    attention of the data          |
|                                   |    depositor.*                    |
|                                   |                                   |
|                                   |*This statement does not replace   |
|                                   |a more comprehensive data          |
|                                   |agreement(see Access condition).*  |
+-----------------------------------+-----------------------------------+
| Access conditions                 |Each dataset should have an        |
|                                   |“Access policy” attached to it.    |
|                                   |The IHSN recommends three levels   |
|                                   |of accessibility:                  |
|                                   |                                   |
|                                   |-  Public use files, accessible    |
|                                   |   to all                          |
|                                   |                                   |
|                                   |-  Licensed datasets, accessible   |
|                                   |   under conditions                |
|                                   |                                   |
|                                   |-  Datasets only accessible in a   |
|                                   |   data enclave, for the most      |
|                                   |   sensitive and confidential      |
|                                   |   data.                           |
|                                   |                                   |
|                                   |The IHSN has formulated standard,  |
|                                   |generic policies and access forms  |
|                                   |for each one of these three        |
|                                   |levels (which each country can     |
|                                   |customize to its specific needs).  |
|                                   |One of the three policies may be   |
|                                   |copy/pasted in this field once it  |
|                                   |has been edited as needed and      |
|                                   |approved by the appropriate        |
|                                   |authority. Before you fill this    |
|                                   |field, a decision has to be made   |
|                                   |by the management of the data      |
|                                   |depositor agency. Avoid writing a  |
|                                   |specific statement for each        |
|                                   |dataset.                           |
|                                   |                                   |
|                                   |If the access policy is subject    |
|                                   |to regular changes, you should     |
|                                   |enter here a URL where the user    |
|                                   |will find detailed information on  |
|                                   |access policy which applies to     |
|                                   |this specific dataset. If the      |
|                                   |datasets are sold, pricing         |
|                                   |information should also be         |
|                                   |provided on a website instead of   |
|                                   |being entered here.                |
|                                   |                                   |
|                                   |If the access policy is not        |
|                                   |subject to regular changes, you    |
|                                   |may enter more detailed            |
|                                   |information here. For a public     |
|                                   |use file for example, you could    |
|                                   |enter information like:            |
|                                   |                                   |
|                                   |*The dataset has been anonymized   |
|                                   |and is available as a Public Use   |
|                                   |Dataset. It is accessible to all   |
|                                   |for statistical and research       |
|                                   |purposes only, under the           |
|                                   |following terms and conditions:*   |
|                                   |                                   |
|                                   |1.  *The data and other materials  |
|                                   |    will not be redistributed or   |
|                                   |    sold to other individuals,     |
|                                   |    institutions, or organizations |
|                                   |    without the written agreement  |
|                                   |    of the [National Data          |
|                                   |    Archive].*                     |
|                                   |                                   |
|                                   |2.  *The data will be used for     |
|                                   |    statistical and scientific     |
|                                   |    research purposes only. They   |
|                                   |    will be used solely for        |
|                                   |    reporting of aggregated        |
|                                   |    information, and not for       |
|                                   |    investigation of specific      |
|                                   |    individuals or organizations.* |
|                                   |                                   |
|                                   |3.  *No attempt will be made to    |
|                                   |    re-identify respondents, and   |
|                                   |    no use will be made of the     |
|                                   |    identity of any person or      |
|                                   |    establishment discovered       |
|                                   |    inadvertently. Any such        |
|                                   |    discovery would immediately be |
|                                   |    reported to the [National Data |
|                                   |    Archive].*                     |
|                                   |                                   |
|                                   |4.  *No attempt will be made to    |
|                                   |    produce links among datasets   |
|                                   |    provided by the [National Data |
|                                   |    Archive], or among data from   |
|                                   |    the [National Data Archive]    |
|                                   |    and other datasets that could  |
|                                   |    identify individuals or        |
|                                   |    organizations.*                |
|                                   |                                   |
|                                   |5.  *Any books, articles,          |
|                                   |    conference papers, theses,     |
|                                   |    dissertations, reports, or     |
|                                   |    other publications that employ |
|                                   |    data obtained from the         |
|                                   |    [National Data Archive] will   |
|                                   |    cite the source of data in     |
|                                   |    accordance with the Citation   |
|                                   |    Requirement provided with each |
|                                   |    dataset.*                      |
|                                   |                                   |
|                                   |6.  *An electronic copy of all     |
|                                   |    reports and publications based |
|                                   |    on the requested data will be  |
|                                   |    sent to the [National Data     |
|                                   |    Archive].*                     |
|                                   |                                   |
|                                   |7.  *The original collector of the |
|                                   |    data, the [National Data       |
|                                   |    Archive], and the relevant     |
|                                   |    funding agencies bear no       |
|                                   |    responsibility for use of the  |
|                                   |    data or for interpretations or |
|                                   |    inferences based upon such     |
|                                   |    uses.*                         |
+-----------------------------------+-----------------------------------+
| Citation requirements             |Citation requirement is the way    |
|                                   |that the dataset should be         |
|                                   |referenced when cited in any       |
|                                   |publication. Every dataset should  |
|                                   |have a citation requirement. This  |
|                                   |will guarantee that the data       |
|                                   |producer gets proper credit, and   |
|                                   |that analytical results can be     |
|                                   |linked to the proper version of    |
|                                   |the dataset. The Access Policy     |
|                                   |should explicitly mention the      |
|                                   |obligation to comply with the      |
|                                   |citation requirement (in the       |
|                                   |example above, see item 5). The    |
|                                   |citation should include at least   |
|                                   |the primary investigator, the      |
|                                   |name and abbreviation of the       |
|                                   |dataset, the reference year, and   |
|                                   |the version number. Include also   |
|                                   |a website where the data or        |
|                                   |information on the data is made    |
|                                   |available by the official data     |
|                                   |depositor.                         |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  *"National Statistics Office of  |
|                                   |  Popstan, Multiple Indicators     |
|                                   |  Cluster Survey 2000 (MICS 2000), |
|                                   |  Version 1.1 of the public use    |
|                                   |  dataset (April 2001), provided by|
|                                   |  the National Data Archive.       |
|                                   |  www.nda_popstan.org"*            |
+-----------------------------------+-----------------------------------+
| **Disclaimer and Copyright**                                          |
+-----------------------------------+-----------------------------------+
| Disclaimer                        |A disclaimer limits the liability  |
|                                   |that the Statistics Office has     |
|                                   |regarding the use of the data. A   |
|                                   |standard legal statement should    |
|                                   |be used for all datasets from a    |
|                                   |same agency. The IHSN recommends   |
|                                   |the following formulation:         |
|                                   |                                   |
|                                   |*The user of the data              |
|                                   |acknowledges that the original     |
|                                   |collector of the data, the         |
|                                   |authorized distributor of the      |
|                                   |data, and the relevant funding     |
|                                   |agency bear no responsibility for  |
|                                   |use of the data or for             |
|                                   |interpretations or inferences      |
|                                   |based upon such uses.*             |
+-----------------------------------+-----------------------------------+
| Copyright                         |Include here a copyright           |
|                                   |statement on the dataset, such     |
|                                   |as:                                |
|                                   |                                   |
|                                   |*© 2007, Popstan Central           |
|                                   |Statistics Agency*                 |
+-----------------------------------+-----------------------------------+
| **Contacts**                                                          |
+-----------------------------------+-----------------------------------+
| Contact persons                   |Users of the data may need         |
|                                   |further clarification and          |
|                                   |information. This section may      |
|                                   |include the                        |
|                                   |name-affiliation-email-URI of one  |
|                                   |or multiple contact persons.       |
|                                   |Avoid putting the name of          |
|                                   |individuals. The information       |
|                                   |provided here should be valid for  |
|                                   |the long term. It is therefore     |
|                                   |preferable to identify contact     |
|                                   |persons by a title. The same       |
|                                   |applies for the email field.       |
|                                   |Ideally, a “generic” email         |
|                                   |address should be provided. It is  |
|                                   |easy to configure a mail server    |
|                                   |in such a way that all messages    |
|                                   |sent to the generic email address  |
|                                   |would be automatically forwarded   |
|                                   |to some staff members.             |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  *Name: Head, Data Processing     |
|                                   |  Division*                        |
|                                   |                                   |
|                                   |  *Affiliation: National           |
|                                   |  Statistics Office*               |
|                                   |                                   |
|                                   |  *Email: dataproc@cso.org*        |
|                                   |                                   |
|                                   |  *URI: www.cso.org/databank*      |
+-----------------------------------+-----------------------------------+

5.3. Good practices for completing the File Description
-------------------------------------------------------

The File Description is the DDI section that aims to provide a detailed
description of each data file. The IHSN has selected six of the
available DDI elements.

+-----------------------------------+-----------------------------------+
| Contents                          |A data filename usually provides   |
|                                   |little information on its          |
|                                   |content. Provide here a            |
|                                   |description of this content. This  |
|                                   |description should clearly         |
|                                   |distinguish collected variables    |
|                                   |and derived variables. It is also  |
|                                   |useful to indicate the             |
|                                   |availability in the data file of   |
|                                   |some particular variables such as  |
|                                   |the weighting coefficients. If     |
|                                   |the file contains derived          |
|                                   |variables, it is good practice to  |
|                                   |refer to the computer program      |
|                                   |that generated it.                 |
|                                   |                                   |
|                                   |Examples:                          |
|                                   |  - *The file contains data        |
|                                   |    related to section 3A of the   |
|                                   |    household survey questionnaire |
|                                   |    (Education of household        |
|                                   |    members aged 6 to 24 years).   |
|                                   |    It also contains the weighting |
|                                   |    coefficient, and various       |
|                                   |    recoded variables on levels of |
|                                   |    education.*                    |
|                                   |                                   |
|                                   |  - *The file contains derived     |
|                                   |    data on household consumption, |
|                                   |    annualized and aggregated by   |
|                                   |    category of products and       |
|                                   |    services. The file also        |
|                                   |    contains a regional price      |
|                                   |    deflator variable and the      |
|                                   |    household weighting            |
|                                   |    coefficient. The file was      |
|                                   |    generated using a Stata        |
|                                   |    program named                  |
|                                   |    “cons_aggregate.do” available  |
|                                   |    in the external resources.*    |
+-----------------------------------+-----------------------------------+
| Producer                          |Put the name of the agency that    |
|                                   |produced the data file. Most data  |
|                                   |files will have been produced by   |
|                                   |the survey primary investigator.   |
|                                   |In some cases however, auxiliary   |
|                                   |or derived files from other        |
|                                   |producers may be released with a   |
|                                   |data set. This may for example     |
|                                   |include CPI data generated by a    |
|                                   |different agency, or files         |
|                                   |containing derived variables       |
|                                   |generated by a researcher.         |
+-----------------------------------+-----------------------------------+
| Version                           |A data file may undergo various    |
|                                   |changes and modifications. These   |
|                                   |file specific versions can be      |
|                                   |tracked in this element. This      |
|                                   |field will in most cases be left   |
|                                   |empty. It is more important to     |
|                                   |fill the field identifying the     |
|                                   |version of the dataset (see        |
|                                   |above).                            |
+-----------------------------------+-----------------------------------+
| Processing Checks                 |Use this element if needed to      |
|                                   |provide information about the      |
|                                   |types of checks and operations     |
|                                   |that have been performed on the    |
|                                   |data file to make sure that the    |
|                                   |data are as correct as possible,   |
|                                   |e.g. consistency checking,         |
|                                   |wildcode checking, etc. Note that  |
|                                   |the information included here      |
|                                   |should be specific to the data     |
|                                   |file. Information about data       |
|                                   |processing checks that have been   |
|                                   |carried out on the data            |
|                                   |collection (study) as a whole      |
|                                   |should be provided in the "Data    |
|                                   |editing" element at the study      |
|                                   |level.                             |
|                                   |                                   |
|                                   |You may also provide here a        |
|                                   |reference to an external resource  |
|                                   |that contains the specifications   |
|                                   |for the data processing checks     |
|                                   |(that same information may be      |
|                                   |provided also in the “Data         |
|                                   |Editing” filed in the Study        |
|                                   |Description section).              |
+-----------------------------------+-----------------------------------+
| Missing data                      |Missing data can be given certain  |
|                                   |coding. A common convention is to  |
|                                   |iterate the number “9” to fill a   |
|                                   |field. This value needs to be      |
|                                   |defined as missing in the data     |
|                                   |set and can be explained in        |
|                                   |detail in this element.            |
+-----------------------------------+-----------------------------------+
| Notes                             |This field, aiming to provide      |
|                                   |information to the user on items   |
|                                   |not covered elsewhere, will in     |
|                                   |most cases be left empty.          |
+-----------------------------------+-----------------------------------+

5.4. Good practices for completing the Variables Description
------------------------------------------------------------

The Variable Description is the section of the DDI document that
provides detailed information on each variable.

+-----------------------------------+-----------------------------------+
| Variable Names                    |These are the names given to the   |
|                                   |variables. Ideally, the variable   |
|                                   |names should be a maximum of 8     |
|                                   |characters, and use a logical      |
|                                   |naming convention (e.g., section   |
|                                   |(S) and question (Q) numbers to    |
|                                   |name the question). If the         |
|                                   |variable names do not follow       |
|                                   |these principles, DO NOT CHANGE    |
|                                   |THE VARIABLE NAMES IN THE          |
|                                   |TOOLKIT, but make recommendations  |
|                                   |to the data processor for          |
|                                   |consideration for future surveys.  |
+-----------------------------------+-----------------------------------+
| Variable Labels                   |All variables should have a label  |
|                                   |that                               |
|                                   |                                   |
|                                   |-  Provides the item or question   |
|                                   |   number in the original data     |
|                                   |   collection instrument (unless   |
|                                   |   item number serves as the       |
|                                   |   variable name)                  |
|                                   |                                   |
|                                   |-  Provides a clear indication of  |
|                                   |   what the variable contains      |
|                                   |                                   |
|                                   |-  Provides an indication of       |
|                                   |   whether the variable is         |
|                                   |   constructed from other items    |
|                                   |                                   |
|                                   |Recommendations:                   |
|                                   |                                   |
|                                   |-  Do not use ALL CAPS in labels.  |
|                                   |                                   |
|                                   |-  Make sure that different        |
|                                   |   variables have different        |
|                                   |   labels (avoid duplicate         |
|                                   |   labels). The IHSN Toolkit       |
|                                   |   provides a tool to check        |
|                                   |   availability and unicity of     |
|                                   |   variable labels (see Tools >    |
|                                   |   Validate Variable).             |
|                                   |                                   |
|                                   |-  For expenditure or income:      |
|                                   |   indicating the currency and     |
|                                   |   period of reference is crucial  |
|                                   |   (e.g. “Annual per capita real   |
|                                   |   expenditure in local currency”  |
+-----------------------------------+-----------------------------------+
| Width, StartCol, Endcol           |When you import your data files    |
|                                   |from Stata or SPSS, the            |
|                                   |information on StartCol and        |
|                                   |EndCol will be empty. It is        |
|                                   |crucial to add this information,   |
|                                   |in order to allow users to export  |
|                                   |the data to ASCII fixed format.    |
|                                   |To do so, use the “Variables >     |
|                                   |Resequence” command in the         |
|                                   |Toolkit, for each data file.       |
+-----------------------------------+-----------------------------------+
| Categories                        |Variable categories are the lists  |
|                                   |of codes (and their meaning) that  |
|                                   |apply to the variable. The         |
|                                   |Toolkit imports categories and     |
|                                   |their labels from the source data  |
|                                   |files (SPSS, Stata).               |
|                                   |                                   |
|                                   |If necessary, add/edit the codes.  |
|                                   |Use the Documentation > Create     |
|                                   |categories from statistics if the  |
|                                   |source dataset did not include     |
|                                   |value labels (e,g., when imported  |
|                                   |from ASCII). Make sure the         |
|                                   |categories are not hierarchical,   |
|                                   |and do not include codes for       |
|                                   |“Missing”. The codes for Missing   |
|                                   |must be specified in the “Missing  |
|                                   |data” field. If you fail to do     |
|                                   |that, the summary statistics       |
|                                   |(mean, standard deviation, etc)    |
|                                   |will be calculated including the   |
|                                   |missing code, which will be        |
|                                   |considered as a valid value.       |
|                                   |                                   |
|                                   |.. image:: media/image13.png       |
+-----------------------------------+-----------------------------------+
| Data type                         |Four types of variables are        |
|                                   |recognized by the Toolkit:         |
|                                   |                                   |
|                                   |-  *Numeric: Numeric variables     |
|                                   |   are used to store any number,   |
|                                   |   integer or floating point       |
|                                   |   (decimals).*                    |
|                                   |                                   |
|                                   |-  *Fixed string: A fixed string   |
|                                   |   variable has a predefined       |
|                                   |   length (default length is 8     |
|                                   |   but it can range from 1 to 255  |
|                                   |   characters in length) which     |
|                                   |   enables the publisher to        |
|                                   |   handle this data type more      |
|                                   |   efficiently.*                   |
|                                   |                                   |
|                                   |-  *Dynamic string: Dynamic        |
|                                   |   string variables can be used    |
|                                   |   to store open-ended             |
|                                   |   questions.*                     |
|                                   |                                   |
|                                   |-  *Date: date variables stored    |
|                                   |   in ISO format                   |
|                                   |   (YYYY-MM-DD?—should specify)*   |
|                                   |                                   |
|                                   |The data type is usually properly  |
|                                   |identified when the data is        |
|                                   |imported. It is important to       |
|                                   |avoid the use of string variables  |
|                                   |when this is not absolutely        |
|                                   |needed. Such issues must be taken  |
|                                   |care of before the data is         |
|                                   |imported in the Toolkit. See the   |
|                                   |section on “\ `1. Gathering and    |
|                                   |preparing the                      |
|                                   |dataset <#gathering-and-preparing  |
|                                   |-the-data-set>`__\ ”               |
|                                   |above.                             |
+-----------------------------------+-----------------------------------+
| Measure                           |The Microdata Management Toolkit   |
|                                   |will allow you to define the       |
|                                   |measure of a variable as:          |
|                                   |                                   |
|                                   |-  *Nominal*: variable with        |
|                                   |   numeric assignations for        |
|                                   |   responses; the number assigned  |
|                                   |   to each response does not have  |
|                                   |   a meaning by itself.            |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  Variable *sex*: 1 =              |
|                                   |  Male, 2 = Female (the number     |
|                                   |  does not have a meaning by       |
|                                   |  itself; we could as well have    |
|                                   |  assigned Male = 2 and Female =   |
|                                   |  1). When variables are           |
|                                   |  nominal, we can produce          |
|                                   |  frequency tables by code, but    |
|                                   |  calculating mean or standard     |
|                                   |  deviation of the codes would     |
|                                   |  not make sense.                  |
|                                   |                                   |
|                                   |-  *Ordinal*: variable with        |
|                                   |   numeric assignations and in a   |
|                                   |   logical sequence. The absolute  |
|                                   |   size of the number, or the      |
|                                   |   difference between two numbers  |
|                                   |   has no meaning. But the         |
|                                   |   sequence of the number          |
|                                   |   matters.                        |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  An example of an                 |
|                                   |  ordinal variable would be a      |
|                                   |  variable indicating the level    |
|                                   |  of satisfaction of the           |
|                                   |  respondent, for example on a     |
|                                   |  scale of 1 (very unsatisfied)    |
|                                   |  to 5 (very satisfied).           |
|                                   |                                   |
|                                   |-  *Scale*: continuous variables   |
|                                   |   that have inherent and not      |
|                                   |   categorical value. Examples of  |
|                                   |   such variables include the age  |
|                                   |   of the person, the amount of    |
|                                   |   income or expenditure, etc.     |
+-----------------------------------+-----------------------------------+
| Time variable                     |This is a check-box used to tag    |
|                                   |and identify variables used to     |
|                                   |define time.                       |
+-----------------------------------+-----------------------------------+
| Weight variable                   |This is a check box that is used   |
|                                   |to tag the weight variable. It is  |
|                                   |a good practice to include the     |
|                                   |weight variable with each data     |
|                                   |file that is being archived. If    |
|                                   |it is included, the check box      |
|                                   |should be ticked.                  |
+-----------------------------------+-----------------------------------+
| Min                               |Allows modifying the minimum       |
|                                   |value of a variable. For each      |
| Max                               |variable where it makes sense,     |
|                                   |you should check that the Min and  |
|                                   |Max values are correct. Remember:  |
|                                   |if a specific value is used for    |
|                                   |“Missing”, this should not be      |
|                                   |included in the Min-Max range.     |
|                                   |For example, if codes 1 and 2 are  |
|                                   |used for Male and Female, and 9    |
|                                   |for unknown sex, then the Min      |
|                                   |will be 1 and the Max will be 2.   |
|                                   |The code 9 must be listed in the   |
|                                   |“Missing” codes (see below).       |
+-----------------------------------+-----------------------------------+
| Decimals                          |Defines the number of decimal      |
|                                   |places of a numeric variable       |
|                                   |type.                              |
+-----------------------------------+-----------------------------------+
| Implicit decimals                 |This check box is selected only    |
|                                   |when a fixed ASCII-type file is    |
|                                   |imported and the data file         |
|                                   |includes a decimal character. As   |
|                                   |the decimal character also         |
|                                   |requires a space in the variable   |
|                                   |length assignation, it is          |
|                                   |important to check this box in     |
|                                   |order to assure proper alignment   |
|                                   |of the data.                       |
+-----------------------------------+-----------------------------------+
| Missing data                      |Missing values are those values    |
|                                   |that are blank in a data file but  |
|                                   |should have been responses and     |
|                                   |are within the path or universe    |
|                                   |of the questionnaire. Missing      |
|                                   |values should always be coded.     |
|                                   |Missing values should be           |
|                                   |differentiated from “not           |
|                                   |applicable” and zero (0) values.   |
+-----------------------------------+-----------------------------------+
| Statistics Options                |Various options exist for          |
|                                   |displaying and presenting summary  |
|                                   |information of the variable to     |
|                                   |the user or the person browsing    |
|                                   |the output. Summary statistics     |
|                                   |are saved in the DDI document and  |
|                                   |become part of the metadata. It    |
|                                   |is therefore important to select   |
|                                   |the appropriate ones.              |
|                                   |                                   |
|                                   |-  For nominal variables you want  |
|                                   |   to be sure that the categories  |
|                                   |   are well defined and that some  |
|                                   |   of the summary statistics are   |
|                                   |   not displayed (such as means    |
|                                   |   and standard deviations.        |
|                                   |                                   |
|                                   |-  For ordinal values, you want    |
|                                   |   to be sure that the categories  |
|                                   |   are displayed if they are       |
|                                   |   required. Not all ordinal       |
|                                   |   values will require a           |
|                                   |   category. In some cases you     |
|                                   |   may want to include some        |
|                                   |   summary statistics such as      |
|                                   |   mean and standard deviation.    |
|                                   |                                   |
|                                   |-  For scale values, you do not    |
|                                   |   want to define categories and   |
|                                   |   you may want to include some    |
|                                   |   summary statistics such as      |
|                                   |   mean and standard deviation.    |
|                                   |                                   |
|                                   |Make sure you do not include       |
|                                   |“Frequencies” for variables such   |
|                                   |as the household identification    |
|                                   |number or enumeration area. This   |
|                                   |would produce a useless frequency  |
|                                   |table, that would considerably     |
|                                   |increase the size of your DDI      |
|                                   |file (in general, a very large     |
|                                   |DDI file–8 to 10Mb or more–        |
|                                   |indicates such a problem).         |
|                                   |                                   |
|                                   |Make sure also that you do not     |
|                                   |include meaningless summary        |
|                                   |statistics, such as the mean or    |
|                                   |standard deviation calculated on   |
|                                   |the codes used for variable SEX.   |
|                                   |                                   |
|                                   |Notes:                             |
|                                   |                                   |
|                                   |-  Summary statistics such as the  |
|                                   |   mean or standard deviation are  |
|                                   |   calculated using all valid      |
|                                   |   values. If special codes are    |
|                                   |   used to indicate missing        |
|                                   |   values, make sure they are      |
|                                   |   declared in the “Missing”       |
|                                   |   section. If not, they will be   |
|                                   |   included in the calculations.   |
|                                   |   For example, if you use code    |
|                                   |   99999 for indicating missing    |
|                                   |   values in a variable on         |
|                                   |   household expenditure, code     |
|                                   |   99999 must be listed in the     |
|                                   |   missing section as follows:     |
|                                   |                                   |
|                                   |.. image:: media/image14.png       |
|                                   |                                   |
|                                   |-  If you modify information such  |
|                                   |   as the categories or missing    |
|                                   |   values, you must use the        |
|                                   |   “Documentation > Update         |
|                                   |   Statistics” command in the      |
|                                   |   Toolkit to refresh the summary  |
|                                   |   statistics.                     |
+-----------------------------------+-----------------------------------+
| Weights                           |The appropriate weight should be   |
|                                   |attached to the file and selected  |
|                                   |in this element. The weight        |
|                                   |should be well labelled.           |
+-----------------------------------+-----------------------------------+
| Definition                        |This element provides a space to   |
|                                   |describe the variable in detail.   |
|                                   |Not all variables require          |
|                                   |definition. The following          |
|                                   |variables should always be         |
|                                   |defined when available in a        |
|                                   |questionnaire:                     |
|                                   |                                   |
|                                   |-  Household (attach this          |
|                                   |   definition to the               |
|                                   |   “household ID” variable         |
|                                   |                                   |
|                                   |-  Head of household (attach this  |
|                                   |   definition to the variable      |
|                                   |   “relationship to the head”      |
|                                   |                                   |
|                                   |-  Urban/rural                     |
+-----------------------------------+-----------------------------------+
| Universe                          |The universe at the variable       |
|                                   |level reflects skip patterns       |
|                                   |within-records in a                |
|                                   |questionnaire. This information    |
|                                   |can typically be copy/pasted from  |
|                                   |the survey questionnaire. Try to   |
|                                   |be as specific as possible. This   |
|                                   |information is very useful for     |
|                                   |the analyst.                       |
|                                   |                                   |
|                                   |In many cases, a block of          |
|                                   |variables will have the same       |
|                                   |universe (for example, a block of  |
|                                   |variables on education can all     |
|                                   |relate to the “Population aged 6   |
|                                   |to 24 year). The Toolkit allows    |
|                                   |you to select multiple variables   |
|                                   |and enter the universe             |
|                                   |information to all variables at    |
|                                   |once.                              |
+-----------------------------------+-----------------------------------+
| Source of information             |Enter information regarding who    |
|                                   |provided the information           |
|                                   |contained within the variable. In  |
|                                   |most cases, the source will be     |
|                                   |“Head of household” or “Household  |
|                                   |member”. But it may also be:       |
|                                   |                                   |
|                                   |-  GPS measure (for geographic     |
|                                   |   position)                       |
|                                   |                                   |
|                                   |-  Interviewer’s visual            |
|                                   |   observation (for type of        |
|                                   |   dwelling)                       |
|                                   |                                   |
|                                   |-  Best informant in community     |
|                                   |                                   |
|                                   |-  Etc.                            |
+-----------------------------------+-----------------------------------+
| Concepts                          |Greater description on the nature  |
|                                   |of the variable can be placed in   |
|                                   |this element. For example this     |
|                                   |element can provide a clearer      |
|                                   |definition for certain variables   |
|                                   |(i.e. a variable that provides     |
|                                   |information on whether a person    |
|                                   |is a household member). In the     |
|                                   |case of household membership, a    |
|                                   |conceptual definition can be       |
|                                   |provided.                          |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  *A household member is defined as|
|                                   |  any person who has been resident |
|                                   |  in the household for six months  |
|                                   |  or more in a given year and takes|
|                                   |  meals together OR by default the |
|                                   |  head of household, infants under |
|                                   |  6 months, newly wedded couples   |
|                                   |  etc.*                            |
+-----------------------------------+-----------------------------------+
| Pre-question text                 |The *pre-question texts* are the   |
|                                   |instructions provided to the       |
| Literal question                  |interviewers and **printed in the  |
|                                   |questionnaire before the literal   |
| Post-question text                |question**. This does not apply to |
|                                   |all variables. Do not confuse      |
|                                   |this with instructions provided    |
|                                   |in the interviewer’s manual. With  |
|                                   |this and the next two fields, one  |
|                                   |should be able to understand how   |
|                                   |the question was asked during the  |
|                                   |interview. See example below.      |
|                                   |                                   |
|                                   |The *literal question* is the      |
|                                   |full text of the questionnaire as  |
|                                   |the enumerator is expected to ask  |
|                                   |it when conducting the interview.  |
|                                   |This does not apply to all         |
|                                   |variables (it does not apply to    |
|                                   |derived variables).                |
|                                   |                                   |
|                                   |The *post-question texts* are      |
|                                   |instructions provided to the       |
|                                   |interviewers, **printed in the     |
|                                   |questionnaire after the literal    |
|                                   |question**. Post-question can be   |
|                                   |used to enter information on       |
|                                   |skips provided in the              |
|                                   |questionnaire. This does not       |
|                                   |apply to all variables. Do not     |
|                                   |confuse this with instructions     |
|                                   |provided in the interviewer’s      |
|                                   |manual. With this and the next     |
|                                   |two fields, one should be able to  |
|                                   |understand how the question was    |
|                                   |asked during the interview. See    |
|                                   |example above.                     |
|                                   |                                   |
|                                   |Example:                           |
|                                   |  In the example below             |
|                                   |  (extracted from a UNICEF-MICS    |
|                                   |  standard questionnaire), we find |
|                                   |  a pre-question, a literal        |
|                                   |  question and a post-question.    |
|                                   |                                   |
|                                   |.. image:: media/image15.png       |
|                                   |                                   |
|                                   |-  Pre-question: *Check age. If    |
|                                   |   child is 3 years old or more,   |
|                                   |   ask:*                           |
|                                   |                                   |
|                                   |-  Literal question: *Does (name)  |
|                                   |   attend any organized learning   |
|                                   |   or early childhood education    |
|                                   |   programme, such as private or   |
|                                   |   government facility, including  |
|                                   |   kindergarten or community       |
|                                   |   child care?*                    |
|                                   |                                   |
|                                   |-  Post-question: *If answer is 2  |
|                                   |   or 9 > Goto next module*        |
+-----------------------------------+-----------------------------------+
| Interviewer Instruction           |Copy/paste the instructions        |
|                                   |provided to the interviewers **in  |
|                                   |the interviewer’s manual**. In     |
|                                   |cases where some instructions      |
|                                   |relate to multiple variables,      |
|                                   |repeat the information in all      |
|                                   |variables. The Toolkit allows you  |
|                                   |to select multiple variables and   |
|                                   |enter the information to all       |
|                                   |these variables at once.           |
+-----------------------------------+-----------------------------------+
| Imputation                        |The field is provided to record    |
|                                   |any imputation or replacement      |
|                                   |technique used to correct          |
|                                   |inconsistent or unreasonable       |
|                                   |data. It is recommended that this  |
|                                   |field provide a summary of what    |
|                                   |was done and include a reference   |
|                                   |to a file in the external          |
|                                   |resources section.                 |
+-----------------------------------+-----------------------------------+
| Recoding and derivation           |This element applies to data that  |
|                                   |were obtained by recoding          |
|                                   |collected variables, or by         |
|                                   |calculating new variables that     |
|                                   |were not directly obtained from    |
|                                   |data collection. It is very        |
|                                   |important to properly document     |
|                                   |such variables. Poorly documented  |
|                                   |variables cannot (or should not)   |
|                                   |be used by researchers. In cases   |
|                                   |where the recoding or derivation   |
|                                   |method was very simple, a full     |
|                                   |description can be provided here.  |
|                                   |For example, if variable AGE_GRP   |
|                                   |was obtained by recoding variable  |
|                                   |S1Q3, we could simply mention      |
|                                   |*“Variable obtained by recoding    |
|                                   |the age in years provided in       |
|                                   |variable S1Q3 into age groups for  |
|                                   |years 0-4, 5-9, …, 60-64, 65 and   |
|                                   |over. Code 99 indicates unknown    |
|                                   |age.”*                             |
|                                   |                                   |
|                                   |When the derivation method is      |
|                                   |more complex, provide here a       |
|                                   |reference to a document (and/or    |
|                                   |computer program) to be provided   |
|                                   |as an External Resource. This      |
|                                   |will be the case for example for   |
|                                   |a variable “TOT_EXP” containing    |
|                                   |the household annual total         |
|                                   |expenditure, obtained from a       |
|                                   |household budget survey. In such   |
|                                   |case, the information provided     |
|                                   |here could be:                     |
|                                   |                                   |
|                                   |*“This variable provides the       |
|                                   |annual household expenditure. It   |
|                                   |was obtained by aggregating        |
|                                   |expenditure data on all goods and  |
|                                   |services, available in sections 4  |
|                                   |to 6 of the household              |
|                                   |questionnaire. It contains         |
|                                   |imputed rental values for          |
|                                   |owner-occupied dwellings. The      |
|                                   |values have been deflated by a     |
|                                   |regional price deflator available  |
|                                   |in variable REG_DEF”. All values   |
|                                   |are in local currency. Outliers    |
|                                   |have been fixed. Details on the    |
|                                   |calculations are available in      |
|                                   |Appendix 2 of the Report on Data   |
|                                   |Processing, and in the Stata       |
|                                   |program “aggregates.do” available  |
|                                   |in external resources.”*           |
+-----------------------------------+-----------------------------------+
| Security                          |This field will be left empty in   |
|                                   |most cases. It can be used to      |
|                                   |identify variables that are        |
|                                   |direct identifiers of the          |
|                                   |respondents (or highly             |
|                                   |identifying indirect               |
|                                   |identifiers), and that should not  |
|                                   |be released.                       |
+-----------------------------------+-----------------------------------+
| Notes                             |This element is provided in order  |
|                                   |to record any additional or        |
|                                   |auxiliary information related to   |
|                                   |the specific variable.             |
+-----------------------------------+-----------------------------------+

5.5. Good practices for completing the External Resources description
---------------------------------------------------------------------

The External Resources are all materials related to the study others
than the data files. They include documents (such as the questionnaires,
interviewer’s manuals, reports, etc), programs (data entry, editing,
tabulation, and analysis), maps, photos, and others. To document
external resources, the IHSN Toolkit uses the Dublin Core metadata
standard (which complements the DDI standard).

+-----------------------------------+-----------------------------------+
| Label                             |This is the label that will be     |
|                                   |used to display a hyper link to    |
|                                   |the attached document. It can be   |
|                                   |the title, name, or an             |
|                                   |abbreviated version of the title.  |
+-----------------------------------+-----------------------------------+
| Resource                          |The resource is used to point to   |
|                                   |the file that will be attached     |
|                                   |and distributed. The folder where  |
|                                   |the document is found is a         |
|                                   |relative path and should be the    |
|                                   |folder that will be pasted into    |
|                                   |the document path. Once you        |
|                                   |have pointed to the specified      |
|                                   |resource make sure you check file  |
|                                   |access by clicking the folder      |
|                                   |icon to the right of the entry     |
|                                   |field.                             |
+-----------------------------------+-----------------------------------+
| Type                              |This is crucial information. A     |
|                                   |controlled vocabulary is           |
|                                   |provided. The selection of the     |
|                                   |type is important as it            |
|                                   |determines the way it will be      |
|                                   |presented or displayed to the      |
|                                   |user in the final output. The      |
|                                   |following are the choices:         |
|                                   |                                   |
|                                   |-  Document Administrative: This   |
|                                   |   includes materials such as the  |
|                                   |   survey budget; grant agreement  |
|                                   |   with sponsors; list of staff    |
|                                   |   and interviewers, etc.          |
|                                   |                                   |
|                                   |-  Document Analytical: Documents  |
|                                   |   that present analytical output  |
|                                   |   (academic papers, etc. This     |
|                                   |   does not include the            |
|                                   |   descriptive survey report (see  |
|                                   |   below).                         |
|                                   |                                   |
|                                   |-  Document Questionnaire: the     |
|                                   |   actual questionnaire(s) used    |
|                                   |   in the field.                   |
|                                   |                                   |
|                                   |-  Document Reference: Any         |
|                                   |   reference documents that are    |
|                                   |   not directly related to the     |
|                                   |   specific dataset, but that      |
|                                   |   provide background information  |
|                                   |   regarding methodology, etc.     |
|                                   |   For international standard      |
|                                   |   surveys, this may for example   |
|                                   |   include the generic guidelines  |
|                                   |   provided by the survey          |
|                                   |   sponsor.                        |
|                                   |                                   |
|                                   |-  Document Report: Survey         |
|                                   |   reports, studies and other      |
|                                   |   reports that use the data as    |
|                                   |   the basis for their findings.   |
|                                   |                                   |
|                                   |-  Document Technical:             |
|                                   |   Methodological documents        |
|                                   |   related to survey design,       |
|                                   |   interviewer’s and supervisor’s  |
|                                   |   manuals, editing                |
|                                   |   specifications, data entry      |
|                                   |   operator’s manual, tabulation   |
|                                   |   and analysis plan, etc.         |
|                                   |                                   |
|                                   |-  Document Other: Miscellaneous   |
|                                   |   items                           |
|                                   |                                   |
|                                   |-  Audio: audio type files.        |
|                                   |                                   |
|                                   |-  Map: Any cartographic           |
|                                   |   information.                    |
|                                   |                                   |
|                                   |-  Photo: Photos can provide good  |
|                                   |   documentary evidence of a       |
|                                   |   survey.                         |
|                                   |                                   |
|                                   |-  Program: programs generated     |
|                                   |   during data entry and analysis  |
|                                   |   (data entry, editing,           |
|                                   |   tabulation and analysis).       |
|                                   |   These can be zipped together    |
|                                   |   (include a brief summary        |
|                                   |   report to describe the          |
|                                   |   contents)                       |
|                                   |                                   |
|                                   |-  Table: Tabulations such as      |
|                                   |   confidence intervals that may   |
|                                   |   not be included in a general    |
|                                   |   report.                         |
|                                   |                                   |
|                                   |-  Video: video type files         |
|                                   |   provided as additional visual   |
|                                   |   information                     |
|                                   |                                   |
|                                   |-  Website: Link to related        |
|                                   |   website(s), such as a link to   |
|                                   |   a Redatam server, or to the     |
|                                   |   website of the survey sponsor   |
|                                   |   in the case of international    |
|                                   |   survey programs like the DHS,   |
|                                   |   LSMS, or MICS).                 |
|                                   |                                   |
|                                   |-  Database: any databases         |
|                                   |   related to the survey (e.g., a  |
|                                   |   Devinfo database providing the  |
|                                   |   aggregated results of the       |
|                                   |   survey).                        |
+-----------------------------------+-----------------------------------+
| Title                             |Full title of the document as it   |
|                                   |is provided on the cover page.     |
+-----------------------------------+-----------------------------------+
| Subtitle                          |Subtitle if relevant.              |
+-----------------------------------+-----------------------------------+
| Author(s)                         |Include all authors that are       |
|                                   |listed on the report.              |
+-----------------------------------+-----------------------------------+
| Date                              |Date of the publication of the     |
|                                   |report or resource (at least       |
|                                   |month and year). For reports,      |
|                                   |this is most likely stated on the  |
|                                   |cover page of the document. For    |
|                                   |other types of resources, put      |
|                                   |here the date the resource was     |
|                                   |produced.                          |
+-----------------------------------+-----------------------------------+
| Country                           |The country (or countries) that    |
|                                   |are covered by the associated      |
|                                   |document.                          |
+-----------------------------------+-----------------------------------+
| Language                          |Use the Language element to list   |
|                                   |all languages which appear in a    |
|                                   |resource. The languages should be  |
|                                   |selected from the drop-down list,  |
|                                   |and each language should appear    |
|                                   |on its own line. The proposed      |
|                                   |controlled vocabulary is based on  |
|                                   |ISO 639-3s.                        |
+-----------------------------------+-----------------------------------+
| Format                            |The file format provides           |
|                                   |information on the kind of         |
|                                   |electronic document being          |
|                                   |provided. This includes: PDF,      |
|                                   |Word, Excel etc. This is a         |
|                                   |controlled vocabulary. If the      |
|                                   |controlled vocabulary does not     |
|                                   |provide the format you need, type  |
|                                   |it (or add it in the controlled    |
|                                   |vocabulary using the Toolkit       |
|                                   |Template Editor). Providing        |
|                                   |information on the format will     |
|                                   |inform the user on the software    |
|                                   |needed to open the file.           |
+-----------------------------------+-----------------------------------+
| ID Number                         |If there is a unique ID number     |
|                                   |which references the document      |
|                                   |(such as a Library of Congress     |
|                                   |number or a World Bank             |
|                                   |Publication number) include this   |
|                                   |as the ID Number.                  |
+-----------------------------------+-----------------------------------+
| Contributor(s)                    |Include the names of all           |
|                                   |organizations that have been       |
|                                   |involved or contributed to         |
|                                   |producing the publication. This    |
|                                   |included funding sources as well   |
|                                   |as authoring entities.             |
+-----------------------------------+-----------------------------------+
| Publisher(s)                      |Include the official               |
|                                   |organization(s) accredited with    |
|                                   |disseminating the report.          |
+-----------------------------------+-----------------------------------+
| Rights                            |Some resources are protected by    |
|                                   |copyrights. Use the Rights         |
|                                   |element to provide a clear and     |
|                                   |complete description of the usage  |
|                                   |rights if relevant.                |
+-----------------------------------+-----------------------------------+
| Description                       |A brief description of the         |
|                                   |resource.                          |
+-----------------------------------+-----------------------------------+
| Abstract                          |An abstract of the content of the  |
|                                   |resource.                          |
+-----------------------------------+-----------------------------------+
| Table of Contents                 |Use the Table of Contents element  |
|                                   |to list all sections of a report,  |
|                                   |questionnaire, or other document.  |
|                                   |When copying a table of contents   |
|                                   |from another file into a project,  |
|                                   |pay close attention to the         |
|                                   |formatting as tabs, indents, and   |
|                                   |fonts may not be preserved.        |
|                                   |Because the text cannot be         |
|                                   |formatted, adopting strategies     |
|                                   |such as placing chapter titles in  |
|                                   |capital letters can help keep a    |
|                                   |table of contents organized.       |
|                                   |Including page numbers is not      |
|                                   |crucial.                           |
+-----------------------------------+-----------------------------------+
| Subjects                          |The key topics discussed in the    |
|                                   |resource can be listed in the      |
|                                   |Subjects element. Although the     |
|                                   |IHSN Resource Template does not    |
|                                   |include a controlled vocabulary    |
|                                   |for this element, organizations    |
|                                   |may opt to modify the template     |
|                                   |and establish a set list of        |
|                                   |subjects which all of their        |
|                                   |projects should use when           |
|                                   |documenting studies.               |
+-----------------------------------+-----------------------------------+

.. _section-1:

6. Creating variable groups
===========================

Variable groups are optional, but will help organize the data for the
user into specific subject of use categories. This will be particularly
useful to the user in the case of data files that contain many variables
and are not organized by topic (some flat files contain hundreds or even
thousands of variables).

The Toolkit allows you to group variables found in various separate data
files. For example, education data may be found in various locations and
the disparate variables grouped together. Also, a same variable can
belong to more than one group.

Variable groups are “virtual”. The variables themselves are not moved or
grouped. They remain untouched in the data files.

In the final output of the Toolkit (CD-ROM of website), the variable
groups will appear under a menu item “Data dictionary”. The only reason
for grouping variables is to allow users to easily locate variables
related to their topic of interest. If your dataset contains very few
variables, there is no justification for grouping them.

If you decide to create variable groups (and sub-groups if needed), make
sure that ALL variables in the dataset belong to at least one group.

Variable groups also have their own DDI elements which include Type,
Label, Text, Definition, Universe, and Notes. These elements are
optional and will in most cases be left empty.

+-----------------------------------+-----------------------------------+
| Type                              |This is a controlled vocabulary    |
|                                   |field. It best identifies the      |
|                                   |manner the variables are grouped   |
|                                   |together. This field is optional.  |
+-----------------------------------+-----------------------------------+
| Label                             |The label used to identify the     |
|                                   |group should be clear and relate   |
|                                   |to the type chosen. If these are   |
|                                   |grouped by subject, then the       |
|                                   |subject should be clearly stated   |
|                                   |etc.                               |
+-----------------------------------+-----------------------------------+
| Text                              |Include additional text to         |
|                                   |clarify the reason or purpose for  |
|                                   |grouping the variables. This       |
|                                   |field is optional.                 |
+-----------------------------------+-----------------------------------+
| Definition                        |This optional field is used to     |
|                                   |define the variable group.         |
+-----------------------------------+-----------------------------------+
| Universe                          |This optional field defines the    |
|                                   |universe relevant to the selected  |
|                                   |grouped variables. The variables   |
|                                   |for example can be grouped as      |
|                                   |“Fertility Data” and the universe  |
|                                   |restricted to women between the    |
|                                   |ages of 15-49.                     |
+-----------------------------------+-----------------------------------+
| Notes                             |Additional space for further       |
|                                   |optional explanatory notes.        |
+-----------------------------------+-----------------------------------+

7. Running validations and diagnostics
======================================

The Microdata Management Toolkit includes a useful series of diagnostic
and validation modules (see the drop down menu *Tools*): these range
from very simple validations (such as the *Tools-Validate Metadata*) to
complex visual displays that iterate through each variable and provides
feedback to the archivist at the variable level.

-  *Validate Metadata*: verifies that all mandatory fields are filled
   in.

-  *Validate External Resources*: verifies all mandatory fields in the
   External Resources are filled in.

-  *DDI Diagnostic*: this provides a visual display and issues warnings
   if DDI elements are missing. It also displays information at the file
   level and identifies any variables with missing labels, discrete
   variables with missing value or code label, variables with the same
   name or frequency displays with more than 30 modalities.

-  *DDI Diagnostic Detailed*: this provides a more in-depth display as
   the simpler DDI diagnostic (above). It checks the metadata at the
   individual variable level and checks: labelling, definitions,
   universe, source etc.

-  *Dublin Core diagnostic*: Checks the metadata provided for the
   External Resources.

In addition to these validations, it is recommended that you generate
the DDI document (in the Toolkit, use the Export DDI” command) and
verify the size of the resulting [.xml] file. A fully documented survey
with a large number of variables should not produce a file larger than
10Mb. Very large DDI files often indicate errors in the selection of
summary statistics (for example, frequencies are produced for a variable
like the household ID in a sample household file).

8. Generating the survey documentation in PDF
=============================================

The Microdata Management Toolkit includes a useful tool for producing a
PDF document summarizing all metadata entered in the Toolkit (see *Tools
> Study Documentation PDF*). Generating this report is one of the final
stages of properly preparing a survey for publication and dissemination.
If previous versions exist and changes have been made to the data files
or the metadata make sure you re-run the PDF generator.

This report should be generated, saved and attached as an *External
Resource*.

+--------------------------------------------------------------------+
| **!**                                                              |
|  The PDF report will include a list of all external resources      |
|  related to the study. This list should include this PDF report    |
|  itself. **Before** you generate it, make sure you create one entry|
|  in the External Resources for documenting this report. Immediately|
|  after you generate the PDF report, import it in the Toolkit.      |
+--------------------------------------------------------------------+

One thing to keep in mind is that in a survey with a large number of
variables may produce a document that is very long. If the report is in
excess of 300 or 350 pages, you may want to split this report (e.g.,
produce one report with the study metadata, and one with the files and
variables metadata), or change the content options (e.g., not including
a frequency table for all variables).

9. Producing the final output
=============================

Once you are confident that all necessary checks have been completed,
you may generate the final output using the CD-ROM Builder module of the
IHSN Toolkit. This includes the CD-ROM and survey website.

Before you generate the CD-ROM:

-  Make sure you have a customized “branding” for the CD-ROM. If you
   don’t, design a branding (instructions are provided in the Toolkit
   User’s Guide).

-  Prepare content for the “Home page” of the CD-ROM. Typically, a
   statement by the Director of the data producing agency, or a brief
   summary of the objectives and findings of the survey, will be
   generated.

Generate the CD-ROM with the appropriate options. The IHSN recommends:

-  To generate the CD-ROM without data

-  To export all datasets to ASCII format, and to include the zipped
   ASCII files on the CD-ROM, together with the syntax file to export
   the data to SPSS, Stata and other formats (which shoulod be provided
   as external resources). The ASCII format is more standard than the
   Toolkit Nesstar format, and is a guarantee of long-term viability of
   your data files.

-  To include an autorun file.

-  To include all external resources.

-  To check that the CD-ROM outline does not include any empty pages
   (use the Toolkit utility to check)

-  To name the CD-ROM according to the dataset abbreviation and version.

After you generate the CD-ROM:

-  Check all links before you replicate it, in particular the ones to
   external resources.

-  Test the autorun.

If your agency has a website, you may upload the content of the CD-ROM
directly to the web server. The IHSN recommends the use of a proper
DDI-compliant cataloguing system, such as the one provided by its
National Data Archive (NADA) application. NADA is an open source
package, available free of charge at www.surveynetwork.org.

10. Independent quality review
==============================

An independent review of the data and metadata is highly recommended
prior to publishing the final output. The Appendix provides a blank
review form (the *DDI Reviewer’s Feedback Form*) to be used by an
external reviewer. The IHSN can assist in identifying external
reviewers.

The external review can be based on:

1. The DDI file (xml file, containing no microdata and no external
   resources)

2. The Nesstar file (containing microdata and DDI/DCMI metadata)

3. The CD-ROM (or website), without microdata

4. The CD-ROM (or website), with microdata

The preferred option is the last one, as it allows a full check of the
final output. If data are highly confidential and cannot be shared with
the reviewer, option 3 is the most appropriate.

In order to prepare for the independent quality review, proceed to step
10 if you will use options three or four. Follow the guidance there, and
then finalize the archiving before producing the final output. Else,
send the DDI-XML or the Nesstar file to the reviewer.

The following Form is available at www.surveynetwork.org

.. image:: media/image16.png

.. image:: media/image17.png

.. image:: media/image18.png

.. image:: media/image19.png

.. image:: media/image20.png

.. image:: media/image21.png

.. image:: media/image22.png

.. image:: media/image23.png

.. image:: media/image24.png

.. image:: media/image25.png

.. image:: media/image26.png

.. image:: media/image27.png

.. image:: media/image28.png

.. image:: media/image29.png

.. image:: media/image30.png

.. image:: media/image31.png

.. image:: media/image32.png

.. image:: media/image33.png

.. image:: media/image34.png

.. [1]
   DDI (Data Documentation Initiative) and DCMI (Dublin Core Metadata
   Initiative) are international XML metadata specifications. For more
   information on these standards and on the IHSN Toolkit, please visit
   `www.surveynetwork.org <http://www.surveynetwork.org>`__.

.. [2]
   See section 3 – *Importing data and establishing relationships* for
   more information on key variables.

.. [3]
   In Stata, this can be done through the use of the *group* function
   from the *egen* command. For example, to create a variable hhid based
   on a combination of variables *province*, *district*, *ea* and
   *hhnum*, use the command “egen hhid=group(province district ea hh_num
   )”.
