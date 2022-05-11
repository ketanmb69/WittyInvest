# WittyInvest



A virtual stock market application. Made using python and its framework Django with Ajax for dynamic webpages and live price changing of stocks provided.

To run the application,
The system should have Python-3.7 installed.

This is a private repository,

### The private repository link: https://github.com/ketanmb69/WittyInvest


### unzip the repository and perform below steps to get this application working.

### create virtual environment by 
    ```bash
    python -m venv env ```
    
### Activate the virtual envirmnoment
    ```bashsource env/bin/activate ```
### go to repositoy
    ```bash cd WittyInvest ```
### run below commands,
    ```bash 
    pip install -r requirements.txt
    python manage.py makemigrations
    python manage.py migrate
    python manage.py runserver 8080 ```

### Access the url and check all the functionalities.

## To deploy the application to the production environment like elastic beanstalk.

- 1. Through command line,

   - go to AWS console and create an environment using cloud9 IDE, keep all the details default.

   - follow all the above steps to run the application.
   - then deactivate the virtual environment by
        ```bash deactivate ```
    
   - install elastic beanstalk cli
        ```bash python -m pip install --upgrade pip ```
    
   - check the elastic beanstalk version
        ```bash eb --version ```

   - create an application
        ```bash eb init -r us-east-1 -p python-3.7 <applicationName>
        
        eb init ```

        check Y to use codecommit repository
        provide Name of the repository and branch as main

        click Y for SSH setup
        keep passphrase blank

   - create an elastic beanstalk environment
        ```bash eb create <envName> ```

    It will take 3-4 minuts to create an environment.
    
   - Go to codecommit service, and under clone URL,
     copy HTTP(GRC) URL

     go to project directory in terminal and,
        ```bash git clone <codecommitCopiedURL> ```
        
   - remote origin will be assigned to codecommit.
        ```bash 
        git add .
        git commit -m "Initial Commit"
        git push ```

     it will push all the changes to CodeCommit

   - Now deploy the application,
       ```bash eb deploy ```

   - After successful deployment,
        ```bash eb open ```

    ### The website will be accessible on a production environment that is on elastic beanstalk.

- 2. Through CodePipeline

   - Go to AWS Elastic Beanstalk console,

     create environment,
     provide the application name and environment name
     provide the platform as python and version as python-3.7 and create the environment

     after successful creation of the environment,
     go to AWS CodePipeline service,
     provide the name of the pipeline and keep all the below details same,
     In the next step keep the source code provider as CodeCommit.

     then skip the BUILD stage,
     in the next stage,
     chose Elastic Beanstalk as a Deploy provider and provide the application name and environment that we created just before.

     The pipeline will be created and after successful stages, access the website from elastic beanstalk console.
