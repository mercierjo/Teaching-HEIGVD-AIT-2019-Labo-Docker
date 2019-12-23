# Lab 04 - Docker

Authors: Mercier Jordan, Vogel Maximilian

Date: 18.12.2019

Forked from : https://github.com/SoftEng-HEIGVD/Teaching-HEIGVD-AIT-2019-Labo-Docker

# Table of content

0. [Introduction](#introduction)
1. [Identify issues and install the tools](#task-0)
2. [Add a process supervisor to run several processes](#task-1)
3. [Add a tool to manage membership in the web server cluster](#task-2)
4. [React to membership changes](#task-3)
5. [Use a template engine to easily generate configuration files](#task-4)
6. [Generate a new load balancer configuration when membership changes](#task-5)
7. [Make the load balancer automatically reload the new configuration](#task-6)
8. [Difficulties](#difficulties)
9. [Conclusion](#conclusion)

# Introduction

This lab builds on a previous lab on load balancing.

# <a name="task-0"></a>Task 0 - Identify issues and install the tools

## Identify issues

Last lab's infrastructure (simple distributed system with a load balancer and two web applications):

![Architecture](../assets/img/Lab4_schema.png)


[M1] Do you think we can use the current solution for a production environment? What are the main problems when deploying it in a production environment?

[M2] Describe what you need to do to add new `webapp` container to the infrastructure. Give the exact steps of what you have to do without modifiying the way the things are done. Hint: You probably have to modify some configuration and script files in a Docker image.

[M3] Based on your previous answers, you have detected some issues in the current solution. Now propose a better approach at a high level.

[M4] You probably noticed that the list of web application nodes is hardcoded in the load balancer configuration. How can we manage the web app nodes in a more dynamic fashion?

[M5] Do you think our current solution is able to run additional management processes beside the main web server / load balancer process in a container? If no, what is missing / required to reach the goal? If yes, how to proceed to run for example a log forwarding process?

[M6] What happens if we add more web server nodes? Do you think it is really dynamic? It's far away from being a dynamic configuration. Can you propose a solution to solve this?

## Install the tools : deliverables

1. Take a screenshot of the stats page of HAProxy at <http://192.168.42.42:1936>. You should see your backend nodes.

![Dashboard](./images/step0_dashboard.png)

2. Repository URL : https://github.com/mercierjo/Teaching-HEIGVD-AIT-2019-Labo-Docker

# <a name="task-1"></a>Task 1: Add a process supervisor to run several processes
## Delivrables
1. Take a screenshot of the stats page of HAProxy at http://192.168.42.42:1936. You should see your backend nodes. It should be really similar to the screenshot of the previous task.

![Dashboard Step 1](./images/step1_1.png)

2. Describe your difficulties for this task and your understanding of what is happening during this task. Explain in your own words why are we installing a process supervisor. Do not hesitate to do more research and to find more articles on that topic to illustrate the problem.


# <a name="task-2"></a>Task 2: Add a tool to manage membership in the web server cluster
## Delivrables
1. Provide the docker log output for each of the containers: `ha`,
   `s1` and `s2`. You need to create a folder `logs` in your
   repository to store the files separately from the lab
   report. For each lab task create a folder and name it using the
   task number. No need to create a folder when there are no logs.

   Example:

   ```
   |-- root folder
     |-- logs
       |-- task 1
       |-- task 3
       |-- ...
   ```

2. Give the answer to the question about the existing problem with the
   current solution.

3. Give an explanation on how `Serf` is working. Read the official
   website to get more details about the `GOSSIP` protocol used in
   `Serf`. Try to find other solutions that can be used to solve
   similar situations where we need some auto-discovery mechanism.

# <a name="task-3"></a>Task 3: React to membership changes
## Delivrables
1. Provide the docker log output for each of the containers:  `ha`, `s1` and `s2`.
   Put your logs in the `logs` directory you created in the previous task.

2. Provide the logs from the `ha` container gathered directly from the `/var/log/serf.log`
   file present in the container. Put the logs in the `logs` directory in your repo.

# <a name="task-4"></a>Task 4: Use a template engine to easily generate configuration files

# <a name="task-5"></a>Task 5: Generate a new load balancer configuration when membership changes

# <a name="task-6"></a>Task 6: Make the load balancer automatically reload the new configuration
