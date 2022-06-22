This module is about Performance testing which is a major non-functional requirement.

**Learning outcomes:**

1. Understand the basic concepts of performance testing
2. Identify the performance testing requirements of an application
3. Plan and execute performance test cycle
4. Script and execute a simple performance test script in Jmeter
5. Understand the practical concepts of continuous performance testing
          
**Duration:**  14 hr          

4.4 Performance testing

4.4.1   Basic Introduction (2 hr)

4.4.1.1 What is performance testing?

Performance test is a type of non-functional test approach that is executed on an application to understand its readiness to handle the expected workload. The workload can be the number of users, amount of data in the database, multiple origins, etc. 
This type of test focuses on the speed, stability, scalability, reliability, and resource consumption of the application (not only the code but also the infrastructure in which the application is hosted) under the required workload. 
    
Every application that is designed for a considerable number of end-users should be tested for performance and the identified performance bottlenecks should be eliminated before releasing to end-users

4.4.1.2 Importance of Performance Testing

>“Best Buy’s Website Suffers Black Friday Outage”
>
>-- <cite>[CNBC.com][1]</cite>

[1]:https://www.cnbc.com/2014/11/28/best-buys-website-down-on-black-friday.html

>"HBO website crashes during 'Game of Thrones Season 7 premiere"
>
>-- <cite>[upi.com][2]</cite>

[2]:https://www.upi.com/Entertainment_News/2017/07/17/HBO-website-crashes-during-Game-of-Thrones-Season-7-premiere/9141500268262/#:~:text=July%2017%20(UPI)%20%2D%2D%20Some,in%20a%20simple%20error%20page.

A user's first impression of the application is determined by its performance. 

For software applications, even some seconds of better/worse performance can affect multiple customer engagements. This expectation is higher for mobile applications. For example:

* Slowing down the Amazon website by 100 ms led to a loss of 1% of revenue
* Google found an extra 500 milliseconds in search page generation time dropped traffic by 20%
* 32% of the users tend to switch apps when the page load time of mobile apps is greater than 5 seconds


Hence, identifying these bottlenecks during the testing phase provides us with time to fix such bottlenecks before the product is released. Without performance testing, the application is likely to have issues as follows:

* Slow response
* Intermittent failures
* System crash and loss of data, etc

    
4.4.1.3 Factors impacting performance in a system/application

* Network

The network is an important factor when a cloud-based application is accessed by multiple users, especially from different regions. Inconsistent bandwidth and increased latency will have significant negative effects on application performance. Most of the high payload applications (e.g. Google) have hosted infrastructure in different regions to reduce the latency.

* Application Design

Designing an application without understanding the performance requirement can lead to a poor responsive application that needs to be re-designed after identifying the bottlenecks. So, understanding an application's performance goals in the early phases is required. 

In addition to this, inefficient algorithms, suboptimal SQL queries, and poorly constructed infrastructure (load balancing, scalability mechanism, backup procedures, etc.) are also major factors that can affect the performance frequently

* Integration and Third-party plugins

Integrated applications can access the system at the Application, Database, and Middleware levels. The slowness of one level (e.g. middleware that carries the API) can result in the slowness of the application layer(UI). For the end-user, this will be a slowness of the complete application. 

When executing a performance test, it needs to be carried out to identify and isolate the bottlenecks at specific layers.

Third-party plugins integrated into the application can also cause delays in response which can lead to a negative effect on the application performance.

4.4.1.4 Before Performance Testing...

As a performance test is a non-functional testing approach, we need to conduct successful manual testing (where the application/component under test satisfies the expected functional result). This eliminates most of the functional errors and allows the tester to focus on the performance testing. 

4.4.1.5 Performance testing vs performance engineering

Performance testing is a testing process executed in a controlled environment for the end-user requirement. It is executed to identify the application behavior under the workload that is expected when used by end-users. 

Performance engineering is a continuous process carried out throughout the software development life cycle to meet the defined performance goals. It includes static approaches like practices, techniques, and activities that are conducted to ensure the expected performance of the application throughout its development phase (not only at the testing phase).

Most companies are progressing through implementing performance engineering as part of the application development as it avoids expensive fixes which require repetitive activities. As performance engineering ensures the application meets the requirement from the start of development, performance testing is conducted on components/applications to confirm the required expectation.

4.4.2   Test types (2.5 hr)

4.4.2.1 Front-end performance test

This test allows understanding the performance of an application from the user's standpoint. There is no access to server monitoring or any other back-end means and the testing focus on how it loads for the end-user. 

Front-end performance tests help us to easily identify client-side bottlenecks very easily. Generally, we notice CSS, Image, File Upload/Download, and external requests which cause front-end performance issues.

This test mainly focuses on the loading time of scripts, stylings, related external references, and the consumption of resources.

When conducting front-end tests, we generally focus on the following types of scenarios:
1. Main functions of the applications
2. Functions that loads more resource or loads repetitively 
    E.g.: Browse through different pages load images and scripts
