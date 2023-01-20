#  CFA-SRE-MONIKA - APP SERVICE

each environment specific yaml file will be created under MONIKA_SYNTHETICS repo, e.g monika.prod.yml, monika.qa.yml

Dockerfile should be there with the needful command, along with azure-pipeline.yml file

we fetch the base image under dockerfile as hyperjump/monika:latest
monika.yml file will be copied under /config directory
after copy, following command will be used under dockerfile:

### Dockerfile content as follows:

```
FROM hyperjump/monika:latest
COPY monika.yml /config
CMD["monika", -c", "config/monika.yml", "prometheus", "80", "-s", "-1"]
```


After the changes under monika.yml done, we need to build the image:

```docker build -t testing_monika:latest .```


--------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Local Deployment 
Once the dockerfile is built on local system, we can run it as container and to expose app on 8441 system port:

```docker run -p 8441:80 testing_monika:latest```

Now, the app can be accessed on local URL as follows:

```http://localhost:8441/metrics```

-------------------------------------------------------------------------------------------------------------------------------------------------------------------


Now, we need to add the reference to Dockerfile under zure-pipelines.yml file for automatic build and pushed to the Container Registry as per environment

It makes the tags as per env, whcih can be used for rollback changes

then pushed the modified code to the repository which triggers the pipeline automatically under Azure devops,

in case of syntex error, commit will show failed status under Azure devps pipeline.

Access to push the deployments via Azure devops is also needed to the existing Azure user

SInce there were permissions issues, the repo was added under CFA project, and code was mograted there, which worked well.
