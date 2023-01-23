#  CFA-SRE-MONIKA - APP SERVICE

``` STEP 1: ```  Under the MONIKA_SYNTHETICS repository,  we need to create yml file containeing the required configurations specific to the environments e.g monika.prod.yml, monika.qa.yml

```STEP 2:```  Dockerfile should be there with the needful command, and another file present will be azure-pipeline.yml, where the CICD rules will be added to build and deploy the image.

### Dockerfile content are as follows:

```
FROM hyperjump/monika:latest
COPY monika.yml /config
CMD["monika", -c", "config/monika.yml", "prometheus", "80", "-s", "-1"]
```


```STEP 3:``` After the changes under monika.yml done, we need to build the image:

```
docker build -t testing_monika:latest .
```


--------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Local Deployment 
```STEP 4:```  Once the dockerfile is built on local system, we can run it as container and to expose app on 8441 system port:

```
docker run -p 8441:80 testing_monika:latest
```

```STEP 5:```  Now, the app can be accessed on local URL as follows:

```
http://localhost:8441/metrics
```

-------------------------------------------------------------------------------------------------------------------------------------------------------------------


```STEP 6:```  Now, we need to add the reference to Dockerfile under Azure-pipelines.yml file for automatic build and push to the Container Registry as per environment

  It makes the tags as per env name, which can be used for rollback changes

```STEP 7:```  Once we push the code modifications to the repository, it triggers the pipeline automatically under Azure devops for build and deploy stages.

```
NOTE: in case of syntex error, commit will show failed status under Azure devps pipeline.
```

Access to push the deployments via Azure devops is also needed to the existing Azure user

```
NOTE: Since there were permissions issues, the repo was added under CFA project, and code was mograted there, which worked well.

```

<img width="944" alt="image" src="https://user-images.githubusercontent.com/76546821/213982247-68f656ff-e524-4398-9c9e-28840761fd91.png">

