# Public Cloud - TP1

## Instructions
In this tutorial, we will implement the infrastructure-as-a-service that we have seen in the course. To do this, we will deploy the PetClinic application on a virtual machine.

Here is what the architecture of the application looks like
![Architecture](https://spring-petclinic.github.io/images/petclinic-microservices-architecture.png "Architecture")

The tutorial is divided into two parts: the following `README.md` file, and an `ANSWER.md` file which contains 10 questions to answer.

The idea of the tutorial is to answer the questions in the `ANSWER.md` file and push it to your repository. The rest is explained as the tutorial progresses.

## 1: Git
### 1.0: Fork the lab repo
Follow the link on the board to fork this repository into your personal GitHub Classroom repository. If you have access to the repository, it means that the manipulation worked well.

### 1.1 : Clone the repository
Clone the newly copied repo on your computer 
> From now on, **you will only work in your local copy**.
 
### 1.2: Create an issue
> Create an issue called `1.2` with the commands you made to clone your git repo as the contents.

## 2: IaaS
First, we will deploy this architecture on a virtual machine.

### 2.0: Create an AWS virtual machine
To create an EC2 machine, go to the AWS portal.

First of all, you have to choose the region. Be careful and choose the region **Europe (Ireland) eu-west-1** in the drop-down menu at the top right.

Then click on the EC2 menu. Then click on the Launch Instance button.

It is advisable to start an Ubuntu virtual machine in order to install the application easily.

To facilitate the organisation of virtual machines, please name your machine `firstname-lastname-vm`. Do the same when creating the **security group**, you will need to name it `firstname-lastname-sg`.

### 2.1: Connect to the machine
Once the virtual machine is created, connect to the machine
```bash
ssh ubuntu@<public-ip>
```

### 2.2: Install the necessary tools
Next, install the tools needed to start the application. To run the application correctly, the tools to install are: `git`, `maven` and `openjdk-8-jdk`.
> Create an issue called `2.2` with the contents of the commands you have made

### 2.3: Clone the Spring PetClinic repo
Then clone the PetClinic repo `https://github.com/spring-projects/spring-petclinic`
> ⚠️ **WARNING**: Create an issue called `2.3` with the commands you have done

### 2.4 : Running Spring PetClinic
Run the following command to compile, then run the application
```bash
cd spring-petclinic
./mvnw package
java -jar target/*.jar
```

### 2.5: Connect to the application
Now try to connect to the application. It will normally be impossible to connect to it.
> Create an exit called `2.5` explaining why you cannot connect to the application

### 2.6 Opening the Firewall
In order to connect to the application, you need to open the port where the application is listening. The listening port is `8080`.

To open the port, it is necessary to go to the ***Security Groups***.
> Create an issue called `2.6` with the commands you have made as its content

### 2.7: Verify proper operation
Open the browser and go to the following url to see the Petclinic application: `http://<public-ip>:<port>`

### 2.8 : Install MariaDB
By default, the application starts without a database server and therefore does not persist the data you can modify. In order to be able to persist the data, it is necessary to install MariaDB and to modify the configuration file of the application in order to point on the database.

Install MariaDB as follows: `https://www.digitalocean.com/community/tutorials/how-to-install-mariadb-on-ubuntu-20-04`
> Create an issue called `2.8` with the commands you have made

### 2.9 : Installing schemas and data
In the git repo, there are instructions to create the PetClinic database. These instructions are located here: `spring-petclinic/src/main/resources/db/mysql/`

The txt file in the directory refers to Docker. For the purposes of this tutorial, we will not be installing Docker, as we have already installed MariaDB.

The files to play with on the MariaDB database are in order: `user.sql`, `schema.sql` and `data.sql`.

### 2.10 : Restarting the application
Restart the PetClinic application with the correct profile so that the application can use the MySQL server. The command should be: `java -Dspring.profiles.active=mysql -jar target/*.jar`

### 2.11: Verify proper operation
Open the browser and go to the following url to see the Petclinic application: `http://<public-ip>:<port>`
