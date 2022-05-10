# Simple Message To DataSource

In This WSO2 Enterprise Integrator tutorial we're going to send a simple message to a datasource to get a list of doctors. To see the architecture of what we're trying to create/solve open the architecture image file. The list of doctors will be retrieved by:
1. All doctors:
Resource Path /getAllDoctors   
Resource method - GET
2. Doctors by speciality:
Resource path /getDoctors  
Resource Method - GET

We are going to deploy and send a message to ESB to retrieve these doctors. For simplicity, a Postman collection has been uploaded (see Postman collection) to easily upload the requests to Postman once the tutorial is complete. 

## Get Started
- You must have ant installed. See [Installing Apache Ant](https://ant.apache.org/manual/install.html "Installing Apache Ant")
- [[Download Enterprise Integrator from WSO2]](https://wso2.com/enterprise-integrator/6.6.0 "[Download Enterprise Integrator from WSO2]")

- [Download the dataServiceSample.zip file](https://github.com/wso2-docs/WSO2_EI/blob/master/Quick_Start_Guide_Artifacts/dataServiceSample.zip "Download the dataServiceSample.zip file") and extract it to the  on your computer. Export the sample file to a location we will call data-services. i.e. C:\installs\wso2-servers\wso2ei-6.6.0\samples\data-services

This contains a DB script for updating the back-end database with the channeling information of the healthcare service.
- Create a database named DATA_SERV_QSG in the EI_HOME/samples/data-services/database directory for this purpose.
- Open a terminal, navigate to the Dataservice_Home directory and execute the following command: ant -Ddshome=PATH_TO_EI_HOME


------------

- The database is now updated with information on all available doctors in the healthcare service.
### Start the ESB Profile
- On Mac/Linux: sudo wso2ei-6.6.0-integrator
- On Windows: Go to Start Menu -> Programs -> WSO2 -> Enterprise Integrator 6.6.0 Integrator. This will open a terminal and start the ESB profile.


- In your Web browser, navigate to the ESB profile's management console using the following URL:  https://localhost:9443/carbon/.
- Log into the management console using the following credentials:
Username: admin
Password: admin

1. On the Main tab, click Create under Data Service. 

2. In the Create Data Service screen, enter DOCTORS_DataService as the data service name, and click Next.

3. Click Add New Datasource and enter the following details:

DataSourceID: default
Datasource type: Select RDBMS and default
Database Enginge: H2
Driver Class: org.h2.Driver
URL: jdbc:h2:file:./samples/data-services/database/DATA_SERV_QSG
username: wso2ds
password: wso2ds

4. Click Save and then click Next to start defining a query.

5. Now, let's start writing a query to get data from the datasource. 
First, you need to define a query to get the details of all the available doctors from the database.

a. Click Add New Query to open the Add New Query screen.
b. Enter the following values:

Query ID: select_all_DOCTORS_query
Datasource: default
SQL: SELECT NAME, HOSPITAL, SPECIALITY, AVAILABILITY, CHARGE FROM PUBLIC.DOCTORS
c. Click Generate Response to automatically create mappings for the fields.

d. Under the Result (Output Mapping) section, change the values of the following fields.

You're going to do more or less the same with the next query. For the complete list see [WSO2 Sending a simple message to a datasource](https://docs.wso2.com/display/EI660/Sending+a+Simple+Message+to+a+Datasource#f15bcd27a1b64c7686e862428e7ca62d "WSO2 Sending a simple message to a datasource")

The purpose of the above mentioned was to simplify the documentation for any beginner especially with the paths. The rest is simply following through the enterprise integrator console and is intuitive.

Please find Postman Collection to run tests and if you get a 200 status OK then you have followed along correctly.

Your output should look as follows:
Request - http://localhost:8280/services/DOCTORS_DataService/getAllDoctors

Status: 200 OK    

Sample output
   <DOCTOR>  
        <NAME>thomas collins</NAME>  
        <HOSPITAL>grand oak community hospital</HOSPITAL>  
        <SPECIALITY>surgery</SPECIALITY>  
        <AVAILABILITY>9.00 a.m - 11.00 a.m</AVAILABILITY>  
        <CHARGE>7000</CHARGE>  
    </DOCTOR>  
    <DOCTOR>  

You should find a long list of doctors on assumption that you made a request to all doctors











