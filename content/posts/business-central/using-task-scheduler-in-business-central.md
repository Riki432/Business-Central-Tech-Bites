---
title: "Using Task Scheduler in Business Central"
date: 2022-09-23T20:31:46+05:30
draft: false
tags: ['Business Central']
categories: ['Technical']
summary: 'How to use Task Scheduler in Business Central'
featured_image: 'https://i.ibb.co/8Pb6LFW/image.png'
---

# Introduction
In Business Central, we can use Task Schedulers to use background processing to ensure that Users are not bothered with long operations. 

Task Scheduler provides us an easy to use and monitor way to offload tasks from the main thread. It creates separate sessions for processing and it allows creating multiple sessions which can be used to run tasks in parallel. 

It also allows us to define the company in which the processing will happening which is useful when we have to perform operations across all available companies, for instance initialization of certain fields or creation of certain records on application installation. 


## Pre-requisites
- Business Central OnCloud or OnPremise

## References
- [Task Scheduler Data Type](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/taskscheduler/taskscheduler-data-type)
- [Task Scheduler](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-task-scheduler)

## Configuration
The following procedures are available for the Task Scheduler data type:
1. *CanCreateTask()* - Checks whether it is possible to create a new task in this session.

2. *CreateTask()* - Creates a new task with the specified codeunit, we also specify which Codeunit to run if the main codeunit fails, whether the starts of this task would be Ready when it is created, the company this task will be running under and the time after which this task is to be run.

3. *TaskExists()* - Checks whether the specified Task exists or not.

4. *SetTaskReady()* - Sets the specified task status to Ready, a Task can only begin processing if it is in Ready state.

5. *CancelTask()* - Sets the specified Task's status to Cancel. A Task can only be set to cancel if it is in pending state. A task that is in progress cannot be cancelled.

![alt](https://i.ibb.co/gWCm5hG/image.png)

In case the main Codeunit hits an exception then there are two cases:
- The exception is retriable :- Business Central will re-try the main codeunit a specific number of times with a specific time interval, if it is unable to complete then the task is failed.
- The exception is not retriable :- The task fails and the session is deleted.

Further if there is a failure codeunit defined then Business Central will run the Failure codeunit instead of failing the task and similarly if the Failure Codeunit hits an exception that is it unable to handle then there are same two cases:
- The exception is retriable :- Business Central will re-try the main codeunit a specific number of times with a specific time interval, if it is unable to complete then the task is failed.
- The exception is not retriable :- The task fails and the session is deleted.

I have created an action which creates a simple task for all the companies available to the User. After that action is called, we can see that there are four separate sessions created with the same codeunit for different companies.
The below is the screenshot of the page - Scheduled Tasks

![alt](https://i.ibb.co/8Pb6LFW/image.png)

One **important** thing to note before using Scheduled Tasks is that you need to be a **Licensed User** to use scheduled tasks, for example if there is a API which is trying to create a Scheduled Task, that is going to fail, it's a design choice by Microsoft and so far I haven't been able to come up with a work around for it.

## Conclusion
Thus we saw how to create and use Scheduled Tasks in Business Central for background processing.

Happy Coding!
