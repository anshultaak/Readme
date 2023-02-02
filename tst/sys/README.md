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


### Memory Usage and Database connectivity issue

```Step 1: ``` Check the memory usage in the service. If it shows high usage in the graph, We need to give the server more resources.
<img width="549" alt="image" src="https://user-images.githubusercontent.com/76546821/216268498-62757e94-35be-4120-99f1-43da5bb13bf4.png">

```Step 2: ``` Check that the DataSource is correctly connected to your application and We can check this by going inside the server and trying to connect with the database.

```STEP 3:``` Also, you can check if your website certificate is working fine. In case the website has expired, you need to renew the certificate.

```STEP 4:``` The integration failed due to the data it was required to process.


### we can run the script in the local machine with Docker

To test this URL, we need to create a Dockerfile with the following steps.
```
FROM hyperjump/monika:latest
COPY example.yml /config
CMD["monika", -c", "config/example.yml", "prometheus", "80", "-s", "-1"]

```
We need to create one monika file where we need to define that URL.
```
- id: <UNIQUE_ID>
    name: <SAMPLE_NAME>>
    requests:
      - url: <https://www.SAMPLE_URL.org/>
```

After adding the URL in Example's .yml, we need to build that image.
```
docker build -t testing:latest .
```
 Once the dockerfile is built on local system, we can run it as container and to expose app on 8441 system port:
```
docker run -p 8441:80 testing:latest
```

Now, the app can be accessed on local URL as follows:
```
http://localhost:8441/metrics
```
