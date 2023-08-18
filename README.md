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
1. Select and name the **_Test Plan_** as Contact List-User Account
   <img width="954" alt="image" src="https://github.com/tinavo0305/demo-JMeter/assets/70987579/f2c7a828-dcb8-4135-92f9-9198a6a0e1d7">

2. Add  **_Thread Group_** to create a collection of threads to simulate real users' requests: 
  - Number of threads (users): I simply input 5 users to simulate a simple test so that we can run the load test in the GUI mode
  - Ramp-up: input 1 to make the small delay between starting users (1 second/ 5 users)
  - Loop count: input 1 as I only want to execute the test 1 time
    <img width="754" alt="image" src="https://github.com/tinavo0305/demo-JMeter/assets/70987579/1a623ee9-6b7f-4b14-896f-74c40b0bbf21">

3. Create **_HTTP request Sampler_** to send requests to the web server with values for Protocol, Server name, HTTP Request Method and Path
   Body Data: use built-in JMeter random function to generate dynamic data (email) while creating user
   

6. Configuration Elements > _HTTP Header Manager_ to append the token for subsequent requests
   <img width="1001" alt="image" src="https://github.com/tinavo0305/demo-JMeter/assets/70987579/f1d44932-ff4b-4ac6-87ce-a786cdd320a4">

8. Add _Post-Processors_ > _JSON extractor_ to extract the token (capture any dynamic data from the request)
   <img width="822" alt="image" src="https://github.com/tinavo0305/demo-JMeter/assets/70987579/8111b770-750e-46d8-964c-90b6f6c817a1">

10.  Add _Post-Processors_ > _BeanShell preprocessor_

5. Add _Listeners_ to view the results of the test execution: View Results Tree, View Results in Table, Assertion?

- View result: Request and response
The Sampler result tab contains the response code, response message and information about time, latency, response size in bytes — separately for the headers, the body and the error count.

## Run test with GUI and get result

## Run test with CLI
