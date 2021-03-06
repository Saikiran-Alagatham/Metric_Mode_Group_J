#Project Structure  
The main folder is called Project, which contains five folders:    
* CommonCollections.    
* CommonLang.  
* CommonMath.  
* Common Configuration.  
* CommonDigester.  
* ScriptToExtractDataFromPitestFile

ScriptToExtractDataFromPitestFile contains the script to extract the data.   
Except 'ScripttoExtractDataFromPitestFile', each of the five folders is named after the respective project. Each of these folders conatin the following:   
* the pom files for the five different versions of each project.  
* Folders named 'Metric 1,2,4', Metric3, Metric5, Metric6 containing the results for the respective metric.  
* Folder Correlation, which contains the correlation data and the correlation coefficients in seperate .csv files as well as the .csv files extracted from the Pit and Jacoco.
    
    
 
 

# Metric_Mode

_This Project is aimed at analyzing various open source systems from “The Apache Software Foundation. The systems first undergo a data collection process under which they are subjected to various tools which collect data for different metrics. Later this collected data undergoes Correlation analysis inorder to find some rationales based on the data. By Performing this assessment, we get an idea of the overall quality of the SUT (System under test) as well as helps us to get an idea of the impacts of decision made during the software development life cycle._ 

## Metrics
The chosen systems undergo a rigorous analysis under different tools to measure various metrics including:  
     
### Metric 1 & 2 - Test Coverage Metric  
Test coverage can be done in two ways; namely code statement coverage and code branch coverage.  
  * Statement coverage shows exactly how much percentage of statements of the given code are executed.  
  * Branch coverage verifies that all branches of the code are executed, meaning that all edges in the control flow graph are    executed.
      
### Metric 3- Mutation Score
  Mutation Testing includes changing the code — a small part at a time — creating mutants and running the unit tests suite repeatedly.
  * If the tests still pass — meaning that they were not able to identify the mutant (which might represent a wrong behavior) — we can conclude that they are less strong, and vice-versa.
  * We have used _PiTest_ tool for calculating the mutation coverage for our projects.
  
### Metric 4- Cyclomatic Complexity : McCabe 
  According to its definition by McCabe (1996); cyclomatic complexity is the minimum number of paths that can, in (linear) combination, generate all possible paths through a method.
  * We are using _JaCoCo_ plugin to calculate the cyclomatic complexity.
  * Based on the coverage status of each branch JaCoCo also calculates covered and missed complexity for each method.Missed complexity again is an indication for the number of test cases missing to fully cover a module. Note that as JaCoCo does not   consider exception handling as branches try/catch blocks will also not increase complexity.

### Metric 5- Sofware Maintainance Metric :Code Churn
  Code churn is a means to figure out the changes in the code from one release to next.  
   * It monitors changes in code like refactoring ,  adding new features etc. to ensure that the code remains stable after these changes.  
   * We have used _CLOC_ to determine the number of lines of code added, modified and deleted.

### Metric 6- Software quality metric :Code Smells
  A code smell is a surface indication that usually corresponds to a deeper problem in the system.
  * Code Smells indicate that the code needs refactoring and/or cleaning to increase its quality.
  * There are various code smells like duplicated Code and Logic ,long Methods and Classes,Dead Code ,etc.
  * We use _SonarLint_ and _SonarQube_ to identify the code smells in out projects.
  

## Projects
We have Chosen the following Projects for analysis:-  
1. Commons Math &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp; SLOC ~ 186K  
   * Versions:-
      * 3.6
      * 3.4
      * 3.3
      * 3.1
      * 2.1
2. Commons Collection &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; SLOC ~ 130K  
    * Versions:-  
      * 4.3
      * 4.2
      * 4.1
      * 4.0
      * 4.3-RC2
3. Commons Lang &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SLOC ~ 80K 
    * Versions:-  
      * 3.9
      * 3.8.1
      * 3.7
      * 3.6
      * 3.5
4. Commons Digestor &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SLOC ~ 27K 
    * Versions:-  
      * 3.2
      * 3.1
      * 3.0
      * 2.1
      * 1.8.1
4. Commons Configuration &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SLOC ~ 600K
    * Versions:-  
      * 2.4
      * 2.3
      * 2.2
      * 2.1
      * 2.0

## Tools/Plugins used for Metric Measurement

1. Jacoco Maven Plugin:-  
   * This Plugin has been used to collect data for Metric 1,2 and 4.
   * Each __pom.xml__ file of each version of each Project contains this plugin in __Build.Plugins.Plugin Tag__.
   * Inorder to generate the reports we follow below steps:-  
      1. Insert the plugin in pom.xml in the root directory of the project
      2. Run Maven Clean Goal.
      3. Run the Maven Test Goal.
   * We get the reports in jacoco-ut folder which is currently present in the above folder structure in each project/version sub-folders
2. PiTest Plugin
             
    We get the reports in a Pit-test reports folder after successfully running pit-test plugin.  
    The output is in the form of index.html format for desired result 
   We had to build script inorder to extract data for further correlation.

3. Code Churn  
  Download and install cloc-1.82.exe.  
  
  #### Command used :  
    cloc --diff “version1Code” “Version2Code” --out=report.csv  
    
  This creates a file report.csv that contains the count of files ,blank lines, commented lines and lines of code that are same, added , modified and removed in each of the languages used in the given projects .  
  We consider the sum of values of LOC for added/modified/deleted sections and get a Code Churn value.


4. SonarQube/SonarLint
  After successfully compiling a version we need to run the following command:
 “mvn sonar: sonar Dsonar.projectKey=”KeyValue”Dsonar.host.url=http://localhost:9000 Dsonar.login=admin Dsonar.password=admin” 
 on the terminal. 
  The results can then be seen online on the browser at localhost:9000 where the project was created.
  The code smell value can then be used for further correlation.

## Team Details  

  - ADITYA SURVE        || 40087470 || aditya.surve2913@gmail.com
  - PALLAVI KUMAR       || 40049791 || pallavikumar88992@gmail.com  
  - DIVYA PANDIT        || 40087471 || divyapandit13@gmail.com
  - ANKUR AGARWAL       || 40105298 || ankur.96469@gmail.com
  - HITESH AGARWAL      || 40104304 || hitesh0981@gmail.com




