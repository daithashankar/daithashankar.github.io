# API Testing Using Jmeter - Data Driven Framework

We use jmeter for performance testing, Why can not we use for API Testing. Here we go...

### Pre requisites


## Getting Started

Download complete code in to your system. mention the jmx file name to execute in the config.property file under config folder.
execute the build.xml from the extras folder, Structure of framework looks like below.


### Structure of framework

<pre>

com
|
pro
|
|----------- Config
|
|----------- Jtlfiles
|
|----------- logs
|
|------------results
|             ||------------ Oldresults
|
|----------- stylesheet
|
|-----------  testsuite
|
</pre>

### Description

<b> Config :</b>Under this folder we will maintain configuration file where we will give environment details, File name to execute, 
style sheet names,
etc.

<b> Jtlfiles :</b> Initially after executioin jtl file will move to this folder.

<b> logs :</b> Initially after executioin log file will transfer to this folder.

<b> Results : -->Oldfiles : </b> After executioin of the scripts all log, jtl , html reports will be moved to oldresults folders with timestamp

<b> stylesheet :</b> Stylesheet can be placed in this current folder.

<b> testsuite :</b> Test scripts will be placed in the current folder.

Data files (Excel file) will be placed in Jmeter bin folder.

## Read valus from excel

* Create a excel(.xlsx) file under bin folder.
* Give filename in script under "user defined variable"
* Use the following command to read the data from excel (beanshell sampler)

Syntax :

datatable.getCellData(filename,"SheetName","SearchText", row number)

Eg :

vars.put("SearchText1", datatable.getCellData(filename,"Google","SearchText", 2));

it will read the data from excel and store in "SearchText1".



## Running the tests

* Download project in to ur system.
* Copy Your test script in testsuite folder.
* Under "config" folder in "Config.properties" Update filename property with your test script name .
* Create a excel file under bin folder which we want to read data.
* Open command prompt.
* Navigate to extras folder.
* Execute build command "ant -f build.xml all"
* Check the execution and validate results in oldresults folder.



## Execution

In current test we have two scripts searching in "google" and "bing".

Based on the name which is given in property file it will run the script

Generate the reports in results folder.


## Reports

It will generate two report, One contains only number of samples executed information. Second report will provide the detail execution report.



## Emails

Sending email code is availble in build.xml we need to provide smtp details in it.Email will be send with embeeded report in email body.