3. During high traffic, to understand the mechanism in place to engage the end-users

To perform this test, the QA team uses different tools which allow real-time monitoring, comprehensive statistics, and basic performance analysis. Such commonly used tools are:
1. Lighthouse
2. Web page test
3. Pingdom

4.4.2.2 Back-end performance test

This type of testing is conducted to identify bottlenecks in the infrastructure, application code, and database and focus the testing on the server-side. 

When conducting back-end tests, we generally focus on the following scenarios :
1. Average response time, the throughput of APIs
2. Performance efficiency of services, application code
3. Proper configuration of load balancing mechanisms
4. Infrastructure CPU, Memory consumption
5. Network Latency
6. SQL Functions, Stored Procedure efficiency

To conduct Back-end testing, we need a complete understanding of the back-end concepts to identify and analyze the root cause of the test failures. Usage of back-end performance testing tools also requires some level of expertise.

Commonly used back-end performance tools are:
1. Apache Jmeter
2. Loadrunner
3. LoadNinja


Back-end performance testing can be executed for different duration, loads, and objectives. Following are some of the common performance test types. To understand these types of tests better, let's use the following scenario: 

Your company is developing a food-delivery application. The application to satisfy the following user scenarios:

>The application is expected to handle 100 users at any given time. Lunch time is a rush hour and we can expect 300 concurrent users (12:00 p.m. to 02:00 p.m.).
When promotions are released, about 1000 users are expected to access the system to use the promotion
As the application is released to the public, the number of users will increase 
>


* Load Test

This test is carried out to understand the application's ability to carry out the necessary functions at a peak load. 

In the above example, during the rush hour, there is a peak (300) number of users. Hence, this is an ideal scenario for the load test. 
* Users: 300 concurrent users
* Time: 02 hours
* Function: Login > Select Items to order > Add to cart > Checkout and Payment > Logout
* Objective: Identify the application's ability to handle the load

This is a common type of test carried out in every projects
* Endurance/Soak Test

This test is carried out to understand the application's processing power to handle the continuous flow of data, and consumption of resources for a longer period. Memory Leak, Faulty garbage collection are potential failures in this test.

In the above example, throughout the day 100 concurrent users are accessing the application. The application's ability to handle this can be tested by an endurance test as follows:
* Users: 100 users
* Time: 10 hours
* Function : Login > Select Items to order > Add to cart > Checkout and Payment > Logout
* Objective: Identify the memory (especially) and other resource consumptions when using the app for a long time

Server is extensively monitored in this test

* Stress Test

The main objective of this test is to identify the system's breaking point. Identifying your application's limit, allow you to establish parameters, and implement alerts and backup procedures before reaching any stress failures. 

In the above scenario, a stress test can be carried out to understand the number of users who can successfully access the system
* Users: Increase gradually
* Time: Until breakpoint
* Objectives: Identify the breaking point of the system

Once breaking point is identified, the crash is discussed and proper back up mecahnisms are implemented

* Spike Test

In this test, we send a sudden increase of load to an application. This is carried out to understand the behavior and recovery mechanisms implemented in the application to handle the variations. 

In the above example, there is a spike in load expected when a promotion is released. This can be tested using a spike test
Users: 1000 users
Time: 20 minutes
Function : Login > Access the promotion > Checkout and Pay > Logout
Objective: Identify how the system recovers from the test (Automatic/manual recovery, Auto activating backup systems, etc.)


>We don't need to execute all these tests on all applications. Depending on the necessity, and requirement we need to choose the suitable types of tests.

>Most of the back-end performance testing tools, allow us to configure the number of users, period, and selection of functions to achieve the above test types.
  
4.4.2   Performance test life cycle (5-6 hr)

This is a set of systematic steps that need to be carried out when conducting a performance test on an application. We use this approach to implement performance practice within the project, get the confirmed performance required by the client, and create visibility to all stakeholders on the performance of the application.
    
1. Analyze the stability of the application

This is the phase, where we check the eligibility of the component released to test. The component should have achieved the accepted test coverage. The selected component should have finalized requirements (Constant changes create bugs!!)

Practically, there is a meeting with relevant stakeholders to understand 
* The application architecture
* Refer project documents
* Refer test metrics
* Setup calls

This allows you to understand the risks in the component, infrastructure (any third-party plugins that need to be avoided), and the application.

2. Identify the Performance test requirement/scenarios

This step involves constant communication with the client to understand the business performance requirement of the application. During this step, we try to get information on the
* Most used functions in the application
* Number of users accessing the application during normal hours, and peak hours. 
* Any workflows/mechanisms that are favored by the end-users
* Any spike that can be expected 
* The end-user location, hosting location of the application (to understand the network)


3. Tool Selection

With the above requirements, we need to evaluate which set of performance tools are we going to use. For back-end performance testing we need 2 sets of tools
3.1 Load Generator Tool
This is the tool that simulates the load. This simulates the behavior of multiple users accessing the system and allows us to 
* Create the required scenarios
* Configure the number of users/period etc
* Simulate the performance test as configured

