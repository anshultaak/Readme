# Steps to Add/Modify Web Boxes

* Create AMI/Image of existing Web Box
 - To create AMI from instance follow the AWS deocumentation: https://docs.aws.amazon.com/toolkit-for-visual-studio/latest/user-guide/tkv-create-ami-from-instance.html
  
     NOTE: check NO boot check box.

* Add web boxes over Load balancer
  1. Remove Web Boxes from Load balancer
  2. Deleting the Web Boxes


# Steps For Production Infra changes:

1) [Creating New Web boxes  ](#Creating-New-Web-boxes  )
2) [Testing Application Locally after Upgradation](#Testing-Application-Locally-after-Upgradation)
3) [Add web boxes over Load Balancer](#Add-web-boxes-over-Load-Balancer)
4) [Removed web boxes over Load Balancer](#Removed-web-boxes-over-Load-Balancer)



### Creating New Web Boxes  

* First we need to create an AMI from running web boxes without rebooting.

<img width="750" alt="image" src="https://user-images.githubusercontent.com/107048406/229530863-1453b76b-340d-45ca-b6f2-0fd64f40b48b.png">

* After that, we need to create new web boxes using the same VPC (vpc-42337826) and under the public subnet group(subnet-c0f23fea). We need to attach the following security group to the web boxes.
``` 
   * sg-02a1b17b (FI-Prod-RabbitMQ Internal)
   * sg-10918869 (Connamara Office SSH)
   * sg-6ff70214 (FI Prod RDS/MySQL)
   * sg-8338d9f8 (FI Prod Outbound)
   * sg-f9bbab80 (FI-Prod-HTTP)
```

* We need to add the public IP of the new web boxes to the security group(sg-692dec0f) of the RDS MySQL database(cme-institute-production).

### Testing Application Locally after Upgradation

* We need to SSH into the new web boxes and check the application logs.
```
ssh cme@xx.xx.xx.xx
```

* We can also add the new IPs of the web boxes under the "/etc/hosts" of our local machine 
```
XX.XX.XX.XX institute.cmegroup.com

```

* Access the application by using the URL "institute.cmegroup.com" to verify the UI

### Add web boxes over Load Balancer

* Once you verify that everything is working fine in the new web boxes, we have to modify the load balancer and need to add the new boxes under the load balancer(FI-Prod-HTTP). 
<img width="803" alt="image" src="https://user-images.githubusercontent.com/107048406/229518942-8b62977f-fdb5-435f-afde-be251c145b59.png">


### Removed web boxes over Load Balancer
* Remove Web Boxes from Load balancer
* Deleting the Web boxes
