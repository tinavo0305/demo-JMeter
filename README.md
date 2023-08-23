# demo-JMeter	       <img src="http://home.apache.org/~fschumacher/jmeter.svg" title="Jmeter" alt="Jmeter" width="100" height="40"/>
## Introduction
This project is used to demonstrate my expertise in **REST API Load Performance testing** using **JMeter**

### Description: 
- Use JMeter to do a basic load test for the web application _Contact List application_ to measure the performance of different APIs
- Develop _Test Plan_ with elements such as  _Thread Group_, _HTTP request Samplers_ and _Listeners_ to run tests 
- Use built-in JMeter functions to generate dynamic test data 
- Use _Configuration Elements_ to set up defaults and variables that will be used in Samplers
- Use _Post-Processors_ to execute actions after making a request
- Run the test with GUI mode and in Command-line interface (CLI) 
- Create an HTML report at the end of the test
 
### Test scenarios:
This project will develop an e2e automated test flow for the Contact List application (https://thinking-tester-contact-list.herokuapp.com/). The test flow contains the following test steps:
1. Create User Account (POST method)
2. Get User Profile (GET method)
3. Update User infomation (PATCH method)
4. Delete User Account (DELETE method)
   
Please visit this [link](https://docs.google.com/spreadsheets/d/1xl55NZxQLTskoxS18fS9a5EMeseOn6LBBZ7IOi8KmBc/edit?usp=sharing) to view detailed test cases 
## Steps to configure test
1. Create the **_Test Plan_** named `Contact List - User Account`
   
   <img width="954" alt="Jmeter - test plan" src="https://github.com/tinavo0305/demo-JMeter/assets/70987579/552843a1-03a5-4764-81bd-4f916a0edda2">

2. Add  **_Thread Group_** to create a collection of threads to simulate real users' requests: 
  - Number of threads (users): simply input `5` users to simulate a simple test so that we can run the load test in the GUI mode
  - Ramp-up: input `1` to make the small delay between starting users (1 second/ 5 users = 0.2s)
  - Loop count: input `1` to execute the test 1 time

    <img width="754" alt="Jmeter - Thread group" src="https://github.com/tinavo0305/demo-JMeter/assets/70987579/1edef595-b6dc-4f15-8453-a4836dda7d52">

3. Create **_HTTP request Sampler_** to send requests to the web server with values for `Protocol`, `Server name`, `HTTP Request Method` and `Path`
   With requests that require `Body Data` (example: _Create user account_), use built-in JMeter random function to generate dynamic data while creating user
   
    <img width="872" alt="jmeter-sampler" src="https://github.com/tinavo0305/demo-JMeter/assets/70987579/b0d70ed5-227c-420a-9a1a-bc4093463799">

4. Add _Configuration Elements_ > **_HTTP Header Manager_** to add header for the request:
   - Content-Type and application/json
   - Accept and application/json
    <img width="1001" alt="Jmeter - HTTP Header manager" src="https://github.com/tinavo0305/demo-JMeter/assets/70987579/012b8a10-e396-4934-b136-99001e16c34f">

5. Add _Post-Processors_ > **_JSON extractor_** under request to extract the access token in the response that could be used later in subsequent authorization requests
   - Names of created variables: the extracted value will be stored under the variable name `user_token`
   - JSON Path expression: `$.token` (1st level element from View result tree)
   - Match No.(0 of random): there is 1 token in JSON response
   - Default Value: in case `token` is not found, the `user_token` will have the value `TokenNotFound`

   <img width="822" alt="Jmeter - JSON extractor" src="https://github.com/tinavo0305/demo-JMeter/assets/70987579/f0c81239-fb4c-4327-83e1-d77f4bf39ab5">

   
6. Add **_Listeners_** to view the results of the test execution:
    - `View Results Tree` to view Sampler results (contains the response code, response message and information about time, latency, response size in bytes), request, response data
    - `View Results in Table` to view latency, response size in bytes, etc
   
7. Add _Debug Sampler_ to check if the value is stored in variable `user_token`:
   To troubleshoot script variable, we can add Debug Sampler, then run the script, open View Results Tree and view the value of access token is saved in `user_token` variable
   
8. With requests require an access token in the authorization (example: G_et User Profile_). Use **_HTTP Header Manager_** to add `Bearer ${user_token}` as header 
   <img width="1001" alt="Jmeter - Header manager" src="https://github.com/tinavo0305/demo-JMeter/assets/70987579/3c3323f4-514a-449d-a10d-1f63bef1d369">

9.  Add _Post-Processors_ > **_BeanShell preprocessor_**: input this script to pass the `user_token` value in the Authorization Header for next request

     <img width="901" alt="jmeter-beanshell" src="https://github.com/tinavo0305/demo-JMeter/assets/70987579/943c0bc2-844c-4ecd-b2f2-3bad6b005a13">

## Run test with JMeter GUI mode
1. Download JMeter (make sure that Java is already installed in your system)
2. Open the folder `bin`, open  the file `jmeter.bat` (Windows) (or `jmeter.sh` in Mac/Linux) to open the Jmeter GUI mode
3. Download the file [Demo-load-test-with-RESTAPI.jmx](https://github.com/tinavo0305/demo-JMeter/blob/main/Demo-load-test-with-RESTAPI.jmx) can be found in this project
4. In GUI mode, open the file to import a test plan having all requests, and click `run` button to execute the test  
## Run test with CLI and generate reports at the end of the test
1. Download the file [Demo-load-test-with-RESTAPI.jmx](https://github.com/tinavo0305/demo-JMeter/blob/main/Demo-load-test-with-RESTAPI.jmx) can be found in this project
2. Open a command prompt, go to `bin` folder
3. To generate csv report: enter command `jmeter -n -t "location of the test file" -l "location of results file"`

   Example: `jmeter -n -t "templates\Demo-load-test-with-RESTAPI.jmx" -l "report1.csv"`
4. To generate **html** report: enter command `jmeter -n -t "location of the test file" -l "location of results file" -e -o "location of report folder"`
   
   Example: `jmeter -n -t "templates\Demo-load-test-with-RESTAPI.jmx" -l "report1.csv" -e -o "report-html"`
   
 <img width="944" alt="Jmeter - html report" src="https://github.com/tinavo0305/demo-JMeter/assets/70987579/1c9543cb-3a32-456f-8845-a2463b837baf">
