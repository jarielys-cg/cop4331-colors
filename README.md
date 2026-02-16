# cop4331-colors
## Description
The COLORS web application lets the user search for any available or newly added colors.


## Technologies
- GoDaddy, godaddy.com, to purchase a domain name  

- Digital Ocean, digitalocean.com, to create a LAMP Droplet  

- Computer terminal to connect and add code files to LAMP Droplet  

- Visual Studio Code to create and edit code files   

- AdvancedRestClient, ARC, to test API endpoints   

- Google Chrome to run and test functionality of the finished COLORS web application   


## Instructions
### Step 1 (Digital Ocean & LAMP Droplet)
Create an account on digitalocean.com  

Once logged in, select the **Create** dropdown and select **Droplets**  

Scroll down to **Choose an image** and **select Marketplace**  

Select **LAMP on Ubuntu 24.04**, **Basic Plan**, **Premium Intel**, **$8/mo** payment option  

Create a root password as the **Authentication Method**  

**(Optional)** Create a unique **Hostname** for your droplet  


### Step 2 (GoDaddy & Domain Name)
Create an account on godaddy.com  

Purchase a unique domain name  

On the your profile page, select your newly purchased domain  

Select **Domain**, **DNS** and **DNS Records**  

Locate the row with **Type ‘A’** and **Name ‘@‘** and select **edit**  

Enter the IP address of the LAMP Droplet in the **Value** box  


### Step 3 (Create and Populate MySQL Database)
Open command prompt and run SSH: **ssh root@MyDomainORIPAddress**  

Enter the droplet’s password  

Connect to MySQL: **mysql -u root -p**  

Enter the droplet’s password again  

Create database:  
   &emsp; **create database COP4331;**  
   &emsp; **use COP4331;**  

Create tables:  

    CREATE TABLE `COP4331`.`Users`  
    (  
        `ID` INT NOT NULL AUTO_INCREMENT ,  
        `FirstName` VARCHAR(50) NOT NULL DEFAULT '' ,  
        `LastName` INT NOT NULL DEFAULT '0' ,  
        `Password` VARCHAR(50) NOT NULL DEFAULT '' ,  
        PRIMARY KEY (`ID`)  
    )ENGINE = InnoDB;   

    CREATE TABLE `COP4331`.`Colors`  
    (  
        `ID` INT NOT NULL AUTO_INCREMENT ,  
        `Name` VARCHAR(50) NOT NULL DEFAULT '' ,  
        `UserID` INT NOT NULL DEFAULT '0' ,  
        PRIMARY KEY (`ID`)  
    )ENGINE = InnoDB;   

