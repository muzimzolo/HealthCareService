# HealthCareService

WSO2 project covering the enterprise integrator to work with a health care service API. This project is from the WSO2 EI tutorials https://docs.wso2.com/display/EI660/Tutorials?src=sidebar
The aim of the project is to show knowledge and skill of WSO2 by completing the labs.   
![Alt text](https://docs.wso2.com/download/attachments/141238723/Screen%20Shot%202017-04-05%20at%202.12.23%20PM.png?version=1&modificationDate=1576209870000&api=v2 "a title")

### Preface
A patient wants to make a doctor reservation for a specific need i.e. surgery I want to make sure the patient making the request on the API finds the right doctor to meet this need. That is the problem that I aim to solve. An API has been created using WSO2 technologies as the solution 

How to run the application:
- Open Eclipse or any given IDE
- Run java -jar Hospital-Service-JDK11-2.0.0.jar to start the service
- Run wso2server.bat to start the server
- Export the package composition application 
- Go to https://localhost:9443/carbon/admin/login.jsp and sign in with default credentials

Once you have completed the above steps you can fiddle with the API and run some GET requests on Postman using the following URLs:
- http://localhost:8280/healthcare/querydoctor/cardiology
- http://localhost:8280/healthcare/querydoctor/surgery
- http://localhost:8280/healthcare/querydoctor/gynaecology
- http://localhost:8280/healthcare/querydoctor/ent
- http://localhost:8280/healthcare/querydoctor/paediatric

## What do the above links/requests do?
The above links find a doctor(s) by their speciality, availability, hospital and fee so if a patient needed a certain specialist it's easy to find
a doctor who specialises for a patient's need
