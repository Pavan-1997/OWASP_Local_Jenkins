# OWASP Dependency Check performing in Local Ubuntu Server and also implementing in Jenkins File

- OWASP Dependency Check is a software composition analysis (SCA) tool that identifies project dependencies with known vulnerabilities. It helps developers and security professionals identify and mitigate potential risks associated with using vulnerable libraries and components.

- Use SonarQube for Source Code before building 

- Use OWASP after building 

- OWASP generates a report after vulnerability check 

- OWASP sopports for npm, zip , jar, war, py files

- OWASP can be implemented either in a Jenkins File or running in a Server

![image](https://github.com/Pavan-1997/OWASP_Local_Jenkins/assets/32020205/f9ee3a71-8608-4dbd-b6ac-d7fb5ae23d10)



# OWASP on Ubuntu Server:

1. Create a EC2 Ubuntu Machine


2. Create  a directory 

    a. mkdir pavan

    b. cd pavan

		
4. Clone the code to that directory
```	 
git clone https://github.com/Pavan-1997/Java_Maven_Tomcat.git
```
	
4. Download the latest OWASP
```	
wget https://github.com/jeremylong/DependencyCheck/releases/download/v8.2.1/dependency-check-8.2.1-release.zip
```
	
5. Unzip the file , first download the unzip 
```
sudo apt-get install unzip
```

6. Now unzip the OWASP
```
unzip dependency-check-8.2.1-release.zip
```

7. Install Maven to Build

sudo apt-get update

sudo apt-get install maven


8. Now Build the Source Code 

mvn clean package


9. To run the OWASP which generates report in path suffixed with --out

cd /root/pavan/dependency-check

./bin/dependency-check.sh --out /root/pavan/Petclinic . --scan /root/pavan/Petclinic/target


10. To verify the report generated

cd /root/pavan/Petclinic

You should see dependency-check-report.html




# OWASP using Jenkins File:

1. Go to Manage Jenkins


2. Install the OWASP Dependency-Check


3. Go to Global Tool Configuration

Name - owasp

Check Install automatically

Select dependency-check

Select version dependency-check 6.5.1


4. Edit the JenkinsFile and add the below Stage 

![image](https://github.com/Pavan-1997/OWASP_Local_Jenkins/assets/32020205/7196e9a9-9577-4890-9ec9-603856eb5e61)

5. Now run the Job and look for vulnerabilities in the Dependency-Check Results

![image](https://github.com/Pavan-1997/OWASP_Local_Jenkins/assets/32020205/33ca9d80-cd0e-4940-88b3-4c0661b26bea)

