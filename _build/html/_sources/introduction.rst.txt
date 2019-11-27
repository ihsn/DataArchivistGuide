Introduction
======================

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
============================================

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