Populate working data rows:  
    &emsp; **use COP4331;**  

    insert into Users (FirstName,LastName,Login,Password) VALUES ('Aashish','Yadavally','AYadavally','COP4331');  
    insert into Users (FirstName,LastName,Login,Password) VALUES ('Sam','Hill','SamH','Test');  
    insert into Users (FirstName,LastName,Login,Password) VALUES ('Aashish','Yadavally','AYadavally','5832a71366768098cceb7095efb774f2');  
    insert into Users (FirstName,LastName,Login,Password) VALUES ('Sam','Hill','SamH','0cbc6611f5540bd0809a388dc95a615b');  

    insert into Colors (Name,UserID) VALUES ('Blue',1);  
    insert into Colors (Name,UserID) VALUES ('White',1);  
    insert into Colors (Name,UserID) VALUES ('Black',1);  
    insert into Colors (Name,UserID) VALUES ('gray',1);  
    insert into Colors (Name,UserID) VALUES ('Magenta',1);  
    insert into Colors (Name,UserID) VALUES ('Yellow',1);  
    insert into Colors (Name,UserID) VALUES ('Cyan',1);  
    insert into Colors (Name,UserID) VALUES ('Salmon',1);  
    insert into Colors (Name,UserID) VALUES ('Chartreuse',1);  
    insert into Colors (Name,UserID) VALUES ('Lime',1);  
    insert into Colors (Name,UserID) VALUES ('Light Blue',1);  
    insert into Colors (Name,UserID) VALUES ('Light Gray',1);  
    insert into Colors (Name,UserID) VALUES ('Light Red',1);  
    insert into Colors (Name,UserID) VALUES ('Light Green',1);  
    insert into Colors (Name,UserID) VALUES ('Chiffon',1);  
    insert into Colors (Name,UserID) VALUES ('Fuscia',1);  
    insert into Colors (Name,UserID) VALUES ('Brown',1);  
    insert into Colors (Name,UserID) VALUES ('Beige',1);  

    insert into Colors (Name,UserID) VALUES ('Blue',3);  
    insert into Colors (Name,UserID) VALUES ('White',3);  
    insert into Colors (Name,UserID) VALUES ('Black',3);  
    insert into Colors (Name,UserID) VALUES ('gray',3);  
    insert into Colors (Name,UserID) VALUES ('Magenta',3);  
    insert into Colors (Name,UserID) VALUES ('Yellow',3);  
    insert into Colors (Name,UserID) VALUES ('Cyan',3);  
    insert into Colors (Name,UserID) VALUES ('Salmon',3);  
    insert into Colors (Name,UserID) VALUES ('Chartreuse',3);  
    insert into Colors (Name,UserID) VALUES ('Lime',3);  
    insert into Colors (Name,UserID) VALUES ('Light Blue',3);  
    insert into Colors (Name,UserID) VALUES ('Light Gray',3);  
    insert into Colors (Name,UserID) VALUES ('Light Red',3);  
    insert into Colors (Name,UserID) VALUES ('Light Green',3);  
    insert into Colors (Name,UserID) VALUES ('Chiffon',3);  
    insert into Colors (Name,UserID) VALUES ('Fuscia',3);  
    insert into Colors (Name,UserID) VALUES ('Brown',3);  
    insert into Colors (Name,UserID) VALUES ('Beige',3);  

Test database:  
    &emsp; **select * from Users;**  
    &emsp; **select * from Colors;**  
    &emsp; **select * from Colors where UserID=1;**  
    &emsp; **select * from Colors where UserID=3;**  

Create a user:  
    &emsp; **use COP4331;**  
    &emsp; **create user 'TheBeast' identified by 'WeLoveCOP4331';**  
    &emsp; __grant all privileges on COP4331.* to 'TheBeast'@'%';__  

Now the database is ready to be used.  

**Note:** To exit MySQL use command: **exit;**  


### Step 4 (Add Code Files to LAMP Droplet)  
Navigate to the root: **cd /root**  
Navigate to the web root’s directory: **cd /var/www/html**  
Create the directories:  
    &emsp; **mkdir css**  
    &emsp; **mkdir images**  
    &emsp; **mkdir js**  
    &emsp; **mkdir LAMPAPI**  

**Note:** Type **ls** to view subdirectories or to view content inside directories  

Enter subdirectories and upload all respective files, for example:  
    &emsp; **cd LAMPAPI**  
    &emsp; **C:\Desktop\LAMP Stack\LAMPAPI\AddColor.php**  

**Note:** HTML files will be uploaded to **/var/www/html** directory  


### Step 5 (Create and Test API endpoints)  
Use AdvancedRestClient, ARC, to test API endpoints  
In the search bar, type **http://MyDomainNameORIPAddress/LAMPAPI/EndpointFileName.php**  
Select the dropdown to the left of the search bar and select **POST**  
In the **Header** tab, select the **+ADD**  
    &emsp; **Header name** : **Content-Type**  
    &emsp; **Header value** : **application/json**  

In the **BODY** tab,  
**http://MyDomainNameORIPAddress/LAMPAPI/Login.php**  
    {  
        &emsp; "login" : " ",  
        &emsp; "password" : " "  
    }  

**http://MyDomainNameORIPAddress/LAMPAPI/AddColor.php**  
    {  
        &emsp; "userId" : " ",  
        &emsp; "color" : " "  
    }  

**http://MyDomainNameORIPAddress/LAMPAPI/SearchColors.php**  
    {  
        &emsp; "userId" : " ",  
        &emsp; "search" : " "  
    }  


## COLORS Application
The COLORS web application should now be accessible and working through your purchased domain name. The homepage will be a login page and once the username and password are entered, the website will take you the page that allows you to search for and add colors. 