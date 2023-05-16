
# Create mosquitto  pod with configmap and  secret volume.


# Description 
This project aims to create  mosquitto  pod with configmap volume  which iclude some configuration for this pod  and  secret volume to encrypt some value.
# Steps
1- Create configmap file  mosquitto-configmap.yml which include the folowing attribute :
* log_dest stdout
 * log_type all
 * log_timestamp true
* listener 9001
2- Create secret file mosquitto-secret.yml to encrypt value based on base64.
3- Create mosquitto-deployment.yml  to deploy mosquitto pod which include:

 *  image : eclipse-mosquitto:latest
 * port : 1883
 * Two volumes:
   
    * mosquitto-config
    * mosquitto-secret
# Deployment
-  mosquitto-configmap.yml
```
kubectl apply -f mosquitto-configmap.yml
```
- mosquitto-secret.yml
```
kubectl apply -f mosquitto-secret.yml
```
- mosquitto-deployment.yml
```
kubectl apply -f mosquitto-deployment.yml
```
# Test 
![image](https://user-images.githubusercontent.com/46306526/227744747-2fcd0ad3-b234-464d-a266-d581dba0d1e1.png)

Rum command 
```
kubectl exec -it mosquitto-77dc6c95d9-r4zpt  -- /bin/sh
```
![image](https://user-images.githubusercontent.com/46306526/227744801-e4ed3475-fa07-47bd-ac10-aba6c928e8b6.png)

![image](https://user-images.githubusercontent.com/46306526/227744852-77671930-690e-4458-9431-b3f089daa91b.png)



