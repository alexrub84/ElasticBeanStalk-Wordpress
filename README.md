# ElasticBeanStalk-Wordpress
ElasticBeanStalk Wordpress

This is a set up of Wordpress using AWS infrastructure . 
We are using Elastic Beanstalk and RDS with MySql engine.

What is Elastic Beanstalk ?
Aws Elastic Beanstalk makes it event esaier for developrers to quickly deploy and manage application in the Aws Cloud . Developers simply upload their application, and Elastic Beanstalk automatically handles the deployment details of capacity provisioning, load balancing, auto-scaling, and application health monitoring.

You can see the architecture :

![Schermata da 2023-01-25 13-43-43](https://user-images.githubusercontent.com/123361990/215750691-7f4151b7-73bd-425b-aaff-1024aa15e296.png)


1. Is necessary to have an Aws Account,after a login is most important that you select a Region 

2. Open a Aws Console , and search Elastic Beanstalk 

2. ![Schermata da 2023-01-31 10-37-34](https://user-images.githubusercontent.com/123361990/215723480-72b9aad8-bd7d-47a0-811f-d4489ef3fe2e.png)
3. Click on Create Application 

4. Follow this inscrutions for realize your application :
   4.1 Name of application : in this example , i have write "wordpress"
   4.2 Tag - Key Owner - Value : myemail 
   4.3 Platform - Php is necessary for install and launch our Wordpress Web site 
   4.4 Platform branch- PHP 8.1 running on 64bit Amazon Linux 2
   4.5 Version 3.5.3 
   4.6 Code of application 
   4.7 Click on Configure more options 
   4.8 Select high availability 
   4.9 Scroll down the page , and click on Modify on Database label . You now add a database SQL RDS that apply on your application 
   4.10 For the first time select a Engine : MySql 
   4.11 Istance Class db.t2.small 
   4.12 Storage 20 GB 
   4.13 User name : admin - copy and remember for config Wordpress 
   4.14 Password : select a password - copy and remember for config Wordpress  
   4.15 Availability  : Multi-AZ
![Schermata da 2023-01-31 10-49-15](https://user-images.githubusercontent.com/123361990/215726229-c3e1b3ec-8eb1-4e8c-9fa9-acf747ab6184.png)

5. When you have finish a configuration , we have our environment ready 
![Schermata da 2023-01-31 10-52-45](https://user-images.githubusercontent.com/123361990/215727578-3bfa30c2-1646-45ad-9d15-d2f72df2bca0.png)

6. Now is necessary to take any information, that are most important , go on your environment click on configuration , scroll down the page and select 
   Endpoint link 
   ![Schermata da 2023-01-31 11-23-51](https://user-images.githubusercontent.com/123361990/215735183-c3d2e69f-e71f-4a52-ae9d-fa3a2f149388.png)

7. Perfet now we see a istance of the our DB , here we can found some information that are necessary for install WordPress 
    - Copy a EndPoint 
    - Click on Configuration 
![Schermata da 2023-01-31 11-29-15](https://user-images.githubusercontent.com/123361990/215736306-e5b94ab4-7d14-47a6-adb2-32ac72967216.png)

8. In configuration page , copy a name of DB is necessary to config Wordpress
   ![Schermata da 2023-01-31 11-35-51](https://user-images.githubusercontent.com/123361990/215737026-86b5359f-1663-4497-a1f6-569cadf0db48.png)

6. Now download Wordpress latest version https://wordpress.org/latest.zip

7. Unzip the file on your PC 
![Schermata da 2023-01-31 11-42-42](https://user-images.githubusercontent.com/123361990/215738696-a45213dd-4758-454d-987b-eecd1a2a40e4.png)

8. Open with your Block notes this file wp-config-sample.php , and save it with new name wp-config.php  
![Schermata da 2023-01-31 11-42-31](https://user-images.githubusercontent.com/123361990/215738550-c552c0e4-c997-47c3-840f-42d321e2b2fd.png)

9. Now is necessary to modify many parametres: 

   // ** Impostazioni database - È possibile ottenere queste informazioni dal proprio fornitore di hosting ** //
   /** Il nome del database di WordPress */
   define( 'DB_NAME', 'name' );

   /** Nome utente del database */
   define( 'DB_USER', 'user' );

   /** Password del database */
   define( 'DB_PASSWORD', 'pwd' );

   /** Hostname del database */
   define( 'DB_HOST', 'host' );

   You remember that have copy in the previous steps this value : dbname (8) ; user (4.13) ; password (4.14) and hostname (7)
   
   Put all this information in a wp-config.php file , and you obtain  : 
   
   // ** Impostazioni database - È possibile ottenere queste informazioni dal proprio fornitore di hosting ** //
   /** Il nome del database di WordPress */
   define( 'DB_NAME', 'ebdb' );

   /** Nome utente del database */
   define( 'DB_USER', 'admin' );

   /** Password del database */
   define( 'DB_PASSWORD', 'write here your password' );

   /** Hostname del database */
   define( 'DB_HOST', 'xxxx-e-xxxxxxx-xxxxx-xxxxxxxxxx-xxxxxxxxxx.xxxxxxxxxx.eu-west-1.rds.amazonaws.com' );
    
10. Save the file and close your block notes

11. Create a new file zip on your PC, most important select all file in your folder
![Schermata da 2023-01-31 11-54-26](https://user-images.githubusercontent.com/123361990/215741224-f2991df4-fbf1-4054-a5c0-a474a67d8633.png)

12. Write a name of your file , for example wordpress.zip and save it on your Desktop . 

13. Come back to your Elasti Beanstalk console , open a Enviroment page 
![Schermata da 2023-01-31 11-58-04](https://user-images.githubusercontent.com/123361990/215742907-341c9ca1-dcbe-4338-96ab-f80dd134e087.png)

14. Click on Load and distribute 
![Schermata da 2023-01-31 12-02-51](https://user-images.githubusercontent.com/123361990/215743023-5b6e8915-72ef-4934-a43a-62a67eec5914.png)

15. Click on Select a file , and put here your zip file that we have saved on our Desktop PC.
    
16. When you have upload a file , click on Distribute.

17. Waiting a correct distribution of our application

18. When is complete , we can open our Environment web page , click on the link 
![Schermata da 2023-01-31 12-14-05](https://user-images.githubusercontent.com/123361990/215745518-3dde1032-1491-449c-b08e-677632adea37.png)

19. Welcome on your Wordpress Web Page configuration  
![Schermata da 2023-01-31 12-20-24](https://user-images.githubusercontent.com/123361990/215746515-e0ae53c7-05a1-4238-abab-8812143f1bb3.png)

20. Put here all information that you have save , complete a installation 
    -Db Name : ebdb ; 
    
    -User: admin ;
    
    -Password: write here your password ;
    
    -Database Host : xxxx-e-xxxxxxx-xxxxx-xxxxxxxxxx-xxxxxxxxxx.xxxxxxxxxx.eu-west-1.rds.amazonaws.com ;
    
    -#Click on Submit 
    
21. Run the Installation 

22. Welcome to the famous five-minuite Wordpress installation process! Scroll down and Hit ‘Install WordPress’. If all went well, then you will get a ‘Success’ notification as shown
![Schermata da 2023-01-31 12-25-08](https://user-images.githubusercontent.com/123361990/215747541-ac52ee23-29ac-48ef-b1e6-500da53729b6.png)

23. Provide your login credentials and click Login In
    ![Schermata da 2023-01-31 12-27-04](https://user-images.githubusercontent.com/123361990/215749674-79083976-02fc-464f-bfe1-a8204edecf8b.png)
    
24. Voila! This is a Wordpress dashboard that you can use to create your first plog or website!
![Schermata da 2023-01-31 12-27-14](https://user-images.githubusercontent.com/123361990/215749973-f1b994de-a834-455b-a3f4-8c41eca9f34d.png)
    
What can we do for complete this application ? 
   Attach Elastic Beanstalk to a Route 53 - work in progress
   Enable SSL on Elastic Beanstalk - work in progress

    




