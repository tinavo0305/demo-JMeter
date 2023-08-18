# demo-JMeter	       <img src="http://home.apache.org/~fschumacher/jmeter.svg" title="Jmeter" alt="Jmeter" width="100" height="40"/>
## Introduction
This project is used to demonstrate my expertise in **REST API Load Performance testing** using **JMeter**

### Description: 
- Use JMeter to do a basic load test for the web application _Contact List application_  to test different APIs to measure the performance of 
- Create _Test Plan_ as a container for running tests. It has Elements:  _Thread Group_, HTTP request _Samplers_ and _Listeners_  
- Use _Configuration Elements_ to set up defaults and variables that will be used in Samplers
- Use _Post-Processors_ to execute actions after making a request
- Use the Command-line interface (CLI) to run the test
- Create an HTML report at the end of the test
- View the result: latency, response size in bytes
 
### Test scenarios:
This project will develop an e2e automated test flow for the Contact List application (https://thinking-tester-contact-list.herokuapp.com/). The test flow contains the following test steps:
1. Create User Account
2. Get User Profile
3. Update User infomation
   
Please visit this link to view detailed test cases 
## Steps to configure test
- Configuring the Test Plan
- Create a Thread Group to create a collection of threads to simulate real users' requests: 
  number of threads (users):
  ramp-up
  loop count
- Create HTTP request Sampler to send requests to the web server with values for protocol, server name, Http request method and Path
- Add Listeners to view the results of the test execution: View Results Tree, View Results in Table
- Configuration
- Post Processors
- View result: Request and response
The Sampler result tab contains the response code, response message and information about time, latency, response size in bytes — separately for the headers, the body and the error count.

