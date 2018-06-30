# What is Selenium Grid?
The Selenium Grid is a testing tool which allows us to run your tests on different machines against different browsers. 
It is a part of the Selenium Suite used to run multiple tests across different browsers, operating system and machines.

Selenium Grid uses a hub-node concept where you only run the test on a single machine called a hub, 
but the execution will be done by different machines called nodes. You can connect to it with Selenium Remote by specifying the browser, browser version, and operating system you want. 
You specify these values through Selenium Remote’s Capabilities


[Selenium Grid](http://toolsqa.com/selenium-webdriver/selenium-grid/)

## What is a Hub?
In Selenium Grid, the hub is a computer which is the central point where we can load our tests into. 
Hub also acts as a server because of which it acts as a central point to control the network of Test machines. 

The Selenium Grid has only one hub and it is the master of the network. 
When a test with given DesiredCapabilities is given to Hub, the Hub searches for the node witch matches the given configuration. 

For example, you can say that you want to run the test on Windows 10 and on Chrome browser with verision XXX. 
Hub will try to find a machine in the Grid which matches the criterion and will run the test on that Machine. 
If there is no match, then hub returns an error. There should be only one hub in a Grid.

## What is a Node?
In Selenium Grid, a node is referred to a Test Machine which opts to connect with the Hub. 
This test machine will be used by Hub to run tests on. A Grid network can have multiple nodes. 

A node is supposed to have different platforms i.e. different operating system and browsers. 
The node does not need the same platform for running as that of hub.

How it works?
- First you need to create a hub. 
- Then you can connect (or “register”) nodes to that hub. 
- Nodes are where your tests will run, and the hub is responsible for making sure your tests end up on the right one 
(e.g., the machine with the operating system and browser you specified in your test).
