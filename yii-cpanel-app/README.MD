**CPANEL**
========

**[Introduction](#Introduction)**

**[Authentication](#Authentication)**

**[Manage Cron Jobs](#Manage-Cron-Jobs)**

**[Manage Background Process](#Manage-Background-Process)**



**Introduction**

- Cpanel is used to manage Cron Jobs and Background processes of a project.

- The software utility cron is a time-based job scheduler in Unix-like computer operating systems. People who set up and maintain software environments use cron to schedule jobs (commands or shell scripts) to run periodically at fixed times, dates, or intervals.
- A background process is a computer process that runs behind the scenes (i.e., in the background) and without user intervention.Typical tasks for these processes include logging, system monitoring, scheduling, and user notification



**Authentication**

First and foremost to Manage Cpanel in Local, Follow the steps:

1. Access http://cpanel.yii/auth/account/login

2. Enter user name as "admin"

3. Enter password as "admin" and sign in

   ![](img/cpanel-login.png)

**Manage Cron Jobs**

1. Access http://cpanel.yii/cron.

   ![](img/process-index.png)

2. Click on "create" button(green) on the upper right most corner.

    ![](img/cronjob-create.png)

3. Enter the name of the Cron Job.

4. The Cron Jobs vary in Run time. Specify the run time as per requirement.

        a)every minute and last run : *****
        b)every five minute :*/5****
        c)hourly : 0****
        d)daily : 10***

5. The next field required to be filled is Run command. This is the instance from the current version of the project followed by the cron job respectively.



**Manage Background Process**

1. Access http://cpanel.yii/process.

   ![](img/process-index.png)

2. Click on "create" button(green) on the upper right most corner.

   ![](img/process-create.png)

3. Enter the Name and Run Command where name specified should be the name of the background process and Run command should be the project current instance of version followed by the process.

4. Then create the process.

5. The created process appears in the http://cpanel.yii/process.

6. These processes are provided with options to run,edit and delete.

7. The process works in the project only if we run the background process.

   ![](img/process-run.png)

8. We can similarly stop the process run on clicking on the stop.

9. We can edit and delete the process upon requirement using edit and delete options provided. 
