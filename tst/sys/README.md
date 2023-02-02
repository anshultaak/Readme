# Ongoing issues 

### Grafana
We can log into Grafana and check the dashboard and panel. Under the panel, we can see if the database connection is stable, and we can also view memory and CPU utilization.
With this URL, you can log in to Grafana.
```
https://grafana.sre.cfainstitute.org/d/VM1M3zi4z/sre-dashboard?orgId=1&refresh=30s
```
<img width="584" alt="image" src="https://user-images.githubusercontent.com/76546821/216253650-9ca3df55-bcaa-4762-a529-6f244df3ce8a.png">

### HealthCheck of application
We can login to the Azure portal using this URL, and inside the transition option you can search the URL and be able to see the application. There you can be able to see the graph and also find errors easily.
```
https://portal.azure.com/#@CFAInstitute.onmicrosoft.com/resource/subscriptions/62d44f85-ab88-4465-9f30-5e95ba77a155/resourceGroups/azprdRGInfrastructure/providers/Microsoft.Insights/components/azprdInfrastructure/overview
```
<img width="583" alt="image" src="https://user-images.githubusercontent.com/76546821/216254302-eeea2c79-971d-41e5-a5af-9ae2f4a1613e.png">

<img width="614" alt="image" src="https://user-images.githubusercontent.com/76546821/216254550-18ee8753-0acd-40d9-bdd6-f898f96b6f84.png">

### we can run the script in the local machine with Docker

