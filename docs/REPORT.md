In this project we have three apps:
Account service
It is a standalone process that provides a RESTful server to a repository of accounts that will use the port 2222.
./gradlew accounts:bootRun
![8](https://user-images.githubusercontent.com/75692258/208911774-654e0d11-e8d3-4b6c-b644-f9f66f9e09e6.png)

![1](https://user-images.githubusercontent.com/75692258/208912007-413b4b2d-dd38-46b1-b7f4-0b839b34416d.png)


Web service : 
Is an Eurika client and defines a web server
 ./gradlew web:bootRun
 
 ![5](https://user-images.githubusercontent.com/75692258/208911360-6ae71f80-0e14-438f-9a54-7b1336445beb.png)
 
 ![2](https://user-images.githubusercontent.com/75692258/208912032-1400ae71-5693-47c1-b905-01b24c6d7a28.png)
 
Registration service
Is a service to register the services that are running in the system
./gradlew registration:bootRun
![3](https://user-images.githubusercontent.com/75692258/208911153-4f3dc487-47a0-4a96-8805-0c04a8f58f9a.png)

 we can see the two services registered
![0](https://user-images.githubusercontent.com/75692258/208911932-1892d482-0338-4972-81c9-ddd76398c0c1.png)

Now, I add a new service account in the port 4444
First we need to change the file accounts/src/main/resources/application.yml and change the port
![6](https://user-images.githubusercontent.com/75692258/208912226-7af4e0f9-bb18-407b-bd85-144e667ee9ac.png)

I need to use clean to force recompile the code and copy the changes in resources to classpath 
./gradlew clean account:bootRun
![11](https://user-images.githubusercontent.com/75692258/208912293-82e88a7b-8d4f-4398-ae08-f4e59c04f54f.png)

We can see both account services registered
![13_3](https://user-images.githubusercontent.com/75692258/208912329-fdd3fa65-8224-4df5-8ed8-eb23213633bb.png)


 I proceed to shut down the account (2222) service
 ![13_4](https://user-images.githubusercontent.com/75692258/208912525-738c5d3b-17e8-46f0-a193-0fc85f55ad40.png)

 we can make a request from the web service and still working because the web server searches for the account service in the
 Eureka server (where all the services are registered), and it finds the account service in the port 4444 
 ![13_5](https://user-images.githubusercontent.com/75692258/208912571-63f228b9-af11-4abd-986a-ce5fa5b46472.png)

 
