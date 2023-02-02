# What is Synthetic Monitoring?

Synthetic or directed monitoring is a method to monitor your applications by simulating users – directing the path taken through the application. This directed monitoring provides information as to the uptime and performance of your critical business transactions, and most common paths in the application. The simple reality is that there is no easy way to combine the accessibility, coherence, and manageability offered by a centralized system with the sharing, growth, cost, and autonomy advantages of a distributed system. It is here, at this intersection, that businesses turn to IT development and operations teams for guidance—APM tools enable them to negotiate these gaps.



# Objective of this document

This document will help you guide the troubleshooting steps once your receive an alert from Synthetic failures.
NOTE: Please keep in mind that this document is deduced from most common scenarios for troubleshooting and will keep evolving over time. So please use this only a guide.



### Tool being using Synthetics: 
Selenium with Python and Chrome Driver on Ubuntu & Debian



### Alerts on Synthetic failure:

If the failure happens on Synthetic monitoring an alert will be raised via Opsgene:





# Troubleshooting steps

Step1: Please visit the Grafana 'sre-dashboard' to understand the start time and frequency of the errors(marked in RED):

https://grafana.sre.cfainstitute.org/d/VM1M3zi4z/sre-dashboard?orgId=1&refresh=30s



Step 2: Please check if the timing of these errors correlation with any maintenance window or code deployments.

a.  If the errors are triggered during Maintenance window please add the maintenance window in Opsgenie to suppress the alerts or raise a request with SRE team to update the automation to add condition for maintenance.

b. If errors happened due to a code deployment, please follow the instructions to revert the code to the previous stable deployment version - https://grafana.sre.cfainstitute.org/dashboards/f/lRrn8mzVk/release-dashboards

c. If none of the above, please continue troubleshooting to find the root cause

Step 2: Please try to reproduce the errors by manually executing the workflow on your end or by executing the Synthetic scripts locally.

a. If you run the synthetics locally with browser mode on, you will see the 'Object not found' error that will mean that user is unable to process with the happy path (workflow) because of some failure.



Step 3: When we perform the workflow manually and, in case we face some error, we can check the error with developer tools.

  a. You can access the developer tools:

  



  b. Under the Developer Tools settings, you need to select the Network option where you are able to see the actual URL it is failing on.

  





c. You should get at least the initial understanding of the error:

i. “SWW“ - Something went wrong - this error means that one of the downstream dependency is failure and not returning the expected outcomes.

ii. Failures due to vendor application - Details are provided in the following step

ii. Other most common http errors:

4xx client error – the request contains bad syntax or cannot be fulfilled

5xx server error – the server failed to fulfil an apparently valid request



Step 4: CFA applications are heavily dependent on Vendor tools. You can identify the Vendor applications by:
1. Checking the domains e.g. NetSuite, Prometric 

2. 



Please find below details of some vendor and their most common failures:

a. NetSuite - CFA is using NetSuite as Checkout process for most of our applications like CFA program, Membership, CIPM, ESG registration etc. Most common failures:

i. Bundle dates/window mismatch - Netsuite needs to be updated for every new product released by CFA. Products can be CFA program exam, Membership Join/ Renewal. 

ii. NetSuite being down - you can check the Netsuite office availability page of any outages

iii. Order placed successfully on NetSuite but BERT didn't receive the appropriate notifications back.

b. Adyan - CFA is using Adyan as Payment system. 

c. BenchPrep

d. Salesforce Public

e. Nomadic Public

f. Cvent

g. Higher Logic

h. Prometric

STEP 4:  Check the Azure resource utilization for dependent resources via Grafana.
https://grafana.sre.cfainstitute.org/dashboards/f/QjJtqLR4k/monitored-services


STEP 5:  We can login to the Azure portal using this URL, and inside the transition option you can search the URL and be able to see the application. There you can be able to see the graph and also find errors easily.

https://portal.azure.com/#@CFAInstitute.onmicrosoft.com/resource/subscriptions/62d44f85-ab88-4465-9f30-5e95ba77a155/resourceGroups/azprdRGInfrastructure/providers/Microsoft.Insights/components/azprdInfrastructure/overview 







   



Step 6:  For further investigation, we can log in to Grafana and check the dashboard and panel. Under the panel, we can see if the database connection is stable, and we can also view memory and CPU utilization.

  a. With this URL, you can log in to Grafana.

https://grafana.sre.cfainstitute.org/d/VM1M3zi4z/sre-dashboard?orgId=1&refresh=30s

STEP 7:  If we are still getting errors in the application, we have only one way to resolve this issue: we need to check with the developer.