The tool sends the request to the server, receives the response from the server, and provides a basic analysis of the received metrics. Generally from the load generator tool, we expect the following metrics:
1. Average response time > Average time taken for a request to be sent and received from the server
2. Throughput > No. of requests received from the server within 1 second
3. Success/Failure rate of the execution

3.2 Server Monitoring Tool

During the performance test, we need to monitor the server to understand how the resources are consumed and identify any blockers, leaks, and logs on failed requests (this is used to identify any code failures, and DB timeouts).

We use a server monitoring tool to get:
1. CPU utilization
2. Memory Utilisation
3. Disk I/O
4. Server logs

Depending on the operating system of the OS we can use different tools to get these metrics. Some popular tools are:
1. For Linux > Nmon
2. For Windows > Perfmon
3. For Azure-hosted applications > Azure App Insights
4. Identify the Testing Environment

Performance tests should be carried out in a production identical environment to simulate the real-world scenarios. Practically, this is not always the case. Most of the time, we get a controlled environment with less specification compared to the production environment. 

In this case, the test load should also be adjusted accordingly to relate to the testing environment specification.

6. Plan the Performance test

With all the information gathered, the tester creates a performance test plan. This document is shared with the stakeholders to create the visibility on:

* In scope and Out of the scope of the performance test
* Entry and exit criteria
* Scenarios to be tested, type of test that will be carried out
* Pre-requisites for the scenario (User creation before login). How is this data populated
* Expected Success/ Failure rates of the execution
* Tools to be used
* Test Environment information
* Tasks that will be carried and their timelines
* Deliverables of the test

This document should be shared with the stakeholders and on the confirmation, the rest of the activities are carried out.

7. Performance test script development

Once confirmed, the tester starts creating the scripts for the scenarios using the load generator tool. This will sometimes include any pre-requisite data creation scripts as well. 

When creating performance test scripts, we should consider the following best practices:

* Performance test script and pre-requisite script should be separated
* Test the script to check the dynamic values
* Dynamic values should be parameterized (should not be static values)
* Cookies, sessions, and cache handlers should be implemented correctly


8. Test Execution and Analysis

Before the test execution, we need to make sure that the required pre-requisites are completed :
1. Performance test environment should be ready and the relevant access (to get the metrics, access logs, and monitor performance) should be provided to the tester.
2. Performance test scripts should be tested and available

Once this is confirmed, the performance test is carried out according to the timelines listed in the performance test plan. 
1. We select a type of test that we are going to execute (Load test)
2. Get the configurations, and workflow for the test
3. Configure the load generator tool and script accordingly
4. Execute any pre-cleanse on the testing and server environments (Clear cache, Clear DB threads)
5. Execute the test for a given set of users
	* Note: If our target users for this test are 300, we don't start from 300. This is because it is very difficult to identify any bottlenecks when there are multiple failures. So, we conduct the test by iterations (50,100,150,200,250,300 users)
6. Analyse the test success rate of the test
    * If the test has passed the success rate, move to the next iteration
    * If failed, identify the bottlenecks > report the findings and once the defects are fixed retest on the same iteration

Once the tests are progressed, we create a performance test report which includes the findings, success rate of the test, and any recommendations and publishes it to the stakeholders concluding the performance test of the application. 

An application will go through multiple performance test cycles and should go through one before any major release to the customer. 

**Practical Illustration**
  
4.4.3   Practical Example (Ex: Jmeter)  (3-4 hr)

    Sample web performance test using the tool

4.4.4 More on Performance testing
    
4.4.4.1 Load generation and test distribution options

When executing for a large number of users, we cannot execute the test from one computer. This will cause the client to exhaust, and provide faulty metrics, and may cause the client system to crash as well.

Distributed performance testing is the testing mechanism where the same test is carried out by multiple computers. This helps us to avoid any client failures and create large traffics. 

Many tools like load runner and JMeter have distributed testing options to facilitate this scenario.

4.4.4.2 Performance Testing in Agile Projects and Continuous performance testing

Agile recommends constant changes but performance testing is an important part of agile projects. In this type of project, Performance is focused from initial planning to product delivery. 

With the constant requirement changes, performance tests can be achieved as follows:

1. Performance becomes one of the key aspects in requirement gathering, product planning, and designing
2. Performance test carried out individual components released in sprints
3. Complete performance test on the application before a major release
4. Implement automated performance test on deployment pipelines

This is called Continuous performance testing and is a trending approach on many project teams.

  
4.5 **References/free study materials on Performance testing** 

    https://www.toolsqa.com/software-testing/performance-testing/
    https://www.toolsqa.com/blogs/performance-testing-tools/
    https://www.toolsqa.com/jmeter/introduction-to-jmeter/
    https://www.toolsqa.com/jmeter-tutorial/
  
    Practical assessment of sample performance test development, execution, and result analysis
