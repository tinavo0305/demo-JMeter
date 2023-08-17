# demo-JMeter	       <img src="http://home.apache.org/~fschumacher/jmeter.svg" title="Jmeter" alt="Jmeter" width="100" height="40"/>
## Introduction
This project is used to demonstrate my expertise in **REST API Load Performance testing** using **JMeter**

### Description: 
- Use JMeter to do a load test for the web application **Contact List application** to test different APIs to see how it behaves
- Create _Test Plan_ as a container for running tests
- Use _Thread Group_ to create a collection of threads to simulate real users' requests
- Create HTTP request _Samplers_ to send requests to the web server
- Use _Listeners_ to view results of the test execution in different formats: tree, table, or graph
- Use _Configuration Elements_ to set up defaults and variables
- Use _Post-Processors_ to execute actions after making a request
- Use the Command-line interface (CLI) to run the test
- Create an HTML report at the end of the test
 
### Test scenarios:
This project will develop an e2e automated test flow for the Contact List application (https://thinking-tester-contact-list.herokuapp.com/). The test flow contains the following test steps:
1. Create User Account
2. Get User Profile
3. Update User infomation
   
## Steps to configurate test
- Write Test Plan/ Configuring the Test Plan
- Create a Thread Group:
  number of threads (users):
  ramp-up
  loop count
- Create HTTP request Sampler with values for protocol, server name, Http request method and Path
- Add Listeners to view the result of the test: View Results Tree, View Results in Table
- Configuration
- Post Processors
- View result: Request and response
The Sampler result tab contains the response code, response message and information about time, latency, response size in bytes — separately for the headers, the body and the error count.

